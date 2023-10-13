# Repro for tools #6341

## Versions

fireabse-tools: v12.7.0<br>
firebase-js-sdk: v10.5.0<br>
node: v18.16.1

## Steps to reproduce

(Optional): In "public/configs.js", set `firebaseConfig` to your Firebase project's config. If not changed, a fake config using the project id of `demo-project` will be used.

### Emulator test

This works ("http://127.0.0.1:5000/"):

1. In "public/configs.js"
   - Set `useEmulator` to `true`
1. Run `firebase emulators:start --project <project_id>`
1. Open "http://127.0.0.1:5000" to access the hosted app
1. Click "SIGN IN WITH GOOGLE" button
   - This will automatically redirect to "Sign-in with Google.com"
   - Sign in as expected
1. Get redirected to "http://127.0.0.1:5000/"
   - Page will display user information
   - Console logs will also show `userCredentials`
   - Auth emulator console (http://127.0.0.1:4000/auth)
     - User is created

This does not work ("http://localhost:5000"):

1. In "public/configs.js"
   - Set `useEmulator` to `true`
1. Run `firebase emulators:start --project <project_id>`
1. Open "http://localhost:5000" to access the hosted app
1. Click "SIGN IN WITH GOOGLE" button
   - This will automatically redirect to "Sign-in with Google.com"
   - Sign in as expected
1. Get redirected to "http://localhost:5000"
   - Page will not display any user information
   - Console logs will also show `userCredentials` is `null`
   - Auth emulator console (http://127.0.0.1:4000/auth)
     - User is created

## Notes:

When connecting to an actual Firebase project(Set `useEmulator` to `false`), both "http://127.0.0.1:5000/" and "http://localhost:5000" works.
