# CineQuest Backend: Django REST API

Welcome to the CineQuest backend repository. This application serves as the core data and authentication layer for the CineQuest movie discovery platform, providing JSON endpoints for the Next.js frontend and acting as a synchronization bridge to the external TMDB API.

---

## 🛠 Prerequisites

Before starting, ensure you have the following installed on your machine:
* **Python** (v3.10 or higher)
* **pip** (Python package manager)
* **SQLite** (Default) or **PostgreSQL** (Production ready)
* Optionally: **Redis** (if caching is enabled via the environment)

---

## 🚀 Local Setup & Installation

1. **Create a Virtual Environment**
   It natively isolates the project's dependencies from your global Python environment.
   ```bash
   cd backend
   python -m venv venv
   source venv/bin/activate       # On Mac/Linux
   venv\Scripts\activate          # On Windows
   ```

2. **Install Dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Configure Environment Variables**
   Create a `.env` file in the root of the `backend/` folder (next to `manage.py`). **Never commit this file.**
   ```env
   TMDB_API_KEY=your_tmdb_api_key_v3_here
   DJANGO_SECRET_KEY=super-secret-local-key
   DEBUG=True
   ALLOWED_HOSTS=localhost,127.0.0.1
   CORS_ORIGINS=http://localhost:3000,http://127.0.0.1:3000
   ```

4. **Run Database Migrations**
   ```bash
   python manage.py makemigrations
   python manage.py migrate
   ```

5. **Seed the Local Database (TMDB Sync)**
   Populate your empty database with initial content.
   ```bash
   python manage.py sync_movies --genres
   python manage.py sync_movies --trending 2
   ```

6. **Start the Development Server**
   ```bash
   python manage.py runserver
   ```
   The API will now be available at `http://127.0.0.1:8000/`.

---

## 🏗 Architecture & System Breakdown

The Django configuration utilizes a micro-app structure to separate concerns:

| App Name | Primary Responsibility |
| :--- | :--- |
| **`cinequest`** | Core router, `settings.py` (CORS, auth settings), environment loader. |
| **`movies`** | `Movie` schemas, trending fetching, TMDB integration services, and DRF ViewSets. |
| **`users`** | Custom `User` models built for JWT Authentication via `SimpleJWT`. |
| **`recommendations`** | Algorithms and data models mapping user watchlists to movie similarity vectors. |

### File Structure Map
```text
backend/
├── cinequest/            # Core settings and URL router
│   ├── settings.py       # <--- Environment and App definitions
│   └── urls.py           # <--- Main routing
├── manage.py             # Django entry terminal script
├── movies/               # Core Movie App
│   ├── management/       # Script jobs
│   │   └── commands/sync_movies.py # <--- Task to populate Database from TMDB
│   ├── models.py         # DB Schemas
│   ├── serializers.py    # JSON data mapping
│   ├── services/
│   │   └── tmdb_service.py # <--- External HTTP wrapper for TMDB
│   ├── urls.py           # Movie endpoints
│   └── views.py          # Route controllers
├── recommendations/      # Recommender Engine App
│   ├── models.py
│   ├── serializers.py
│   ├── services/engine.py
│   └── views.py
├── requirements.txt      # Python dependencies
└── users/                # Authentication App
    ├── models.py
    ├── urls.py
    └── views.py          # Session and user generation
```

### Data Flow Diagram

```mermaid
sequenceDiagram
    participant Frontend
    participant DjangoRouter (urls.py)
    participant Views & Serializers
    participant TMDB_Service
    participant SQLite DB

    Frontend->>DjangoRouter: GET /api/movies/trending/
    DjangoRouter->>Views & Serializers: Route to TrendingView
    
    alt Data in Database?
        Views & Serializers->>SQLite DB: Query Local Movies
        SQLite DB-->>Views & Serializers: Return Movie QuerySet
    else Data Missing?
        Views & Serializers->>TMDB_Service: Fetch from API
        TMDB_Service->>TMDB_Service: Request TMDB API
        TMDB_Service-->>Views & Serializers: JSON Raw Response
        Views & Serializers->>SQLite DB: Save Models
    end
    
    Views & Serializers-->>Frontend: HTTP 200 OK (JSON)
```

---

## 🧪 Testing Protocol

Testing is mandatory for our final exam grade. We require a minimum of 5 backend unit tests.

**To Run Tests:**
```bash
python manage.py test
# OR if pytest is configured later:
pytest
```

**What you should be testing:**
- Do models save correctly with valid data?
- Does `GET /movies/` require auth, or is it public?
- Does the TMDB sync script throw errors if the API key is invalid?

---

## 🚨 Troubleshooting & Common Issues

- **`ModuleNotFoundError: No module named 'movie'`**: Check if `"movie.apps.MoviesConfig"` is in `settings.py` `INSTALLED_APPS` instead of `"movies"`.
- **CORS Preflight Fails**: Ensure `corsheaders.middleware.CorsMiddleware` exists in the `MIDDLEWARE` array of `settings.py`, and `CORS_ORIGINS` in your `.env` exactly matches the Next.js port.
- **Empty Database/Data Mismatch**: Ensure you ran `sync_movies --genres` *before* fetching trending movies, otherwise ForeignKey constraints for genres will crash.
