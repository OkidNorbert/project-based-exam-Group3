# MASTER AI PROMPT FOR GROUP 3 — CINEQUEST SOFTWARE CONSTRUCTION PROJECT
**Project Objective**: To restore, fix, improve, test, document, and present a full-stack movie discovery platform built with Django REST API, Next.js, and TMDB API. 

## Non-Negotiable Exam Requirements
1. **Backend Restoration:** Virtual environment, `.env` for TMDB API key, fix Django migrations, sync database with trending/genre commands, fix app naming, fix CORS middleware, and correct HTTP methods.
2. **Frontend Reconstruction:** Add missing TypeScript definitions in `types/`, fix prop mismatches, and repair the search interface visibility.
3. **Code Quality and Refactoring:** Eliminate code smells, improve readability, apply design patterns, ensure consistent style, and add meaningful comments/docstrings.
4. **Testing and Validation:** Minimum 5 backend unit tests, 3 frontend/component tests. A report must explain what was tested, what remains untested, and the risks. All tests must pass.
5. **Git Workflow:** Everyone works on their feature branch. No direct commits to main. Each member needs 5+ meaningful commits. At least 2 PRs with review notes. `CONTRIBUTIONS.md` must list specific contributions.
6. **Innovation Feature:** One significant full-stack unique feature, fully integrated and documented. (Recommended: Personalised Watchlist + Smart Recommendations).
7. **Documentation:** 2-4 page technical report PDF containing Bug Analysis, Refactoring Decisions, Architecture Changes, Innovation Design, Testing Evidence, and Remaining Limitations. 
8. **Presentation:** Physical presentation ensuring all members participate and understand their contribution.

---

## Team Structure & Branch Plan

| Team Member | Role | Assigned Branch |
| :--- | :--- | :--- |
| **EZAMAMTI Austine Ronald** | Backend Lead (Django setup, `.env`, migrations, names) | `feat/backend-core-fixes` |
| **OKIDI Norbert** | Full-Stack Integration Lead (API to UI data flow, frontend/backend connection) | `feat/fullstack-integration` |
| **ODONGKARA Oscar** | API & Data Sync Engineer (CORS, HTTP methods, endpoints, sync commands) | `fix/api-sync-cors` |
| **WANGOLO Bachawa** | Frontend Logic Lead (TypeScript definitions, prop mismatches, search UI) | `fix/frontend-types-search` |
| **REBECCA Alinda** | Testing & Report Lead (Test evidence, reports, risk tracking) | `docs/testing-report` |
| **AHUMUZA Williams** | Frontend UI Support (UI polish, homepage, trailer modal support) | `test/frontend-ui` |
| **NATUKUNDA Warudata** | Backend Test Support (Unit tests, sync testing, endpoint tests) | `test/backend-api` |
| **KIRABO Jorryn Edna.T.** | Documentation & Workflow Support (`CONTRIBUTIONS.md`, PR details) | `docs/contributions-workflow` |
| **EBONG Jesse Johnson** | Innovation Frontend Support (Frontend UI for watchlist/features) | `feat/innovation-ui` |
| **MUNANURA Shane** | Innovation Backend Support & QA (Backend endpoints for watchlist/features) | `feat/innovation-backend` |

---

## Phase-By-Phase Execution Plan

### Phase 1: Backend Restoration (Days 1-3)
**Owner**: Austine & Oscar
- Setup virtual env and `.env` securely.
- Debug and pass all Django migrations.
- Rename applications correctly in `settings.py`.
- Apply `django-cors-headers` correctly to allow frontend connectivity.
- Correct API HTTP verbs (e.g., fixing `GET` vs `POST` in views).
- Run the provided TMDB sync management scripts to seed database.

### Phase 2: Frontend Reconstruction (Days 4-6)
**Owner**: Bachawa & Williams
- Add `types/` interfaces for movies, genres, and API responses.
- Fix broken prop passing mapping across the Next.js components (e.g., Object vs Array errors).
- Repair search visibility DOM styling constraints.

### Phase 3: Integration & QA (Days 7-8)
**Owner**: Norbert & Team
- Home, search, and trailer flow MUST work connected to the local API.

### Phase 4: Innovation Feature (Days 9-10)
**Owner**: Shane & Jesse
- Implement *Personalised Watchlist & Smart Recommendations*.
- Update Models (Backend) and Services (Frontend).

### Phase 5: Code Quality & Testing (Days 11-12)
**Owner**: Warudata, Williams, & Alinda
- Refactor long functions and duplicate CSS/API logic into helpers.
- Run `pytest`/Django tests ensuring 5 units pass on backend.
- Run 3 component tests on frontend.

### Phase 6: Reporting & Report Assembly (Days 13-14)
**Owner**: Jorryn & Alinda
- Aggregate PR links, member commits, and test proofs into Report and `CONTRIBUTIONS.md`.

---

## 2-Week Work Plan (14-Day Roadmap)
1. **Day 1-2**: Repository pulled, `.env` distributed safely off-git, Git branches checked out. Migration fixes deployed.
2. **Day 3-4**: Backend API serving correctly via Postman. Sync applied.
3. **Day 5-6**: Frontend boots locally, TypeScript compiler passes without errors, UI renders.
4. **Day 7**: End-To-End API fetching verified.
5. **Day 8-9**: Refactoring passes: duplicate code removed, code formatted. Watchlist API added.
6. **Day 10**: Watchlist frontend hooked to backend.
7. **Day 11**: All backend and frontend automated tests written.
8. **Day 12**: QA runs. All bugs listed in documentation.
9. **Day 13**: Finalize `CONTRIBUTIONS.md`. Export evidence screenshots.
10. **Day 14**: Freeze code. PDF compilation. Presentation rehearsals.

---

## Task Dependency Map
* Cannot test frontend logic UNTIL `types/` are structurally fixed.
* Cannot start full-stack integration UNTIL `migrations` succeed and `CORS` is enabled.
* Cannot populate database UNTIL TMDB API Key `.env` is loaded by all members locally.
* Cannot pass workflow grade if any PR bypasses member code review.

---

## Checklists

### Backend Checklist
- [ ] `.env` loaded securely, not in source control.
- [ ] Migrations applied successfully.
- [ ] Application names mapped correctly in `INSTALLED_APPS`.
- [ ] Missing CORS middleware enabled for `localhost:3000`.
- [ ] HTTP endpoint logic matches requests.

### Frontend Checklist
- [ ] TypeScript interfaces defined clearly (no implicit `any`).
- [ ] Search input state binds to URL or local state securely.
- [ ] Trailer modal handles empty states gracefully.

### Testing Checklist
- [ ] 5x backend API behaviour tests.
- [ ] 3x frontend component rendering tests.
- [ ] Tests execute without failure on local machines.

---

## GitHub Workflow & PR Guide
* NEVER commit directly to `main`.
* Checkout your assigned branch: `git checkout <your-assigned-branch>`
* Stage your work: `git add <file>`
* Commit descriptively: `git commit -m "fix(backend): resolved CORS issue in settings.py"` or `git commit -m "feat(frontend): added trailer modal component"`
* Push and PR to `main` when working locally is complete.
* Another team member must review the PR and comment before merging.

## Code Review Checklist
- [ ] Does this break existing features?
- [ ] Are variable names descriptive, or are they `x` and `foo`?
- [ ] Does this follow the established formatting style?
- [ ] Is there an obvious lack of Typescript types (`any`)?

---

## `CONTRIBUTIONS.md` Template
Create a file named `CONTRIBUTIONS.md` in root prior to submission:
```markdown
# Group 3 Roles and Contributions
| Member | Expected Role | Exact Delivered Contribution | Github User | Commits | PRs Merged |
|---|---|---|---|---|---|
| EZAMAMTI Austine Ronald | Backend Lead | Fixed migrations, added .env parsing | @austine | 6 | 1 |
| ... | ... | ... | ... | ... | ... |
```

---

## Definition of Done (DoD)
A task is DONE only when:
1. It works on local host without terminal errors.
2. The code is pushed to your feature branch.
3. At least one team member has reviewed the code.
4. Any relevant test cases are passing.
5. The logic is self-documenting or appropriately commented.

## Final Submission Checklist
- [ ] `CONTRIBUTIONS.md` file verified by Jorryn.
- [ ] 2-4 Page Technical Report PDF approved by Alinda.
- [ ] Code base formatted cleanly, `.env` file successfully ignored.
- [ ] Live demo rehearsals finished. Ensure every member speaks!
