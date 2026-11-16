# School Attendance System · سیستەمی ئامادەبوونی قوتابخانە

A web-based school attendance system with RFID card scanning, an admin panel,
student registration, printable student ID cards, and a teacher view.
Built with HTML, CSS, JavaScript (ES modules) and Firebase. Hosted on GitHub Pages.

## Features

- Staff login with role check (`admin` / `staff`) via Firebase Authentication
- RFID card scanner screen for recording attendance
- Admin panel: students, reports, daily status, PDF export
- Student registration and editing
- Automatic student ID card generation (per class, folder or ZIP download)
- Teacher page for class absences

## Project structure

```
.
├── index.html          # Login
├── home.html           # Staff dashboard
├── admin.html          # Admin panel (reports + ID card generator)
├── register.html       # Student registration / editing
├── scanner.html        # RFID attendance scanner
├── teacher.html        # Teacher view
├── js/
│   ├── firebase-config.js   # Firebase initialisation
│   └── auth-guard.js        # Auth + role protection for pages
└── assets/
    ├── images/         # Logos used by the UI
    └── card/           # Templates used for ID card generation
```

## Deploy on GitHub Pages

1. Push this folder to a GitHub repository.
2. **Settings → Pages → Source:** `Deploy from a branch`, branch `main`, folder `/ (root)`.
3. Open `https://<username>.github.io/<repository>/`.

## Local development

ES modules need a web server (opening the files directly will not work):

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

## Firebase setup

- Enable **Email/Password** in Authentication.
- Staff accounts must exist in Realtime Database under `staff/<uid>` with
  `{ "name": "...", "role": "admin" | "staff" }`.
- In Authentication → Settings, add your `github.io` domain to **Authorized domains**.
- The Firebase web config is public by design; real protection comes from
  **Realtime Database / Storage security rules** — make sure they require
  `auth != null` and restrict writes appropriately.
