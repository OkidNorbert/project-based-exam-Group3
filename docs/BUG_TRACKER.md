# BUG ANALYSIS & FIX TRACKER 

This document tracks every bug identified during the **CineQuest Project** Restoration Phase as per Group 3's exam requirements.

---

| Bug ID | Component | Description | Phase | Fix Implemented | Status | Impact |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **BUG-001** | Backend (`settings.py`) | Typo in `INSTALLED_APPS` (referenced as `"movie"` instead of `"movies"`) | Backend Restoration | Changed to `"movies.apps.MoviesConfig"` | **FIXED** ✅ | Unblocked Django startup and migration capability. |
| **BUG-002** | Backend (Migrations) | Database was uninitialized; 21 migrations were missing. | Backend Restoration | Successfully executed `python manage.py migrate` | **FIXED** ✅ | Created SQLite tables for users, movies, and recommendations. |
| **BUG-003** | Backend (`settings.py`) | Missing `CorsMiddleware` from the `MIDDLEWARE` list. | Backend Restoration | Added `CorsMiddleware` to the top of the `MIDDLEWARE` list. | **FIXED** ✅ | Unblocked frontend API communication. |
| **BUG-004** | Backend (Sync Commands) | Local database contains zero entries; frontend is empty. | Backend Restoration | *Needs Action* (Run `sync_movies` after setting `.env`) | *PLANNED* ⏳ | Essential for homepage, search, and trailer functionality. |
| **BUG-005** | Backend (`views.py`) | `search` and `trending` endpoints are incorrectly set to `POST` methods. | Backend Restoration | Changed decorators from `["POST"]` to `["GET"]` | **FIXED** ✅ | Corrected standard data-fetching access for frontend. |
| **BUG-006** | Frontend (`page.tsx`) | `trending` state consumes a Paginated Object instead of a Movie Array. | Frontend Reconstruction | Correctly mapped the `results` array in `page.tsx` | **FIXED** ✅ | Prevents "undefined" failures when components try to slice the data. |
| **BUG-007** | Frontend (Types) | Missing strict TypeScript interfaces for Movie data and API Responses. | Frontend Reconstruction | Added `WatchlistItem`, `MovieMood`, and `RecommendationDashboard` interfaces. | **FIXED** ✅ | Improved code quality and documentation consistency. |

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
