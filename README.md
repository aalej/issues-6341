# Repro for tools #6341

## Versions

fireabse-tools: v12.5.3
firebase-js-sdk: v10.3.1
node: v18.16.1

## Steps to reproduce

Todo: In "public/configs.js", set `firebaseConfig` to your Firebase project's config

### Emulator test

1. In "public/configs.js"
   - Set `useEmulator` to `true`
1. Run `firebase emulators:start --project <project_id>`
1. Open "http://127.0.0.1:5000" to access the hosted app
1. Click "SIGN IN WITH GOOGLE" button
   - This will automatically redirect to "Sign-in with Google.com"
   - Sign in as expected
1. Get redirected to "http://127.0.0.1:5000/"
   - Page will display user information
   - Console logs will also show user credentials

### Firebase project test

1. In "public/configs.js"
   - Set `useEmulator` to `false`
1. Run `firebase emulators:start --only hosting --project <project_id>`
1. Open "http://127.0.0.1:5000" to access the hosted app
1. Click "SIGN IN WITH GOOGLE" button
   - This will automatically redirect to "Sign-in with Google.com"
   - Sign in as expected
1. Get redirected to "http://127.0.0.1:5000/"
   - Page will display user information
   - Console logs will also show user credentials