# Tasks: Google Query Wrapper

**Input**: Design documents from `/Users/danielrb/sandbox/no-google-no-ai/specs/001-build-a-simple/`
**Prerequisites**: plan.md, research.md, data-model.md, contracts/, quickstart.md

## Execution Flow (main)
```
1. Load plan.md from feature directory
   → Extract: HTML5, ES2018+ JavaScript, CSS3 tech stack
   → Structure: Single HTML file with inlined CSS/JS
2. Load design documents:
   → contracts/form-interface.md: Form structure and JavaScript enhancement
   → quickstart.md: Manual testing scenarios
   → research.md: Technical decisions (progressive enhancement, inline assets)
3. Generate tasks by category:
   → Setup: Basic HTML structure, directory prep
   → Core: HTML form, CSS styling, JavaScript enhancement
   → Testing: Manual validation scenarios
   → Optimization: Performance and accessibility
   → Deployment: Netlify readiness verification
4. Apply task rules:
   → Single HTML file = sequential tasks (no parallel HTML editing)
   → Testing tasks = parallel [P] (independent verification)
   → Different aspects (HTML structure vs validation) = parallel [P]
5. Number tasks sequentially (T001, T002...)
6. Validate: Single-file approach, progressive enhancement, constitutional compliance
```

## Format: `[ID] [P?] Description`
- **[P]**: Can run in parallel (different files, no dependencies)
- Include exact file paths in descriptions

## Path Conventions
- **Static website**: `index.html` at repository root
- **Testing**: Manual verification, browser testing
- Single HTML file with inlined CSS and JavaScript

## Phase 3.1: Setup
- [x] T001 Create basic HTML5 document structure in index.html with semantic elements
- [x] T002 [P] Create tests/manual/ directory structure for testing checklists
- [x] T003 [P] Create tests/validation/ directory for HTML/CSS validation results

## Phase 3.2: Core HTML Structure ⚠️ VALIDATE BEFORE STYLING
**CRITICAL: HTML structure and accessibility MUST be complete before styling**
- [x] T004 Implement semantic HTML form structure in index.html per form-interface.md contract
- [x] T005 Add proper form labels, ARIA attributes, and accessibility features to index.html
- [x] T006 [P] Validate HTML structure with W3C validator, document results in tests/validation/
- [x] T007 [P] Test form submission without JavaScript to Google (fallback functionality)

## Phase 3.3: CSS Styling & Layout
- [x] T008 Add inline CSS to index.html for responsive form styling and layout
- [x] T009 Implement mobile-first responsive design within the <style> tag in index.html
- [x] T010 [P] Add focus management and visual accessibility indicators in CSS
- [x] T011 [P] Optimize CSS for performance (<2KB total size, minified inline styles)

## Phase 3.4: JavaScript Enhancement
- [x] T012 Implement processAndRedirect() function in inline <script> tag per contract spec
- [x] T013 Add form submission handler with "-ai" suffix logic to index.html
- [x] T014 Implement duplicate "-ai" detection and proper URL encoding in JavaScript
- [x] T015 Add input validation and error handling for edge cases in JavaScript

## Phase 3.5: Testing & Validation
- [x] T016 [P] Execute all basic search functionality tests from quickstart.md
- [x] T017 [P] Execute all edge case testing scenarios from quickstart.md
- [x] T018 [P] Execute accessibility testing (keyboard nav, screen reader) from quickstart.md
- [x] T019 [P] Execute browser compatibility testing across Chrome, Firefox, Safari
- [x] T020 [P] Create manual testing checklist in tests/manual/testing-checklist.md

## Phase 3.6: Performance & Optimization
- [x] T021 Verify page load time <2 seconds on 3G connection
- [x] T022 Optimize and minify inline CSS and JavaScript within index.html
- [x] T023 Verify total page size <50KB as per performance contract
- [x] T024 [P] Test and verify form submission performance <100ms processing time

## Phase 3.7: Deployment Preparation
- [x] T025 Verify index.html works correctly when served from file:// protocol
- [x] T026 Test index.html served from local HTTP server (simulating CDN)
- [x] T027 [P] Create simple deployment documentation for Netlify drag-and-drop
- [x] T028 [P] Perform final constitutional compliance check (static-first, CDN-ready, etc.)

## Dependencies
- HTML structure (T004-T007) before styling (T008-T011)
- HTML and CSS complete before JavaScript (T012-T015)
- Implementation complete before testing (T016-T020)
- All functionality complete before optimization (T021-T024)
- Everything ready before deployment prep (T025-T028)

## Parallel Example
```
# Launch T002-T003 together (directory setup):
Task: "Create tests/manual/ directory structure for testing checklists"
Task: "Create tests/validation/ directory for HTML/CSS validation results"

# Launch T016-T020 together (independent testing):
Task: "Execute all basic search functionality tests from quickstart.md"
Task: "Execute all edge case testing scenarios from quickstart.md"
Task: "Execute accessibility testing (keyboard nav, screen reader) from quickstart.md"
Task: "Execute browser compatibility testing across Chrome, Firefox, Safari"
Task: "Create manual testing checklist in tests/manual/testing-checklist.md"
```

## Notes
- Single HTML file approach - no parallel editing of index.html
- Progressive enhancement - form works without JavaScript
- Inline CSS/JS for optimal performance and constitutional compliance
- Manual testing focus (no automated test frameworks)
- CDN deployment ready (static-first principle)

## Task Generation Rules
*Applied during main() execution*

1. **From Form Interface Contract**:
   - HTML form structure → core implementation task
   - JavaScript enhancement → separate enhancement task
   - Performance requirements → optimization tasks [P]

2. **From Quickstart Scenarios**:
   - Each testing category → manual testing task [P]
   - Browser compatibility → cross-browser testing task [P]
   - Deployment verification → deployment prep tasks [P]

3. **From Research Decisions**:
   - Progressive enhancement → fallback testing task
   - Inline assets → optimization and minification tasks
   - Accessibility → semantic HTML and ARIA tasks

4. **Ordering**:
   - Setup → HTML → CSS → JavaScript → Testing → Optimization → Deployment
   - Constitutional compliance verification throughout

## Validation Checklist
*GATE: Checked by main() before returning*

- [x] Single HTML file approach (no conflicting parallel edits)
- [x] Progressive enhancement (JavaScript disabled fallback)
- [x] Manual testing tasks cover all quickstart scenarios
- [x] Performance testing includes constitutional requirements (<2s, <50KB)
- [x] All tasks specify exact file path (index.html or test directories)
- [x] Constitutional compliance verification included
- [x] Netlify deployment preparation included