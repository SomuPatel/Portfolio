# Soumya Kumar Patel — Professional Portfolio

Static, responsive portfolio for GitHub Pages. `index.html` includes public profile data and Firebase web config. No admin password is stored in the code.

## GitHub Pages
Upload `index.html`, `profile-photo.jpg` and `profile-backup.json` to the repository root. Enable Settings → Pages → Deploy from a branch → `main` → `/(root)`.

## Firebase admin setup
1. In Firebase Authentication, enable Email/Password and create `somu893@portfolio-admin.com` with a new strong password. The website's username label is `Somu893`.
2. In Firestore, publish `firestore.rules`. It grants writes only to UID `L64S5OtxB5QveZw822UQAIQw1b42`.
3. This page reads and writes the Firestore document `profiles/main`.
4. In Authentication → Settings → Authorized domains, add your GitHub Pages hostname (e.g. `somupatel.github.io`).

Firebase web configuration is public; security comes from Authentication and Rules. If login fails, verify that the Authentication user email matches exactly and Email/Password provider is enabled.
