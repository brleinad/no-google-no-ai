# Tasks: [FEATURE NAME]

**Input**: Design documents from `/specs/[###-feature-name]/`
**Prerequisites**: plan.md (required), research.md, data-model.md, contracts/

## Execution Flow (main)
```
1. Load plan.md from feature directory
   → If not found: ERROR "No implementation plan found"
   → Extract: tech stack, libraries, structure
2. Load optional design documents:
   → data-model.md: Extract entities → model tasks
   → contracts/: Each file → contract test task
   → research.md: Extract decisions → setup tasks
3. Generate tasks by category:
   → Setup: project init, dependencies, linting
   → Tests: contract tests, integration tests
   → Core: models, services, CLI commands
   → Integration: DB, middleware, logging
   → Polish: unit tests, performance, docs
4. Apply task rules:
   → Different files = mark [P] for parallel
   → Same file = sequential (no [P])
   → Tests before implementation (TDD)
5. Number tasks sequentially (T001, T002...)
6. Generate dependency graph
7. Create parallel execution examples
8. Validate task completeness:
   → All contracts have tests?
   → All entities have models?
   → All endpoints implemented?
9. Return: SUCCESS (tasks ready for execution)
```

## Format: `[ID] [P?] Description`
- **[P]**: Can run in parallel (different files, no dependencies)
- Include exact file paths in descriptions

## Path Conventions
- **Static website**: Root level HTML, `css/`, `js/`, `images/`, `pages/` directories
- **Testing**: `tests/manual/`, `tests/validation/`
- All paths relative to repository root for CDN compatibility

## Phase 3.1: Setup
- [ ] T001 Create static website directory structure (css/, js/, images/, pages/)
- [ ] T002 [P] Create base index.html with semantic structure
- [ ] T003 [P] Initialize CSS framework/reset in css/main.css

## Phase 3.2: Core Pages ⚠️ VALIDATE BEFORE STYLING
**CRITICAL: HTML structure and content MUST be complete and valid before styling**
- [ ] T004 [P] Create page content in pages/about.html
- [ ] T005 [P] Create page content in pages/contact.html
- [ ] T006 [P] Validate HTML with W3C validator
- [ ] T007 [P] Test navigation between pages

## Phase 3.3: Styling & Interactivity
- [ ] T008 [P] Implement responsive CSS in css/main.css
- [ ] T009 [P] Add component styles in css/components.css
- [ ] T010 [P] Create JavaScript interactions in js/main.js
- [ ] T011 [P] Optimize and compress images in images/
- [ ] T012 [P] Add favicon and meta tags

## Phase 3.4: Optimization
- [ ] T013 [P] Minify CSS and JavaScript files
- [ ] T014 [P] Optimize image sizes and formats
- [ ] T015 Test load times on 3G connection
- [ ] T016 Verify CDN deployment readiness

## Phase 3.5: Validation & Testing
- [ ] T017 [P] Manual testing in Chrome, Firefox, Safari
- [ ] T018 [P] Mobile responsiveness testing
- [ ] T019 [P] Test without JavaScript enabled
- [ ] T020 [P] Validate all HTML pages with W3C
- [ ] T021 [P] Create manual testing checklist in tests/manual/
- [ ] T022 Performance audit (<2s load time)
- [ ] T023 Final CDN deployment test

## Dependencies
- HTML structure (T004-T007) before styling (T008-T012)
- Content creation before optimization (T013-T016)
- Implementation before validation (T017-T023)

## Parallel Example
```
# Launch T004-T007 together:
Task: "Create page content in pages/about.html"
Task: "Create page content in pages/contact.html"
Task: "Validate HTML with W3C validator"
Task: "Test navigation between pages"
```

## Notes
- [P] tasks = different files, no dependencies
- Validate HTML before styling
- Commit after each task
- Test on multiple browsers and devices
- Optimize for CDN deployment

## Task Generation Rules
*Applied during main() execution*

1. **From Page Structure**:
   - Each page → HTML creation task [P]
   - Navigation → linking tasks

2. **From Design Requirements**:
   - Styling → CSS implementation tasks [P]
   - Interactivity → JavaScript tasks [P]

3. **From User Stories**:
   - Each story → manual testing scenario [P]
   - Performance requirements → optimization tasks

4. **Ordering**:
   - Setup → HTML → CSS → JavaScript → Optimization → Validation
   - Dependencies block parallel execution

## Validation Checklist
*GATE: Checked by main() before returning*

- [ ] All pages have HTML creation tasks
- [ ] HTML validation comes before styling
- [ ] CSS and JavaScript tasks are parallelizable
- [ ] Performance testing includes CDN readiness
- [ ] Manual testing covers all browsers
- [ ] Each task specifies exact file path
- [ ] No task modifies same file as another [P] task