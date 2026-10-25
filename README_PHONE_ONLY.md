# Pantry Pal PWA — phone-only publishing guide

## What's in this project
- Recipe browser and search, ingredient scaling, cooking steps, favorites
- Shopping list with manual entries and check-off
- Estimated ingredient prices in Hungarian forints (editable starter estimates, not live retailer prices)
- Weekly budget limit, purchase records, weekly spend/remaining calculations
- LocalStorage persistence and service-worker offline cache
- PWA manifest and installable home-screen experience

## Publish from Android only (GitHub Pages route)
A hosted HTTPS URL is required for service workers and reliable PWA installation. This project is not published yet; the following steps use your phone's browser.

1. Download and extract the project ZIP using an Android file manager that can extract ZIP files.
2. Create or sign in to a GitHub account at https://github.com.
3. In GitHub, create a new **public** repository named `pantry-pal` (or another name you prefer).
4. Upload the files from this folder to the repository root. Use GitHub's website on your phone; if uploading a folder is awkward, upload files in small batches, ensuring `index.html`, `manifest.webmanifest`, `sw.js`, and both icons end up in the repository root.
5. In the repository, open **Settings → Pages**. Choose **Deploy from a branch**, select `main` and `/(root)`, then save.
6. Wait for GitHub Pages to publish. Your app URL will look like `https://YOUR-USERNAME.github.io/pantry-pal/` (replace with your actual username/repository).
7. Open that URL in Chrome on Android. Wait until it loads once while online.
8. In Chrome, tap **⋮ → Add to Home screen** or **Install app**.

## Updating later
Edit the files in the GitHub repository using GitHub's website on your phone and commit changes. Pages will republish the app. The service worker cache is versioned (`pantry-pal-v2`); when shipping a new app version, increment the cache name in `sw.js` (for example `pantry-pal-v3`) so installed clients refresh assets. Existing user data is in browser localStorage and is not cleared by ordinary app code updates. Avoid changing the app's origin/repository path after installation, because browser storage is scoped to the origin.

## Important limitations
- Estimated prices are approximate example values. No live grocery-price feed is connected; adjust the prices to your local store.
- Data is stored on this device/browser. Clearing browser storage or removing site data can delete it. This is not cloud-synced across devices.
- Offline use starts only after the app is hosted securely and has loaded online at least once.
- A public GitHub Pages repository makes source files visible to anyone. Do not store secrets or private information in this project.
