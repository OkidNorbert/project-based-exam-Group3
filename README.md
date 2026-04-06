# Software Construction Exam Project

A full-stack movie discovery platform built with **Django REST Framework** (backend) and **Next.js** (frontend), powered by The Movie Database (TMDB) API.

## Project Structure

```
├── backend/          # Django REST API
│   ├── cinequest/    # Project settings & URLs
│   ├── movies/       # Movies app (models, views, TMDB service)
│   ├── users/        # Custom user model & auth
│   └── recommendations/  # Recommendation engine & watchlist
├── frontend/         # Next.js application
│   ├── src/app/      # Pages (home, search, movie detail, etc.)
│   ├── src/components/  # Reusable UI components
│   ├── src/lib/      # API client, auth context, utilities
│   └── src/types/    # TypeScript type definitions
```

## Getting Started

### Backend

```bash
cd backend
python -m venv venv
source venv/bin/activate   # Windows: venv\Scripts\activate
pip install -r requirements.txt
python manage.py migrate
python manage.py sync_movies --genres
python manage.py sync_movies --trending 2
python manage.py runserver
```

### Frontend

```bash
cd frontend
npm install
npm run dev
```

### Environment Variables

Create a `.env` file in the `backend/` directory:

```
TMDB_API_KEY=your_tmdb_api_key_here
DJANGO_SECRET_KEY=your_secret_key_here
DEBUG=True
```

## TMDB API

Get your free API key at: https://www.themoviedb.org/settings/api

# project-based-exam

WORK DISTRUBITION

| Member                            | Role                             | Main tasks                                                                                                                            | Suggested branch                |
| --------------------------------- | -------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------- |
| **EZAMAMTI Austine Ronald** | Backend Lead                     | Django setup, virtual environment,`.env`, TMDB key setup, migrations, app naming fixes, backend structure review                    | `feat/backend-core-fixes`     |
| **OKIDI Norbert**           | Full-Stack Integration Lead      | Connect frontend to backend, fix data flow mismatches, ensure homepage/search/trailer work end-to-end, support innovation integration | `feat/fullstack-integration`  |
| **ODONGKARA Oscar**         | API & Data Sync Engineer         | Fix CORS, HTTP methods, validate endpoints, management commands for trending and genres, clean JSON responses                         | `fix/api-sync-cors`           |
| **WANGOLO Bachawa**         | Frontend Logic Lead              | Add TypeScript definitions, fix prop mismatches, repair search visibility, solve frontend compile errors                              | `fix/frontend-types-search`   |
| **REBECCA Alinda**          | Testing & Report Lead            | Coordinate test evidence, collect screenshots/logs, write testing section, track untested risks, support `CONTRIBUTIONS.md`         | `docs/testing-report`         |
| **AHUMUZA Williams**        | Frontend UI Support              | UI polish, homepage rendering support, trailer modal UI support, help with frontend/component tests                                   | `test/frontend-ui`            |
| **NATUKUNDA Warudata**      | Backend Test Support             | Write backend unit tests, test API endpoints, validate sync behaviour, record test cases/results                                      | `test/backend-api`            |
| **KIRABO Jorryn Edna.T.**   | Documentation & Workflow Support | Maintain `CONTRIBUTIONS.md`, organise PR descriptions, help standardise commit messages, compile member notes for report            | `docs/contributions-workflow` |
| **EBONG Jesse Johnson**     | Innovation Frontend Support      | Build frontend UI for the unique feature, support user flow, help demo and test the feature                                           | `feat/innovation-ui`          |
| **MUNANURA Shane**          | Innovation Backend Support & QA  | Build backend logic/models/endpoints for innovation feature, support feature testing, bug validation, demo readiness                  | `feat/innovation-backend`     |
