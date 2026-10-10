# LinkUp — Real-time username chat (CIT assignment)

A starter web messaging app built with HTML, CSS, JavaScript, Firebase Authentication (anonymous sign-in), and Cloud Firestore.

## Features
- Username-only onboarding; no phone number
- Unique usernames
- Add a friend by username
- Real-time one-to-one text messages across devices
- Responsive green-and-white interface
- Firestore rules to restrict chat reads and message sends to chat participants

## Important limitations
- This starter uses anonymous Firebase accounts. The browser remembers the current account, but there is no password-based account recovery. Clearing browser data or switching browser/device can mean losing access to that username. Do not use it for sensitive/private real-world conversations.
- Internet is required for real-time chat.
- It is a learning project, not a production-ready messenger. Add a proper sign-in/recovery method, abuse protection, rate limits, reporting/blocking, and a privacy notice before public use.
- Do not copy WhatsApp's logo or claim LinkUp is affiliated with WhatsApp. LinkUp uses its own branding.

## Step 1 — Create a Firebase project
1. Open https://console.firebase.google.com/ and create a project named `LinkUp`.
2. In the project, add a **Web app** (the `</>` icon).
3. Copy the Firebase web configuration.

## Step 2 — Turn on anonymous authentication
1. In Firebase Console, open **Build → Authentication**.
2. Choose **Get started** if shown.
3. Open **Sign-in method**.
4. Enable **Anonymous**, then save.

## Step 3 — Create Firestore
1. Open **Build → Firestore Database**.
2. Create a database. For a class demo, choose a location near your region if available.
3. Open the **Rules** tab.
4. Replace the rules with the contents of `firestore.rules`.
5. Click **Publish**.

Do not leave Firestore in test mode for this project.

## Step 4 — Add your Firebase configuration
1. Open `index.html` in VS Code.
2. Find `const firebaseConfig = {`.
3. Replace all `PASTE_...` values with the config from your Firebase web app.
4. Save the file. Keep the keys in the config exactly as Firebase gave them.

Firebase web config values identify the project; security is enforced by Authentication and Firestore rules. Never put service-account/private admin keys in browser code.

## Step 5 — Run the website
Recommended: use the VS Code **Live Server** extension:
1. Open the LinkUp folder in VS Code.
2. Right-click `index.html`.
3. Select **Open with Live Server**.
4. The site should open in your browser.

You can also use another local web server. Avoid opening as a `file://` URL if module imports are blocked.

## Step 6 — Test with two users/devices
1. On device/browser A, open LinkUp and register a username, e.g. `sara_22`.
2. On device/browser B (or a different browser profile), open the same deployed/local-hosted site and register another username, e.g. `hamza_17`.
3. On device A, type `hamza_17` in “Find by username…” and click Add.
4. Send a message. It should appear on device B in real time.
5. On device B, the conversation appears in the chat list; open it and reply.

For two physical devices, both need to open a hosted version of the site or a network-accessible dev server, and both need internet access. `localhost` on one device does not automatically mean the other device can access it.

## Troubleshooting
- **“Setup needed”**: Firebase config has not been replaced or includes a `PASTE_` placeholder.
- **auth/operation-not-allowed**: Enable Anonymous sign-in in Firebase Authentication.
- **permission-denied**: Publish the provided Firestore rules and check that Anonymous sign-in is enabled.
- **Username not found**: Both users must register in LinkUp first; then enter the exact username.
- **Two devices cannot open the site**: Deploy it (for example, Firebase Hosting) or use a network-accessible server URL; don't use `localhost` from the second device.

## How to explain this to your teacher
“LinkUp is a responsive real-time messaging web app. HTML defines the structure, CSS creates the interface, JavaScript handles user interaction, Firebase Authentication provides anonymous identities, and Cloud Firestore stores usernames and synchronizes messages in real time. Users can find each other using unique usernames without providing phone numbers.”

## Suggested next improvements
- User profile display names and avatars
- Unread message indicators
- Last-message previews
- Password/email account recovery
- Blocking and reporting
- Progressive Web App install support
