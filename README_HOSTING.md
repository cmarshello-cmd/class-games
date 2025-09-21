# Firebase Hosting — One Site, Many Pages

This folder is ready to deploy to **Firebase Hosting**. It contains:
- `index.html` (landing page with links)
- `games/truth-or-date/index.html` (your latest deck)
- `games/writeround/Teacher.html` and `Student.html`
- `firebase.json` (hosting config)
- `firestore.rules` (starter Firestore rules)

## Deploy steps

1) Install CLI
```
npm i -g firebase-tools
firebase login
```

2) Create/choose your Firebase project in the console.

3) Initialize (in this folder)
```
firebase init hosting
# ✓ Use an existing project → select your project
# ? What do you want to use as your public directory?  .
# ? Configure as a single-page app (rewrite all urls to /index.html)?  No
# ? Set up automatic builds and deploys with GitHub?  No (you can later)
```

4) Paste your Firebase config into both **WriteRound** HTML files:
Search for `const firebaseConfig = { ... }` and replace placeholders.

5) Enable **Authentication → Anonymous** and **Firestore** in the Firebase console.
   - In **Auth → Settings → Authorized domains**, add your Hosting domain (e.g., `<project-id>.web.app`).

6) (Optional) Set Firestore rules:
Open `firestore.rules` and adjust as needed, then:
```
firebase deploy --only firestore:rules
```

7) Deploy Hosting
```
firebase deploy --only hosting
```
Your site goes live at `https://<project-id>.web.app`.

## Add more games
Create more folders in `/games/<your-game>/` and add an `index.html`. Link them from `index.html`.

## Troubleshooting
- If auth fails in class: ensure your Hosting domain is in **Authorized domains**.
- School networks: allowlist `*.firebaseio.com`, `*.googleapis.com`, and your site domain.
