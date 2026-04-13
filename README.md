# FOSSEE Workshop Booking: UI/UX Enhancement

UI/UX redesign of the FOSSEE `workshop_booking` Django monolith completed for the Summer Fellowship Python Screening Task.

This repository keeps the original Django backend workflows intact while improving the frontend experience through Django templates, shared CSS, and lightweight enhancements focused on usability, responsiveness, accessibility, and visual clarity.

## Project Overview

The application is a workshop coordination portal where:

- Coordinators can register, manage their profiles, and propose workshops.
- Instructors can review workshop requests, accept proposals, and manage workshop dates.
- Users can browse workshop types and view public statistics.

This project is **not** a React or Node application. It uses:

- Django templates for HTML rendering
- Static CSS/JS assets for frontend behavior
- Django forms and server-rendered views for interaction

## Repository Structure

```text
workshop_booking/
├── cms/                         # CMS pages and navigation models/templates
├── docs/
│   ├── Getting_Started.md
│   └── screenshots/
│       ├── before/
│       └── after/
├── statistics_app/             # Public/team statistics pages
├── teams/                      # Team-related models
├── workshop_app/               # Core booking workflows, templates, forms, static files
│   ├── static/workshop_app/
│   │   ├── css/base.css        # Shared UI stylesheet
│   │   ├── js/                 # Existing JS utilities
│   │   └── img/                # Existing images/assets
│   └── templates/
│       ├── registration/       # Password/auth templates
│       └── workshop_app/       # Main application templates
├── workshop_portal/            # Django project settings and root URLs
├── manage.py
└── requirements.txt
```

## Frontend-Related Files

### Main templates

- `workshop_app/templates/workshop_app/base.html`
- `workshop_app/templates/workshop_app/login.html`
- `workshop_app/templates/workshop_app/register.html`
- `workshop_app/templates/workshop_app/propose_workshop.html`
- `workshop_app/templates/workshop_app/workshop_type_list.html`
- `workshop_app/templates/workshop_app/workshop_type_details.html`
- `workshop_app/templates/workshop_app/workshop_status_coordinator.html`
- `workshop_app/templates/workshop_app/workshop_status_instructor.html`
- `workshop_app/templates/workshop_app/workshop_details.html`
- `workshop_app/templates/workshop_app/view_profile.html`
- `workshop_app/templates/workshop_app/add_workshop_type.html`
- `workshop_app/templates/workshop_app/edit_workshop_type.html`
- `workshop_app/templates/workshop_app/activation.html`
- `workshop_app/templates/workshop_app/logout.html`

### Auth and password templates

- `workshop_app/templates/registration/password_reset_form.html`
- `workshop_app/templates/registration/password_reset_done.html`
- `workshop_app/templates/registration/password_reset_confirm.html`
- `workshop_app/templates/registration/password_reset_complete.html`
- `workshop_app/templates/registration/password_change_form.html`
- `workshop_app/templates/registration/password_change_done.html`

### Static frontend files

- `workshop_app/static/workshop_app/css/base.css`
- `workshop_app/static/workshop_app/js/*.js`
- `workshop_app/static/workshop_app/img/*`
- `cms/templates/cms_base.html`

## Main UI Pages Identified

- Login page
- Coordinator registration page
- Coordinator dashboard
- Instructor dashboard
- Workshop types listing
- Workshop type detail page
- Propose workshop form
- Workshop detail and comments page
- Profile view/edit page
- Password reset/change pages
- CMS pages
- Public statistics page

## Setup Instructions

### Recommended environment

- Python `3.11` is the safest option for Django `3.0.7`
- Python `3.12` also works if `setuptools` is installed in the virtual environment

### Local setup

```powershell
cd C:\Users\Abhay\Desktop\SUMMER_INTERNSHIP\workshop_booking
python -m venv .venv
.venv\Scripts\Activate.ps1
pip install -r requirements.txt
pip install setuptools
python manage.py migrate
python manage.py createsuperuser
python manage.py runserver
```

Open:

- `http://127.0.0.1:8000/`
- `http://127.0.0.1:8000/admin/`

### Important note about migrations

The repository was missing initial migrations for `cms` and `teams`, so this enhancement adds:

- `cms/migrations/0001_initial.py`
- `teams/migrations/0001_initial.py`

Without them, the root route can fail because `cms.Page` is queried before the corresponding tables exist.

## Exact Commands Used To Run The Project

If `.venv` already exists:

```powershell
cd C:\Users\Abhay\Desktop\SUMMER_INTERNSHIP\workshop_booking
.venv\Scripts\Activate.ps1
python manage.py migrate
python manage.py runserver 127.0.0.1:8000
```

If PowerShell blocks activation:

```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
.venv\Scripts\Activate.ps1
```

## UI Improvements Summary

### Shared layout and navigation

- Redesigned the main navbar with stronger branding, clearer actions, and improved spacing.
- Added unauthenticated CTA actions for login and registration.
- Added semantic header, main, and footer structure.
- Added a skip link for keyboard users.
- Added meta descriptions and cleaner page titles.

### Homepage and entry flow

- Treated login as a stronger landing experience with a hero section and concise product messaging.
- Improved visual hierarchy for first-time and returning users.

### Workshop listing and detail pages

- Replaced dense table-first listing with card-based workshop type browsing.
- Improved details layout using readable content sections instead of flat tables.
- Fixed pagination markup and made navigation clearer.

### Dashboard and forms

- Refreshed coordinator and instructor dashboards with hero sections, clearer section labels, and cleaner tables.
- Reworked registration, proposal, password, and profile forms with better spacing, labels, and feedback.
- Preserved all backend form handling and URL flows.

### Footer

- Replaced the fixed footer with a flexible footer that no longer overlaps content.
- Added quick navigation and stronger site identity.

## Design Principles Used

### 1. Clear visual hierarchy

Large headings, concise supporting copy, and section grouping were used to help users scan quickly and understand the next action.

### 2. Reduced friction

Important actions such as login, registration, proposal submission, and workshop review are now easier to find and visually prioritized.

### 3. Consistency

The redesign uses a shared design language across pages:

- common hero pattern
- shared cards
- consistent button styles
- unified forms
- consistent spacing and color system

### 4. Lightweight practicality

The implementation keeps the existing stack intact and does not introduce heavy UI frameworks or frontend build tooling.

## Responsiveness Approach

The UI is built to work across mobile, tablet, and desktop using:

- CSS Grid for responsive content sections
- Flexbox for nav, actions, and metadata rows
- responsive spacing and container sizing
- table wrappers to prevent horizontal breakage
- stacked button and form layouts on narrow screens

### Mobile-first improvements applied

- reduced padding on small screens
- stacked CTA buttons and form fields
- responsive card grid for workshop types
- removal of fixed footer overlap issues
- better touch-friendly spacing for navigation and actions

## Accessibility Improvements

- Added semantic `header`, `main`, and `footer` structure
- Added a keyboard-accessible skip link
- Improved label visibility and form readability
- Increased contrast between text and backgrounds
- Improved focus states for inputs, buttons, links, and pagination
- Added clearer status badges and section headings

## SEO Improvements

- Added `meta` descriptions to main templates
- Improved page title structure
- Strengthened heading hierarchy with clearer page-level `h1` usage
- Reduced generic placeholder titles

## Design vs Performance Trade-Offs

The redesign favors noticeable UX improvements while staying lightweight:

- Reused Bootstrap and the existing JS stack instead of introducing new frontend dependencies
- Added typography and richer layout styling via CSS rather than JavaScript-heavy interactions
- Kept server-rendered templates and backend logic unchanged for reliability

Trade-off:

- The visual layer is significantly improved, but still constrained by the existing Django template structure and legacy project organization

## Challenges Faced

- The project is a Django monolith with older template patterns and table-heavy layouts.
- The existing repository had no `package.json`, so the frontend had to be improved entirely through templates and static files.
- The initial environment used Python `3.12`, which required `setuptools` to avoid the `distutils` import issue with Django `3.0.7`.
- The repository was missing initial migrations for `cms` and `teams`, which prevented a clean local run until those were added.
- The existing test suite contains a pre-existing broken import: `edit_profile` is referenced in `workshop_app/tests/test_views.py` but does not exist in `workshop_app/views.py`.

## Verification Notes

The following checks were run locally:

- `python manage.py check`
- `python manage.py migrate --noinput`
- `python manage.py runserver 127.0.0.1:8000`

Smoke-tested routes:

- `/`
- `/workshop/login/`
- `/workshop/register/`
- `/workshop/types/`
- `/statistics/public`

Known pre-existing issue:

- `python manage.py test workshop_app.tests.test_views statistics_app.tests.test_views`
  fails because `workshop_app/tests/test_views.py` imports a missing `edit_profile` view that is not part of this UI enhancement.

## Before / After Screenshots

Store screenshots here:

- `docs/screenshots/before/`
- `docs/screenshots/after/`

Suggested captures:

1. Login page
2. Registration page
3. Coordinator dashboard
4. Instructor dashboard
5. Workshop types listing
6. Propose workshop form
7. Profile page
8. Workshop details/comments page

Markdown example after saving screenshots:

```md
## Screenshots

### Before
![Login Before](docs/screenshots/before/login-before.png)
![Workshop Types Before](docs/screenshots/before/workshop-types-before.png)

### After
![Login After](docs/screenshots/after/login-after.png)
![Workshop Types After](docs/screenshots/after/workshop-types-after.png)
```

## Suggested Git Workflow

Use multiple clean commits instead of one large dump.

Suggested commit sequence:

1. `git add workshop_app/forms.py workshop_app/templates/workshop_app/base.html workshop_app/static/workshop_app/css/base.css cms/templates/cms_base.html`
   `git commit -m "Redesign shared layout and form styling"`

2. `git add workshop_app/templates/workshop_app/login.html workshop_app/templates/workshop_app/register.html workshop_app/templates/workshop_app/propose_workshop.html workshop_app/templates/registration`
   `git commit -m "Improve authentication and proposal flows"`

3. `git add workshop_app/templates/workshop_app/workshop_type_list.html workshop_app/templates/workshop_app/workshop_type_details.html workshop_app/templates/workshop_app/add_workshop_type.html workshop_app/templates/workshop_app/edit_workshop_type.html`
   `git commit -m "Refresh workshop catalog and workshop type screens"`

4. `git add workshop_app/templates/workshop_app/workshop_status_coordinator.html workshop_app/templates/workshop_app/workshop_status_instructor.html workshop_app/templates/workshop_app/workshop_details.html workshop_app/templates/workshop_app/view_profile.html`
   `git commit -m "Modernize dashboards, profile, and workshop details"`

5. `git add cms/migrations teams/migrations README.md docs/screenshots`
   `git commit -m "Add missing migrations and document UI enhancement work"`

## Submission Checklist

- Push the completed project to a public GitHub repository
- Ensure `.venv/` is not committed
- Include before/after screenshots
- Confirm `README.md` is updated
- Mention that the project remains a Django monolith
- Mention that no unnecessary frameworks were added

## Final Submission Email Template

```text
Subject: FOSSEE Summer Fellowship Python Screening Task Submission - UI/UX Enhancement

Hello Team FOSSEE,

I am submitting my solution for the Summer Fellowship Python Screening Task: UI/UX Enhancement.

Project Repository:
<YOUR_GITHUB_REPO_LINK>

In this submission, I worked on the existing Django-based workshop_booking project and focused on improving the UI/UX while keeping the backend functionality intact. The work includes:

- responsive redesign of core templates
- improved navigation and layout hierarchy
- cleaner forms and workshop flows
- accessibility and readability improvements
- README updates with setup notes and screenshot documentation

The repository also includes before/after screenshots and a summary of the design decisions taken during the enhancement process.

Thank you for your time and consideration.

Best regards,
<YOUR_NAME>
```

## Submission Note

This enhancement intentionally keeps the project human-scale and realistic:

- no frontend framework migration
- no heavy dependencies
- no backend workflow rewrites
- focused, practical UI/UX improvements that fit the existing Django codebase
