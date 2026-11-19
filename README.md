# Marrow Buddies

Daily Marrow PG video streaks, together. Live at https://t4n15hq.github.io/marrow-buddies/

## Using it
1. Open the link and tap **Sign in with Google**.
2. Tap **Create a squad**, give it a name, pick a mascot and a daily goal.
3. Tap **Invite buddies** and send the link. Anyone who opens it signs in and joins your squad.

Got a code instead of a link? Tap **Join with a code** and paste it (pasting the whole invite link works too).

To switch squads, tap your name at the top, then **Leave squad**. Your video logs are kept.

## Notes
- A day counts toward a streak when at least one video is logged. Squad streak = days on which everyone who had joined logged one.
- Everyone in a squad sees each other's logs. Only you can change yours. Other squads can't see anything.
- The invite code is the only key to a squad, so share the link only with people you want in it.

## For whoever maintains this
- `index.html` is the whole app. GitHub Pages serves it from the `main` branch.
- Data and sign-in live in the Firebase project `marrow-buddies-hj9ay` (Firestore + Google sign-in).
- After editing `firestore.rules`, publish it with `firebase deploy --only firestore:rules --project marrow-buddies-hj9ay`.
- Test locally with `firebase emulators:start --only auth,firestore,hosting --project marrow-buddies-hj9ay`, then open http://localhost:5005.
