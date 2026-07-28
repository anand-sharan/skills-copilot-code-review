---
description: "Implement add-announcement-banner for teacher-created announcements across backend, data, and frontend with validation"
---

# Add Announcement Banner Implementation

Implement the `add-announcement-banner` feature end to end in this repository.

## Goal

Allow authenticated teachers to create and manage an announcement that is shown as a banner in the web UI while preserving existing activities, signup, and auth behavior.

## Constraints

- Keep changes incremental and scoped to the feature.
- Keep the existing stack: FastAPI + PyMongo + vanilla HTML/CSS/JS.
- Do not break Argon2 auth verification or existing teacher auth checks.
- Keep frontend logic in `src/static/app.js` and avoid inline scripts.

## Required Work

1. Backend API
- Add announcement endpoints in a dedicated router under `src/backend/routers`.
- Include the new router in `src/app.py`.
- Provide read endpoint for banner display and teacher-protected create/update/delete endpoints.
- Return simple JSON payloads suitable for frontend rendering.

2. Data Layer
- Add/use a dedicated announcements collection in `src/backend/database.py`.
- Define a minimal schema shape (title, message, author, timestamps, active flag as needed).

3. Frontend UI
- Add banner container near the header in `src/static/index.html`.
- Add teacher-only controls for creating/updating announcements.
- Implement fetch/render/create/update/delete logic in `src/static/app.js`.
- Style the banner and controls in `src/static/styles.css` using existing CSS variables.

4. Auth Behavior
- Anonymous users can view the banner when active (if public display is intended).
- Only logged-in teachers can manage announcements.

## Validation

- Run the app and verify no import/runtime errors.
- Verify:
  - activity listing and filters still work,
  - login/logout still updates UI state correctly,
  - announcement banner renders correctly,
  - teacher CRUD actions succeed when authenticated,
  - teacher CRUD actions fail with correct auth errors when unauthenticated.

## Delivery Format

Provide:
- changed files,
- summary of backend/data/frontend changes,
- test/validation steps run and outcomes,
- follow-up risks or TODOs if any.
