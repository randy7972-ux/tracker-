# MHT-CET Planner — Android PWA

This package turns the supplied planner into an installable, offline-capable Progressive Web App. The original test schedule, calendar, timeline, styling and embedded syllabus image are preserved.

## Deploy (free option: Vercel)

1. Extract this ZIP on your computer.
2. Open https://vercel.com/ and sign in.
3. Choose **Add New → Project** and import a Git repository containing these files, or use Vercel CLI to deploy this folder.
4. Use the project root as the site root. No build command or framework preset is needed; this is a static site.
5. Once deployed, open the HTTPS URL on your Android phone in Chrome.

## Install on Android

1. Visit the deployed HTTPS website in Chrome while online.
2. Wait for the first page load to finish.
3. Tap **Install app** on the planner if the button appears, or open Chrome's ⋮ menu and choose **Install app** / **Add to Home screen**.
4. Launch **CET Planner** from your app drawer or home screen. It opens as an app without Chrome's address bar.
5. After the first successful load and service-worker installation, the planner shell is cached and can open offline. For best results, open it once online after installation before going offline.

## Offline behaviour and limitations

- The planner HTML, manifest and icons are cached. The syllabus preview image is embedded directly in the HTML, so it is available offline too.
- Offline use works after the first successful online visit; a first-ever visit cannot work without a connection.
- Use HTTPS hosting (Vercel provides it). Service workers do not work from a `file://` URL or ordinary unencrypted HTTP. `localhost` is an exception for local testing.
- To publish an updated version later, replace the files and change `CACHE_NAME` in `sw.js` (for example, `mht-cet-planner-v2`) so devices refresh the offline cache.
- Android/Chrome decides whether to show the native install prompt. The manifest requests fullscreen first, with standalone as fallback; exact system-bar behaviour can vary by Android version.

## Files

- `index.html` — planner interface and original schedule
- `manifest.webmanifest` — app name, icons, launch mode and scope
- `sw.js` — offline caching and update handling
- `icons/` — app icons
