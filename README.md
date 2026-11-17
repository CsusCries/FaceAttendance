# Face Attendance

A free, opt-in face-recognition attendance / check-in app that runs entirely in a **tablet's web browser**. No server, no account, no installs, and nothing is uploaded.

Built on the open-source [Human](https://github.com/vladmandic/human) library (MIT license), bundled in `vendor/human/`.

## Features
- **Enroll**: name + consent checkbox + 5 camera shots.
- **Check in**: live camera recognises enrolled people (green box with their name), everyone else shows "Unknown". One check-in per person per day, downloadable as CSV.
- **People & data**: remove a person, delete all data, export/import a backup, adjust match strictness, optional liveness check (blocks photos/screens).
- **Privacy tab**: plain-language privacy note to show students, parents and staff.

## Host it for free (needed for the camera, which requires https)
**GitHub Pages:** repo **Settings → Pages → Build and deployment → Deploy from a branch → `main` / `(root)` → Save**. After a minute the app is at `https://<your-username>.github.io/FaceAttendance/`.

**Or Vercel:** import this repo at vercel.com (no build settings needed).

Open the link on the tablet, allow camera access, and optionally use "Add to Home Screen".

## Run locally
```bash
python3 -m http.server 8000
```
Then open http://localhost:8000 (the camera works on `localhost` without https).

## Tips for accuracy
- Good, even lighting; tablet steady at face height.
- Enroll people in the same place you'll check them in.
- Two people confused with each other → raise "Match strictness". Known people showing "Unknown" → lower it slightly or re-enroll.
- Works best for groups of up to about 50 people per tablet.

## Data and privacy
- Stores only a name and a **face code** (1,024 numbers) per person, never photos.
- Data stays in **that tablet's browser** (localStorage). Clearing browser data erases it, so use **Export backup**.
- First load downloads about 10 MB of models; after that the browser cache serves them.

See [PRIVACY.md](PRIVACY.md) for the privacy note and [CONSENT_FORM.md](CONSENT_FORM.md) for a parent/guardian consent form template.

**For schools:** get approval from the school administration and written consent (from a parent or guardian for students under 18) before enrolling anyone. Check the privacy laws that apply where you are (e.g. Data Privacy Act, GDPR, COPPA/FERPA, BIPA). Recognition can make mistakes, so attendance should be confirmable by a teacher and never used alone for discipline or grading.

## Credits
- Face detection and recognition: [Human](https://github.com/vladmandic/human) by Vladimir Mandic, MIT license (see `vendor/human/LICENSE`).
