# Avni Chat — Stitch UI pack

## What is included
- `index.html`: screen launcher, with links to all 20 designs.
- `screens/`: the 20 original Stitch `code.html` screens, copied without redesigning them.
- `assets/`: available screen preview images from the ZIP.
- `firebase-config.example.js`: safe client-side config template (placeholders only).

## Preview
Open `index.html` in a browser. If a browser blocks local scripts or styles, upload the folder to a static host or run a local static server. The designs load Tailwind CSS and fonts from online CDNs.

## Important status
This is a design handoff, not a completed real-time chat application. The existing screens are independent HTML prototypes. The launcher does not claim that authentication or messages work. Firebase configuration has not been supplied, so no live Firebase project has been connected yet.

## Firebase next step
1. Create a Firebase project at https://console.firebase.google.com/
2. Add a Web app and copy its Web app config into a local config file.
3. Enable Authentication > Email/Password.
4. Create a Cloud Firestore database.
5. Add Firestore security rules so each user can access only permitted profile/conversation documents.
6. Implement and test signup/login/logout, profile creation with a unique Avni ID, conversation membership checks, real-time messages, and deployment.

Do not share your password or Firebase service-account/private admin key. The Firebase web config is intended for browser apps, but access must be protected with Authentication and Firestore Security Rules.


## Firebase config supplied
- Project ID: `avni-chat`
- Added `firebase-config.js` with the Web App config you supplied.
- Added `firebase-test.html` to test Email/Password signup, login, and logout.

## Test Firebase authentication
1. Open Firebase Console → Authentication → Sign-in method.
2. Enable **Email/Password** and press Save. Email link/passwordless sign-in is not needed for this flow.
3. Serve this folder using a static web host or local development server. ES module imports usually do not work by opening the HTML file directly as `file://`.
4. Open `firebase-test.html`, create an account with a test email/password, then log out and log in again.

## Important
This is an authentication test page, not yet the full real-time chat application. Firestore profile creation, unique Avni ID generation, chat rooms/messages, file uploads, security rules, and deployment still need to be implemented and tested. Do not use Firestore Test Mode for a public launch; configure restrictive Firestore Security Rules before adding real users.

## Next-step implementation added
- `chat.html`: functional Firebase email/password signup/login/logout, profile creation, unique Avni ID reservation, search/open one-to-one chats by Avni ID, and real-time Firestore messages.
- `firestore.rules`: starting security rules for profiles, Avni ID lookup, chats, and messages.

## Required setup before testing chat
1. Firebase Console → Firestore Database → Rules.
2. Copy the contents of `firestore.rules` into the Rules editor and Publish.
3. Confirm Authentication → Sign-in method → Email/Password is enabled.
4. Host this folder on an HTTPS static host (or run a local development server); don't open `chat.html` directly as a `file://` URL.
5. Open `chat.html` in two different accounts/devices. Create accounts, share Avni IDs, start chat, and send messages.

This is an initial one-to-one text chat, not a complete production launch. Test with non-sensitive accounts first. Before public launch, review and test the Firestore rules and add rate limits, abuse reporting/blocking, email verification, and moderation. Firebase web config is public client config, not an admin secret.
