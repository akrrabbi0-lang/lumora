# Lumora

## Folders
- `public/` : the website (Netlify publishes this folder)
- `firestore.rules`, `storage.rules`, `firebase.json`, `.firebaserc` : Firebase settings
- `netlify.toml` : Netlify settings (publish folder = public)
- `design/logos/` : logo options
- `archive/` : older versions

## Publish
1. Upload this folder to a GitHub repository.
2. Netlify: Add new site > Import from Git > pick the repo. Publish directory is read from netlify.toml.
3. Firebase Console > Authentication > Settings > Authorized domains: add your Netlify domain.
4. Deploy the rules once: `firebase deploy --only firestore:rules,storage`

## Adding a clip
Upload the video and poster in Firebase Console > Storage > folder `clips` (not to GitHub). Then add to `public/clips.json`:

    [{"id":"c1","title":"My clip","file":"c1.mp4","poster":"c1.jpg"}]

## One-time: CORS for downloads
Run once (Google Cloud SDK): `gsutil cors set cors.json gs://lomura-fde61.firebasestorage.app`
Without it the Download button opens the video in a new tab instead of saving it.
