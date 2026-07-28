---
applyTo: "src/static/index.html,src/static/app.js,src/static/styles.css,src/backend/routers/*.py,src/backend/database.py"
description: "Use when implementing the add-announcement-banner feature for teacher-created announcements"
---

# Add Announcement Banner Guidance

Use these rules when adding teacher announcements that appear as a banner in the web UI.

## Scope

- Keep the feature focused on a banner-style announcement area in the existing frontend.
- Avoid unrelated UI redesigns or architecture rewrites.

## Frontend Rules

- Add the banner markup in [src/static/index.html](src/static/index.html) near the header section.
- Implement fetch/render/visibility logic in [src/static/app.js](src/static/app.js).
- Add styles in [src/static/styles.css](src/static/styles.css) using existing CSS variables and naming style.
- Keep login/logout behavior intact. Announcement creation controls should be teacher-only.

## Backend Rules

- Add any new teacher announcement endpoints in a dedicated router under `src/backend/routers` and include it from [src/app.py](src/app.py).
- Keep response payloads simple JSON for easy frontend rendering.
- Enforce teacher authentication checks for create/update/delete operations.

## Data Rules

- If persistence is needed, define a dedicated MongoDB collection in [src/backend/database.py](src/backend/database.py).
- Keep announcement document shape explicit and minimal (title/message/timestamps/author).

## Acceptance Checks

- Not logged in: banner display works for public view (if intended), but no create/edit controls are shown.
- Logged in as teacher: create announcement path works and updates banner state.
- Existing activity filtering, sign-up, and authentication flows remain functional.
