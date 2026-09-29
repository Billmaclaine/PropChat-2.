# PropChat — Build the APK from an Android phone

This project is prepared so GitHub Actions can compile the Python/Kivy Android app for you. You do **not** need a computer.

## 1. Download and extract this project

Download the ZIP, then extract it with your Android file manager.

## 2. Create the GitHub repository

Open GitHub in your Android browser and sign in.

Create a new repository named `propchat`.

For the simplest free setup, make the repository **Public**. GitHub currently provides free and unlimited standard hosted runners for public repositories.

## 3. Upload the project files

Open the new repository and choose **Add file → Upload files**.

Upload the **contents** of the extracted `PropChat-v1.1-integrated` folder, not the ZIP file itself.

Make sure GitHub shows these paths at the repository root:

- `.github/workflows/android-apk.yml`
- `buildozer.spec`
- `propchat/main.py`
- `propchat/requirements.txt`
- `server/main.py`
- `server/requirements.txt`

Commit the files to the `main` branch.

## 4. Start the build

The workflow starts automatically after the commit.

You can also open **Actions → Build PropChat Android APK → Run workflow** to start it manually.

Wait for the job to finish. The first Buildozer Android build can take a while because Android build dependencies are downloaded.

## 5. Download the APK

Open the completed workflow run. Scroll to **Artifacts** and tap:

`PropChat-Android-APK`

GitHub will download a ZIP containing the APK. Extract that ZIP and tap the `.apk` file to install it on Android.

## Important

This workflow builds the Android client. The current project still expects the PropChat FastAPI backend at the API address configured in `propchat/main.py`. An APK can therefore install and launch without a deployed backend, but live account login, messaging, status, media and call signaling require the backend to be reachable from the phone.

The next deployment step is to put the `server/` backend on a public HTTPS host and change the app's API URL from the local `127.0.0.1` default to that HTTPS address.
