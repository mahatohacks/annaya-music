# Annaya Music App

Android 13+ (minimum SDK 33) music player with an offline library, local playlists, YouTube search, shared catalog playback, offline downloads, an admin sign-in/upload screen, and a deployable catalog server.

## Project contents

- `app/` — native Android app.
- `server/` — Node.js API and Docker deployment.
- `render.yaml` — Render Blueprint for an HTTPS server with persistent song storage.
- `DEPLOY_RENDER.md` — step-by-step server setup.

## Build

Open this folder in Android Studio, allow Gradle to sync, then choose **Build > Build Bundle(s) / APK(s) > Build APK(s)**. The project targets API 35 and uses Android Gradle Plugin 8.7.3. Android SDK license terms must be accepted in Android Studio/SDK Manager before the build.

## Connect phones to the shared library

Deploy `render.yaml` from the repository root using the steps in `DEPLOY_RENDER.md`. The Render service address is created during deployment. Enter its HTTPS origin in the app's Online tab, then sign in from Admin to upload songs. Shared features work after the server is deployed and reachable. Local offline music and playlists work without a server.

The app starts empty. Choose MP3/AAC songs from the device to play offline. The admin can upload licensed audio to the shared server. YouTube searches open the official YouTube app or site; this app does not download YouTube audio.
