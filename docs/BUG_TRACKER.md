# BUG ANALYSIS & FIX TRACKER 

This document tracks every bug identified during the **CineQuest Project** Restoration Phase as per Group 3's exam requirements.

---

| Bug ID | Component | Description | Phase | Fix Implemented | Status | Impact |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **BUG-001** | Backend (`settings.py`) | Typo in `INSTALLED_APPS` (referenced as `"movie"` instead of `"movies"`) | Backend Restoration | Changed to `"movies.apps.MoviesConfig"` | **FIXED** ✅ | Unblocked Django startup and migration capability. |
| **BUG-002** | Backend (Migrations) | Database was uninitialized; 21 migrations were missing. | Backend Restoration | Successfully executed `python manage.py migrate` | **FIXED** ✅ | Created SQLite tables for users, movies, and recommendations. |
| **BUG-003** | Backend (`settings.py`) | Missing `CorsMiddleware` from the `MIDDLEWARE` list. | Backend Restoration | *Needs Action* (Add to top of MIDDLEWARE list) | *PLANNED* ⏳ | Frontend will be blocked from fetching any data until fixed. |
| **BUG-004** | Backend (Sync Commands) | Local database contains zero entries; frontend is empty. | Backend Restoration | *Needs Action* (Run `sync_movies` after setting `.env`) | *PLANNED* ⏳ | Essential for homepage, search, and trailer functionality. |
| **BUG-005** | Backend (`views.py`) | `search` and `trending` endpoints are incorrectly set to `POST` methods. | Backend Restoration | *Needs Action* (Change decorators from `@api_view(["POST"])` to `["GET"]`) | *PLANNED* ⏳ | Allows standard browser URL-based searching and trending fetching. |
| **BUG-006** | Frontend (`page.tsx`) | `trending` state consumes a Paginated Object instead of a Movie Array. | Frontend Reconstruction | *Needs Action* (Need to map to `results` array in the component) | *PLANNED* ⏳ | Prevents "undefined" errors when the carousel tries to loop over data. |
| **BUG-007** | Frontend (Types) | Missing strict TypeScript interfaces for Movie data and API Responses. | Frontend Reconstruction | *Needs Action* (Add to `/types/movie.ts`) | *PLANNED* ⏳ | Improves code quality, editor support, and prevents silent UI failures. |

---

## 🛠 Required Environment Variables

To fix **BUG-004**, create a `.env` in the `backend/` folder:

```bash
TMDB_API_KEY=your_v3_key_here
DJANGO_SECRET_KEY=exam-secret-key-123
DEBUG=True
```

## 📜 Git Rules Reminder
- **Never** commit directly to `main`.
- Each fix should be pushed to your own feature branch first (**`feat/fullstack-integration`**).
- Link each PR to a Bug ID for traceability.
