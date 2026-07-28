# Agent Instructions for skills-copilot-code-review

Use this file as the default playbook for code changes in this repository.

## Project Snapshot

- Backend: FastAPI app in [src/app.py](src/app.py)
- Data store: MongoDB via PyMongo in [src/backend/database.py](src/backend/database.py)
- API routes: [src/backend/routers/activities.py](src/backend/routers/activities.py), [src/backend/routers/auth.py](src/backend/routers/auth.py)
- Frontend: plain HTML/CSS/JS in [src/static/index.html](src/static/index.html), [src/static/styles.css](src/static/styles.css), [src/static/app.js](src/static/app.js)

## Setup and Run

- Install deps: `pip install -r requirements.txt`
- Run app (from repository root): `python -m src.app`
- Open UI: `http://localhost:8000/static/index.html`
- API docs: `http://localhost:8000/docs`

MongoDB must be reachable at `mongodb://localhost:27017/`.

## Coding Conventions

- Keep the stack simple: use FastAPI + PyMongo + vanilla JS/CSS (no framework migrations).
- Preserve existing endpoint style:
- Use module-level APIRouters under `src/backend/routers`.
- Keep existing route prefixes (`/activities`, `/auth`) unless a new domain requires a new router.
- Keep frontend interactions in `src/static/app.js`; avoid inline scripts in HTML.
- Prefer incremental edits over broad refactors.

## Data and Auth Constraints

- Teacher auth is currently lightweight and query-param based (see `/auth/login` and `teacher_username` checks).
- Do not expose password hashes or break Argon2 verification flow in [src/backend/database.py](src/backend/database.py).

## Validation Before Finishing

- Verify app starts without import errors.
- Verify activity list and filtering still work.
- Verify login/logout still updates UI state correctly.
- For API edits, sanity-check happy path and auth failure path.

## Linked Docs

- Top-level context: [README.md](README.md)
- App-level API context: [src/README.md](src/README.md)
