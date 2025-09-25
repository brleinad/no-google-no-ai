
# Implementation Plan: Google Query Wrapper

**Branch**: `001-build-a-simple` | **Date**: 2025-09-25 | **Spec**: [spec.md](./spec.md)
**Input**: Feature specification from `/Users/danielrb/sandbox/no-google-no-ai/specs/001-build-a-simple/spec.md`

## Execution Flow (/plan command scope)
```
1. Load feature spec from Input path
   → If not found: ERROR "No feature spec at {path}"
2. Fill Technical Context (scan for NEEDS CLARIFICATION)
   → Detect Project Type from context (web=frontend+backend, mobile=app+api)
   → Set Structure Decision based on project type
3. Fill the Constitution Check section based on the content of the constitution document.
4. Evaluate Constitution Check section below
   → If violations exist: Document in Complexity Tracking
   → If no justification possible: ERROR "Simplify approach first"
   → Update Progress Tracking: Initial Constitution Check
5. Execute Phase 0 → research.md
   → If NEEDS CLARIFICATION remain: ERROR "Resolve unknowns"
6. Execute Phase 1 → contracts, data-model.md, quickstart.md, agent-specific template file (e.g., `CLAUDE.md` for Claude Code, `.github/copilot-instructions.md` for GitHub Copilot, `GEMINI.md` for Gemini CLI, `QWEN.md` for Qwen Code or `AGENTS.md` for opencode).
7. Re-evaluate Constitution Check section
   → If new violations: Refactor design, return to Phase 1
   → Update Progress Tracking: Post-Design Constitution Check
8. Plan Phase 2 → Describe task generation approach (DO NOT create tasks.md)
9. STOP - Ready for /tasks command
```

**IMPORTANT**: The /plan command STOPS at step 7. Phases 2-4 are executed by other commands:
- Phase 2: /tasks command creates tasks.md
- Phase 3-4: Implementation execution (manual or via tools)

## Summary
Simple static web app that provides a search input field, automatically appends "-ai" to user queries, and redirects to Google search to avoid AI-generated summaries. Built as vanilla HTML/CSS/JavaScript for seamless CDN deployment.

## Technical Context
**Language/Version**: HTML5, ES2018+ JavaScript, CSS3
**Primary Dependencies**: None (vanilla web technologies only)
**Storage**: N/A (stateless static site)
**Testing**: Manual browser testing, W3C HTML validation
**Target Platform**: Modern web browsers (Chrome, Firefox, Safari)
**Project Type**: single (static website)
**Performance Goals**: <2 seconds load time on 3G, immediate redirect on search
**Constraints**: No build tools, no frameworks, CDN-ready, Netlify deployment
**Scale/Scope**: Single-page app with search form, minimal footprint

## Constitution Check
*GATE: Must pass before Phase 0 research. Re-check after Phase 1 design.*

**Static-First Compliance**:
- [x] No server-side processing, databases, or dynamic content generation
- [x] All content pre-built and self-contained
- [x] HTML, CSS, JavaScript, and assets servable directly from CDN

**CDN-Ready Compliance**:
- [x] All paths relative or absolute (no localhost dependencies)
- [x] Assets optimized for CDN delivery (minified CSS/JS, compressed images)
- [x] Proper caching headers via meta tags

**Minimal Dependencies Compliance**:
- [x] Vanilla HTML/CSS/JS preferred over frameworks
- [x] Libraries use CDN-hosted versions or single-file includes
- [x] No build tools unless absolutely required

**Performance-First Compliance**:
- [x] Pages load in under 2 seconds on 3G
- [x] Images optimized, CSS/JS minified
- [x] Minimal HTTP requests, no heavy libraries

**Simple Deployment Compliance**:
- [x] Single-step deployment (push to repo or drag-and-drop)
- [x] No build pipelines, environment variables, or configuration files

## Project Structure

### Documentation (this feature)
```
specs/[###-feature]/
├── plan.md              # This file (/plan command output)
├── research.md          # Phase 0 output (/plan command)
├── data-model.md        # Phase 1 output (/plan command)
├── quickstart.md        # Phase 1 output (/plan command)
├── contracts/           # Phase 1 output (/plan command)
└── tasks.md             # Phase 2 output (/tasks command - NOT created by /plan)
```

### Source Code (repository root)
```
# Static Website Structure (DEFAULT)
index.html                 # Homepage at root
css/
├── main.css              # Main stylesheet
└── components.css        # Component-specific styles
js/
├── main.js               # Main JavaScript
└── components.js         # Component logic
images/
├── favicon.ico
├── logo.png
└── assets/               # Other media files
pages/
├── index.html            # main and only page that redirects to google
tests/
├── manual/               # Manual testing checklists
└── validation/           # HTML/CSS validation
```

**Structure Decision**: Static website structure for CDN deployment

## Phase 0: Outline & Research
1. **Extract unknowns from Technical Context** above:
   - For each NEEDS CLARIFICATION → research task
   - For each dependency → best practices task
   - For each integration → patterns task

2. **Generate and dispatch research agents**:
   ```
   For each unknown in Technical Context:
     Task: "Research {unknown} for {feature context}"
   For each technology choice:
     Task: "Find best practices for {tech} in {domain}"
   ```

3. **Consolidate findings** in `research.md` using format:
   - Decision: [what was chosen]
   - Rationale: [why chosen]
   - Alternatives considered: [what else evaluated]

**Output**: research.md with all NEEDS CLARIFICATION resolved

## Phase 1: Design & Contracts
*Prerequisites: research.md complete*

1. **Extract entities from feature spec** → `data-model.md`:
   - Entity name, fields, relationships
   - Validation rules from requirements
   - State transitions if applicable

2. **Generate API contracts** from functional requirements:
   - For each user action → endpoint
   - Use standard REST/GraphQL patterns
   - Output OpenAPI/GraphQL schema to `/contracts/`

3. **Generate contract tests** from contracts:
   - One test file per endpoint
   - Assert request/response schemas
   - Tests must fail (no implementation yet)

4. **Extract test scenarios** from user stories:
   - Each story → integration test scenario
   - Quickstart test = story validation steps

5. **Update agent file incrementally** (O(1) operation):
   - Run `.specify/scripts/bash/update-agent-context.sh claude`
     **IMPORTANT**: Execute it exactly as specified above. Do not add or remove any arguments.
   - If exists: Add only NEW tech from current plan
   - Preserve manual additions between markers
   - Update recent changes (keep last 3)
   - Keep under 150 lines for token efficiency
   - Output to repository root

**Output**: data-model.md, /contracts/*, failing tests, quickstart.md, agent-specific file

## Phase 2: Task Planning Approach
*This section describes what the /tasks command will do - DO NOT execute during /plan*

**Task Generation Strategy**:
- Load `.specify/templates/tasks-template.md` as base
- Generate tasks from Phase 1 design docs (form interface contract, quickstart scenarios)
- HTML structure creation → single file task
- CSS styling implementation → parallel with HTML validation
- JavaScript enhancement → after HTML structure complete
- Testing scenarios from quickstart.md → manual verification tasks

**Ordering Strategy**:
- HTML-first: Semantic structure before styling
- Progressive enhancement: Basic functionality, then JavaScript enhancement
- Validation workflow: HTML validation, then accessibility testing
- Performance optimization: Minification and CDN preparation
- Deployment readiness: Final Netlify deployment verification

**Estimated Output**: 15-20 numbered, ordered tasks in tasks.md

**Static Website Focus**:
- Single HTML file with inlined CSS/JS
- Manual testing approach (no automated test framework)
- Progressive enhancement pattern (works without JS)
- CDN optimization tasks
- Accessibility compliance verification

**IMPORTANT**: This phase is executed by the /tasks command, NOT by /plan

## Phase 3+: Future Implementation
*These phases are beyond the scope of the /plan command*

**Phase 3**: Task execution (/tasks command creates tasks.md)  
**Phase 4**: Implementation (execute tasks.md following constitutional principles)  
**Phase 5**: Validation (run tests, execute quickstart.md, performance validation)

## Complexity Tracking
*Fill ONLY if Constitution Check has violations that must be justified*

| Violation | Why Needed | Simpler Alternative Rejected Because |
|-----------|------------|-------------------------------------|
| [e.g., 4th project] | [current need] | [why 3 projects insufficient] |
| [e.g., Repository pattern] | [specific problem] | [why direct DB access insufficient] |


## Progress Tracking
*This checklist is updated during execution flow*

**Phase Status**:
- [x] Phase 0: Research complete (/plan command)
- [x] Phase 1: Design complete (/plan command)
- [x] Phase 2: Task planning complete (/plan command - describe approach only)
- [ ] Phase 3: Tasks generated (/tasks command)
- [ ] Phase 4: Implementation complete
- [ ] Phase 5: Validation passed

**Gate Status**:
- [x] Initial Constitution Check: PASS
- [x] Post-Design Constitution Check: PASS
- [x] All NEEDS CLARIFICATION resolved
- [x] Complexity deviations documented (none required)

---
*Based on Constitution v2.1.1 - See `/memory/constitution.md`*
