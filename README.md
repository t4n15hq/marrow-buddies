# Marrow Buddies: setup (about 15 minutes, free)

Your friends sign in with Google, so they don't need a Claude account. A squad code keeps strangers out.

## 1. Create a Firebase project
1. Go to https://console.firebase.google.com, click **Create a project**, and give it a name (e.g. `marrow-buddies`). You can turn Google Analytics off.
2. Click **Build → Authentication → Get started → Google**, then **Enable** and **Save**.
3. Click **Build → Firestore Database → Create database**. Pick a location near your squad (e.g. `asia-south1` for India) and start in **production mode**.
4. Go to **Project settings (gear icon) → Your apps → Web (</>)** and register an app. Copy the `firebaseConfig` values.

## 2. Plug in your config and squad code
- In `index.html`, paste the config values into `FIREBASE_CONFIG` near the top of the main script.
- In `firestore.rules`, change `CHANGE_ME_pinkmarrow` to your own squad code. Share the code only with your friends.

## 3a. Host on GitHub Pages (no command line needed)
1. Create a new public repo on GitHub (e.g. `marrow-buddies`) and upload `index.html` with **Add file → Upload files**.
2. Go to repo **Settings → Pages**. Set Source to **Deploy from a branch**, choose branch `main` and folder `/ (root)`, then **Save**. After a minute your site is at `https://<your-username>.github.io/marrow-buddies/`.
3. In Firebase: **Authentication → Settings → Authorized domains → Add domain** → `<your-username>.github.io`.
4. In Firebase: **Firestore Database → Rules**. Paste in the contents of `firestore.rules` (with your squad code) and click **Publish**.

## 3b. Or deploy with the Firebase CLI instead (the Spark plan is free)
```bash
npm install -g firebase-tools
firebase login
cd marrow-buddies-standalone
firebase use --add            # pick your project
firebase deploy --only firestore:rules,hosting
```
You'll get a link like `https://marrow-buddies.web.app`. Send it to your friends.

Hosting somewhere else (Netlify, GitHub Pages)? Add that domain under **Authentication → Settings → Authorized domains**, and still run `firebase deploy --only firestore:rules`.

## 4. Join
Each person opens the link and taps **Sign in with Google**, then **Join the squad**. They enter the squad code and pick a mascot and a daily goal.

## Notes
- A day counts toward a streak when at least one video is logged. Squad streak = days on which everyone who had joined logged one.
- Everyone in the squad can see all logs. Only you can change your own.
- To change the squad code later, edit `firestore.rules` and redeploy. Existing members stay in, but they need the new code to edit their buddy card.
- To remove someone: Firestore console → `members` → delete their document.
