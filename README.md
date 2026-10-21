# Soumya Kumar Patel — Professional Digital Profile

A responsive, single-page professional portfolio built with HTML, CSS and vanilla JavaScript. It is designed for GitHub Pages and includes a secure-by-design admin workflow using Firebase Authentication + Cloud Firestore.

## What's included

- `index.html` — portfolio website, responsive layout, experience timeline, skills, education, contact buttons, share link and print/save-as-PDF button.
- `assets/profile-photo.jpg` — cropped profile photo taken from the supplied profile screenshot.
- `firestore.rules` — Firestore rules: public visitors can read the profile; only the dedicated admin email can write it.
- `profile-backup.json` — editable backup of the starter profile data.

## Important admin security note

The admin ID shown by the login screen is `Somu893`. The password is **not** embedded, hidden, encoded or obfuscated in the website source. Anything placed in a GitHub Pages HTML/JavaScript file can be inspected by visitors, so hard-coding a password there is not secure.

The login password must be created and checked by Firebase Authentication. Because the password shared in the setup request has been exposed in chat and is short, use a new, unique password in Firebase rather than reusing it. The password stays in Firebase Authentication and is entered in the login screen only when signing in.

The admin login maps the username `Somu893` to this Firebase Authentication email: `somu893@portfolio-admin.com`. Do not create a sign-up page for visitors. Create this account yourself in the Firebase Console only.

## 1. Create the Firebase project

1. Open the Firebase Console: <https://console.firebase.google.com/> and create a project.
2. In Project settings → General, add a **Web app** and copy its Firebase configuration.
3. In Authentication → Sign-in method, enable **Email/Password**.
4. In Authentication → Users, choose **Add user**. Use the email `somu893@portfolio-admin.com` and set a new strong, unique password. Store that password in a password manager. It is not necessary for this email address to receive messages if you do not turn on email verification.
5. In Firestore Database, create a database. The profile can be stored in any supported region.
6. Open Firestore → Rules and paste the contents of `firestore.rules`, then Publish. This allows public profile reads but limits writes to the dedicated admin account email.
7. Open `index.html` in an editor. Find `const firebaseConfig = { ... }` near the bottom and replace all `YOUR_...` placeholders with the Web app's configuration values. Keep the property names and quotes as they are. Firebase's web config is a public client identifier, not an admin password; database access is protected by Authentication and Firestore Rules.

The site expects the Firestore document path `profiles/main`. You do **not** need to create the document manually. The first successful admin save creates it.

## 2. Test before publishing

1. Save the edited `index.html`.
2. Open it using a small local web server (recommended) or deploy it to GitHub Pages; Firebase Authentication is more reliable over `http://localhost`/HTTPS than opening the file directly with `file://`.
3. Click **Admin access** in the footer. Enter ID `Somu893` and the password you created for the Firebase Authentication user.
4. Update fields in the tabs. Experience, education and community focus lists are edited as JSON arrays. Use **Backup / JSON** to export a complete backup or import an earlier one.
5. Click **Save changes**. The public profile reads `profiles/main` from Firestore, so visitors to your deployed URL will see the published version.

If sign-in works but saving fails, recheck the Firestore Rules and verify the account's email is exactly `somu893@portfolio-admin.com`.

## 3. Publish on GitHub Pages

1. Create a new GitHub repository, for example `soumyapatel-portfolio`.
2. Upload `index.html`, `firestore.rules`, `profile-backup.json`, `README.md` and the `assets` folder (including `profile-photo.jpg`). Keep the file paths the same.
3. In the repository, open **Settings → Pages**.
4. Under **Build and deployment**, choose **Deploy from a branch**, select the `main` branch and `/ (root)`, then Save.
5. Wait for GitHub Pages to publish your site. Your public URL will look like `https://YOUR-GITHUB-USERNAME.github.io/soumyapatel-portfolio/`.
6. Open the published HTTPS URL on your phone, test each section, test sharing, and test the admin login / save. Share the public URL with recruiters or contacts.

## Editing and backups

For ordinary content updates, use **Admin access** → edit the relevant tab → **Save changes**. For arrays in the Experience, Education and Focus tabs, preserve valid JSON syntax. Download a backup before making major edits. You can also edit `profile-backup.json` and import it in the admin panel.

The image can be replaced by uploading a new image at `assets/profile-photo.jpg` (keep the same name) or by entering an HTTPS image URL in the admin panel. A relative path such as `assets/profile-photo.jpg` works when the file is inside this repository.

## Data privacy

This is a public professional profile, so the name, work history, education, phone and email entered here are visible to visitors. Remove any detail you do not want to publish. The Firestore document is publicly readable by design; only its writes are restricted. Do not store identity documents, passwords or confidential company records here.
