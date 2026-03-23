# 🏭 Software Factory Architecture (V1)

## Overview
The Software Factory is a lean, AI-driven, multi-agent development environment orchestrated by **Zhen Claw**. It relies heavily on API-driven specialist agents to execute tasks based on strict, pre-defined blueprints.

## Core Principles & Protocols
- **The Clarity Protocol:** No speculation. If technical details are vague, the factory halts. Zhen Claw will ask critical questions to ensure the blueprint is flawless before a single line of code is written.
- **Blueprint First:** Code is never written without a finalized Product Requirements Document (PRD) and UI/UX design. 
- **Centralized Knowledge:** All code, docs, and assets are stored in a centralized GitHub repository and synced via Google Drive/Calendar.

## 1. The Orchestrator (Zhen Claw)
- **Role:** Project Manager, Context Keeper, and Task Router.
- **Engine:** Kimi k2.5 running on a single Ollama Cloud Instance.
- **Responsibilities:** 
  - Enforce the Clarity Protocol.
  - Break down high-level user requests.
  - Route tasks to the correct specialist APIs.
  - Manage the file system, Git repositories, and Google Workspace integrations.

## 2. The Specialist APIs
*This layer requires zero local hosting—it’s 100% API-driven.*
- **The Technical Writer:** Claude Opus 4.5 (via Anthropic API). Drafts PRDs, API specs, and system logic.
- **The UI/UX Designer:** Figma AI (via Figma API/Web) or fallback vision model. Generates wireframes, design tokens, and UI mockups.
- **The Coder:** minimax-m2.5 (via OpenRouter API). Receives the PRD and design specs, and writes code that exactly matches the blueprint.

## 3. The Workspace & Storage Layer
- **Local File System:** `~/.openclaw/workspace` (where all code, docs, and memory live temporarily during execution).
- **Version Control (GitHub):** The Coder pushes code to a dedicated shared repository. Zhen Claw tracks progress and manages pull requests.
- **Documentation & Management (Notion):** Notion is the central brain for technical blueprints. It hosts the PRDs, architecture specs, and a Kanban board to track the progress of every specialist agent (To Do, In Progress, Review, Done).

## 4. The Bulletproof Workflow
1. **Input & Specs (The Blueprint & The Interrogation):** 
   - User provides a feature idea. 
   - Zhen Claw loops in the Technical Writer (Claude Opus 4.5) to draft the initial PRD.
   - *Clarity Check:* Zhen Claw and Claude review the specs for technical gaps or vague requirements. Zhen Claw presents critical questions back to the user. Proceed only when all assumptions are cleared up.
2. **Design (The Look):** 
   - PRD is locked in. 
   - Hand requirements to the UI/UX Designer (Figma AI/Fallback) to generate wireframes and UI mockups.
3. **Execution (The Build):** 
   - Docs and designs are finalized. 
   - Wake up the Coder (minimax-m2.5 via OpenRouter). The Coder receives the PRD and design files, writing code that exactly matches the blueprint.
4. **Testing & QA (The Crucible - *NEW*):**
   - The Coder writes and runs unit/integration tests. 
   - If tests fail, the Coder iterates until passing.
5. **Review & Ship:** 
   - Zhen Claw reviews the Coder's output against the original Claude docs and Figma designs.
   - Code is pushed to GitHub; docs are synced.
   - Final approval from the user.
