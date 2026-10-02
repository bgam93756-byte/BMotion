# Butterscotch Clicker

A candy-shop clicker game in one HTML file, with Google sign-in, cloud saves and a public leaderboard powered by Firebase.

Without Firebase set up, the game still works in guest mode and saves progress on the device.

## Files

| File | What it is |
|---|---|
| `index.html` | The whole game |
| `firebase-config.js` | Your Firebase project's web config (fill this in) |
| `firestore.rules` | Database security rules (paste into Firebase) |
| `firebase.json` | Only needed if you deploy with the Firebase CLI |

## Set up Firebase (about 10 minutes, works from a phone browser)

1. Go to <https://console.firebase.google.com>, tap **Create a project**, give it a name, and finish the steps. Google Analytics is optional.
2. **Add a web app:** on the project home, tap the **</>** (Web) icon, name it, and register it. Copy the `firebaseConfig` values it shows into `firebase-config.js`.
3. **Turn on Google sign-in:** **Build → Authentication → Get started → Sign-in method → Google → Enable**, pick a support email, and save.
4. **Create the database:** **Build → Firestore Database → Create database**, pick a location, and choose **production mode**.
5. **Add the security rules:** in Firestore, open the **Rules** tab, replace everything with the contents of `firestore.rules`, and tap **Publish**.
6. **Allow your website:** **Authentication → Settings → Authorized domains → Add domain**, and add the domain the game is hosted on, for example `bgam93756-byte.github.io`.

## Host it on GitHub Pages (free)

1. Merge this folder into the `main` branch.
2. In the repo on GitHub: **Settings → Pages → Build and deployment → Source: GitHub Actions**.
3. The workflow `.github/workflows/butterscotch-pages.yml` deploys the game on every push to `main` that changes this folder. You can also run it from the **Actions** tab.
4. The game will be at `https://bgam93756-byte.github.io/BMotion/`.

## What gets stored

- `saves/{uid}`: each player's full save. Only that player can read or write it.
- `leaderboard/{uid}`: name, Google profile photo, butterscotch made, per-second rate, crowns and trophies. Anyone can read it; each player can only write their own row.

The game runs on the player's device, so a determined player could still edit their own score. The rules stop anyone from writing someone else's row or posting malformed data.
