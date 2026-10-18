# Lumora

## Folders
- `public/` : the website (Netlify publishes this folder)
  - `index.html` : main app (new design + animated logo + Firebase login)
  - `clips.json` : list of clips (27 clips with posters for now)
  - `posters/` : poster images
  - `stats.json` : download counts shown on cards (edit by hand)
  - `ads.json` : optional extra ads (leave as []; use admin.html to upload ads)
  - icons: favicon.ico, favicon-32.png, apple-touch-icon.png, logo.png
- `firestore.rules`, `storage.rules`, `firebase.json`, `.firebaserc` : Firebase
- `cors.json` : CORS for Storage downloads
- `netlify.toml` : Netlify settings (publish folder = public)
- `design/logos/` : logo options
- `archive/` : older or alternate versions

## Publish
1. Upload everything in this folder to a GitHub repository.
2. Netlify: Add new site > Import from Git > pick the repo.
3. Firebase Console > Authentication > Settings > Authorized domains: add your Netlify domain.
4. Firebase Console > Authentication > Sign-in method: Google must be enabled.
5. Rules: paste firestore.rules in Firestore > Rules, and storage.rules in Storage > Rules, then Publish.

## Adding clips
Sign in on the site with akr.rabbi0@gmail.com. Your email shows on the button at the top right; open it and choose "Upload & manage" (or go to your-site/admin.html).
Videos tab: drop a video, type a title, press Upload clip. A poster is taken from the video automatically (or choose your own). The clip appears on the site right away, no code editing.
The same tab lists every clip, shows which ones have no video yet, and lets you attach a video to the 27 older clips ("Upload video").
Optional, so Download saves directly: `gsutil cors set cors.json gs://lomura-fde61.firebasestorage.app`

## Ads
In admin.html > "Upload as ad": choose a video or image, name, optional link, and how many times it may be shown.
All running ads are mixed and one is picked at random before a clip (the first clip of a visit has no ad). Skip appears after 5 seconds.
When an ad reaches its limit it stops automatically. You can pause, change the limit, or delete it in the "Your ads" list.
After updating, publish BOTH rules again: firestore.rules (Firestore > Rules) and storage.rules (Storage > Rules).
