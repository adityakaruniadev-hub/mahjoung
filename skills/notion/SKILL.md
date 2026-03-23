---
name: notion-integration
description: >
 Use this skill whenever the user wants to interact with Notion via the API — including
 reading or writing pages, querying databases (data sources), managing blocks, searching
 workspaces, or building any Notion-powered automation or integration. Trigger this skill
 when the user mentions Notion pages, Notion databases, Notion API, Notion integration tokens,
 or wants to sync, automate, read, create, or update anything in Notion. Also trigger when
 the user wants to build a tool, script, or agent that reads from or writes to Notion.
 Always use this skill before writing any Notion API code — it contains critical details
 about the latest API version (2025-09-03), authentication patterns, data source terminology,
 pagination, and common gotchas that prevent integration failures.
---

# Notion API Integration Skill

## Overview

The Notion API (base URL: `https://api.notion.com/v1`) lets agents and integrations programmatically read and write pages, databases (now called **data sources** in API v2025-09-03), blocks, users, and comments.

**Always include this header in every request:**
```
Notion-Version: 2025-09-03
```

---

## 1. Authentication

### Internal Integration (most common for agents)
- Create an integration at https://notion.so/my-integrations
- Copy the **Internal Integration Token** (starts with `secret_...`)
- Share target pages/databases with the integration: `••• menu → Connect to → [your integration]`

```
Authorization: Bearer secret_XXXXXXXXXXXXXXXXXXXXXXXXXXXX
Notion-Version: 2025-09-03
Content-Type: application/json
```

### Public Integration (OAuth 2.0)
- Uses Client ID + Client Secret from the integration dashboard
- Redirect users through OAuth flow to get an `access_token`
- Token endpoint: `POST https://api.notion.com/v1/oauth/token`
- See `references/oauth.md` for the full OAuth flow.

---

## 2. Key Terminology (API v2025-09-03)

| Old term | New term (v2025-09-03) | Notes |
|----------------|------------------------|---------------------------------------------|
| Database | Data Source | Databases are now called data sources in API |
| Database ID | Data Source ID | Use `data_source_id` in new endpoints |
| `/v1/databases/...` | `/v1/data_sources/...` | Migrate to new endpoints |

> ⚠️ **Breaking change**: As of API version 2025-09-03, databases are referred to as **data sources**. Existing integrations using `/v1/databases/` still work but should be migrated. Always use the new `/v1/data_sources/` endpoints for new code.

---

## 3. Core Endpoints Reference

### 🔍 Search
```http
POST /v1/search
Body: { "query": "page title", "filter": { "value": "page", "property": "object" } }
```
- Returns pages and data sources the integration has access to
- Use an empty `query: ""` to list all accessible content
- Results now include `data_source` objects (in addition to `page` and `database`)

### 📄 Pages
| Action | Method | Endpoint |
|-----------------|--------|---------------------------------|
| Get page | GET | `/v1/pages/{page_id}` |
| Create page | POST | `/v1/pages` |
| Update page | PATCH | `/v1/pages/{page_id}` |
| Archive page | PATCH | `/v1/pages/{page_id}` (set `archived: true`) |

**Create a page in a data source:**
```json
POST /v1/pages
{
 "parent": { "database_id": "DATA_SOURCE_ID" },
 "properties": {
 "Name": { "title": [{ "text": { "content": "New Entry" } }] },
 "Status": { "select": { "name": "Todo" } }
 }
}
```

**Create a standalone page:**
```json
POST /v1/pages
{
 "parent": { "page_id": "PARENT_PAGE_ID" },
 "properties": {
 "title": [{ "text": { "content": "My Page" } }]
 },
 "children": [
 { "object": "block", "type": "paragraph",
 "paragraph": { "rich_text": [{ "text": { "content": "Hello!" } }] }
 }
 ]
}
```

### 🗄️ Data Sources (Databases)
| Action | Method | Endpoint |
|--------------------|--------|---------------------------------------|
| Get data source | GET | `/v1/data_sources/{data_source_id}` |
| Create data source | POST | `/v1/data_sources` |
| Update data source | PATCH | `/v1/data_sources/{data_source_id}` |
| Query data source | POST | `/v1/data_sources/{data_source_id}/query` |

**Query with filter and sort:**
```json
POST /v1/data_sources/{data_source_id}/query
{
 "filter": {
 "property": "Status",
 "select": { "equals": "Active" }
 },
 "sorts": [{ "property": "Date", "direction": "descending" }],
 "page_size": 50
}
```

### 🧱 Blocks
| Action | Method | Endpoint |
|----------------------|--------|--------------------------------------|
| Get block | GET | `/v1/blocks/{block_id}` |
| Get block children | GET | `/v1/blocks/{block_id}/children` |
| Append block children| PATCH | `/v1/blocks/{block_id}/children` |
| Update block | PATCH | `/v1/blocks/{block_id}` |
| Delete block | DELETE | `/v1/blocks/{block_id}` |

**Append content to a page:**
```json
PATCH /v1/blocks/{page_id}/children
{
 "children": [
 {
 "object": "block",
 "type": "heading_2",
 "heading_2": { "rich_text": [{ "text": { "content": "Section Title" } }] }
 },
 {
 "object": "block",
 "type": "paragraph",
 "paragraph": { "rich_text": [{ "text": { "content": "Body text here." } }] }
 }
 ]
}
```

### 👥 Users
```http
GET /v1/users # List all workspace users
GET /v1/users/{user_id} # Get specific user
GET /v1/users/me # Get the bot user (integration identity)
```

### 💬 Comments
```http
GET /v1/comments?block_id={id} # List comments on a block/page
POST /v1/comments # Create a comment
```

---

## 4. Pagination

All list endpoints use **cursor-based pagination**. Default page size = 10.

```json
GET /v1/blocks/{id}/children?page_size=100&start_cursor=CURSOR_TOKEN
```

**Response pattern:**
```json
{
 "results": [...],
 "has_more": true,
 "next_cursor": "abc123"
}
```

**Always paginate to get all results:**
```python
def get_all(url, headers, params=None):
 results = []
 cursor = None
 while True:
 p = {**(params or {}), "page_size": 100}
 if cursor:
 p["start_cursor"] = cursor
 r = requests.get(url, headers=headers, params=p).json()
 results.extend(r["results"])
 if not r.get("has_more"):
 break
 cursor = r["next_cursor"]
 return results
```

---

## 5. Block Types Reference

Common block types for page content:

| Type | Key | Notes |
|-----------------|----------------|----------------------------------|
| Paragraph | `paragraph` | Most common text block |
| Heading 1–3 | `heading_1` etc| Section headings |
| Bulleted list | `bulleted_list_item` | List item |
| Numbered list | `numbered_list_item` | Ordered list item |
| To-do | `to_do` | Checkbox; add `checked: bool` |
| Toggle | `toggle` | Collapsible block with children |
| Code | `code` | Code block; specify `language` |
| Callout | `callout` | Callout box with icon |
| Divider | `divider` | Horizontal rule; no content |
| Image | `image` | External URL or file object |
| Table | `table` | Use `table_row` children |
| Child page | `child_page` | Inline sub-page reference |

For deeply nested content, recursively fetch children when `has_children: true`.

---

## 6. Property Types (Database/Data Source)

When creating pages inside data sources, match the property type:

| Property Type | Payload Example |
|---------------|-----------------|
| `title` | `[{ "text": { "content": "Value" } }]` |
| `rich_text` | `[{ "text": { "content": "Value" } }]` |
| `number` | `{ "number": 42 }` |
| `select` | `{ "select": { "name": "Option" } }` |
| `multi_select`| `{ "multi_select": [{ "name": "Tag1" }] }` |
| `date` | `{ "date": { "start": "2025-03-18" } }` |
| `checkbox` | `{ "checkbox": true }` |
| `url` | `{ "url": "https://example.com" }` |
| `email` | `{ "email": "user@example.com" }` |
| `phone_number`| `{ "phone_number": "+1234567890" }` |
| `relation` | `{ "relation": [{ "id": "PAGE_ID" }] }` |
| `people` | `{ "people": [{ "id": "USER_ID" }] }` |
| `files` | `{ "files": [{ "name": "file", "external": { "url": "..." } }] }` |

---

## 7. Finding IDs

**Page/Database ID from URL:**
```
https://notion.so/My-Page-Title-16d8004e5f6a42a69811
 └─── ID is the last 32 chars (with hyphens added)
→ 16d8004e-5f6a-42a6-9811-51c22ddada12
```

**Via search:**
```http
POST /v1/search
{ "query": "page name" }
```
Returns full objects including their IDs.

---

## 8. Rate Limits & Best Practices

- **Rate limit**: ~3 requests/second per integration token
- On `429 Too Many Requests`, respect `Retry-After` header
- Use `page_size: 100` (max) to minimize requests
- For large pages, read blocks asynchronously / with a queue
- Never store API keys in plaintext in committed code — use env vars

```python
import os
NOTION_TOKEN = os.environ["NOTION_API_KEY"]
headers = {
 "Authorization": f"Bearer {NOTION_TOKEN}",
 "Notion-Version": "2025-09-03",
 "Content-Type": "application/json"
}
```

---

## 9. Error Handling

| Status | Meaning | Action |
|--------|----------------------------------|-------------------------------------|
| 400 | Bad request / invalid payload | Check property types and structure |
| 401 | Unauthorized | Check integration token |
| 403 | Forbidden / not shared | Share the page with the integration |
| 404 | Not found | Verify ID; check page is shared |
| 409 | Conflict | Retry with backoff |
| 429 | Rate limited | Wait `Retry-After` seconds |
| 500 | Notion server error | Retry with exponential backoff |

**Common mistake**: 403 errors almost always mean the integration wasn't added to the page via `Connect to`. This is required even if you have the token.

---

## 10. Webhooks (v2025-09-03)

Notion can send webhook events when pages or data sources change.

- Register via the integration dashboard
- Events include: `page.created`, `page.updated`, `database.updated`, `data_source.*`
- New `data_source_id` field now included in webhook payloads
- Webhooks do **not** support user changes or workspace settings

See `references/webhooks.md` for full event schemas.

---

## 11. SDK Usage

**JavaScript/TypeScript (recommended):**
```bash
npm install @notionhq/client # Use v5.x for API 2025-09-03
```
```javascript
const { Client } = require("@notionhq/client");
const notion = new Client({ auth: process.env.NOTION_API_KEY });

// Query a data source
const response = await notion.databases.query({
 database_id: "DATA_SOURCE_ID",
 filter: { property: "Status", select: { equals": "Active" } }
});
```

**Python:**
```bash
pip install notion-client
```
```python
from notion_client import Client
notion = Client(auth=os.environ["NOTION_API_KEY"])
results = notion.databases.query(database_id="DATA_SOURCE_ID")
```

---

## Reference Files

- `references/oauth.md` — Full OAuth 2.0 flow for public integrations
- `references/webhooks.md` — Webhook event schemas and setup
- `references/block-types.md` — Complete block type reference with all fields
- `references/filter-syntax.md` — Full filter/sort syntax for data source queries