# Green Sparrow: Firebase setup

`firebase-config.js` already points at project **green-sparrow-bec1e**. These steps are the same for any project; do the ones you haven't done yet.

1. Firebase Console > Build > **Firestore Database** > Create database > Production mode > region `asia-south1 (Mumbai)`.
2. Build > **Authentication** > Get started > Sign-in method > enable **Email/Password**.
3. Authentication > Users > **Add user** (your admin email + password). Copy that user's **UID**.
4. Firestore > Start collection `admins` > Document ID = the UID from step 3 > add field `role` (string) = `admin`.
5. Firestore > **Rules** tab > paste everything from `firestore.rules` > Publish.
6. Authentication > Settings > **Authorized domains** > add your live domain (e.g. greensparrow.in).
7. Upload the whole folder to your hosting (admin pages must stay in `/admin/`, next to `firebase-config.js` one level up).
8. Test: submit a form on the website, open `/admin/login.html`, sign in, and watch it appear live.

## If something doesn't work
- Sign in, then open **Connection check** (bottom of the dashboard sidebar). It shows which step is missing.
- Login says "not an admin yet": the page shows your UID; create the `admins/<UID>` document (step 4).
- "permission-denied" banner: publish `firestore.rules` (step 5).
- "unauthorized-domain": add the domain (step 6).
- Don't open the pages by double-clicking the file; Firebase Auth needs http(s).
