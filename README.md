# LeaderLog PWA — Setup Guide for Lakshman

## Step 1: Host on GitHub Pages (free, 5 minutes)

1. Go to github.com and create a free account (or log into yours)
2. Click **New repository** → Name it `leaderlog` → Set to **Public** → Create
3. Upload ALL files from this folder:
   - index.html
   - manifest.json
   - sw.js
   - icon-192.png
   - icon-512.png
4. Go to **Settings** → **Pages** → Source: **Deploy from branch** → Branch: **main** → Save
5. Your app URL will be: `https://YOUR-USERNAME.github.io/leaderlog`

## Step 2: Firebase Setup (real-time sync)

1. Go to console.firebase.google.com
2. Add project → Name: `leaderlog` → Disable Analytics → Create
3. Click **Web icon </>** → Register app as `leaderlog` → Copy the firebaseConfig object
4. Build → **Firestore Database** → Create database → Production mode → Region: **asia-south1 (Mumbai)**
5. Build → **Authentication** → Get started → Enable **Google** sign-in
6. Firestore → **Rules** tab → Replace rules with:
```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /users/{userId}/{document=**} {
      allow read, write: if request.auth != null && request.auth.uid == userId;
    }
  }
}
```
7. Publish rules

## Step 3: Install on each device

### Android Phone
1. Open Chrome → go to your GitHub Pages URL
2. When prompted "Add to home screen" → tap Add
3. OR: tap ⋮ menu → "Add to Home screen"

### Windows Laptop
1. Open Chrome → go to your URL  
2. Click the install icon (⊕) in the address bar
3. OR: ⋮ menu → "Install Leadership Journal..."

### iPad
1. Open Safari → go to your URL
2. Tap Share button → "Add to Home Screen" → Add

## First Launch
1. Open the app → you'll see the Firebase config screen
2. Paste your firebaseConfig JSON
3. Click "Save Config & Launch"
4. Sign in with Google
5. All your data now syncs across devices in real-time!

## Your app URL
`https://YOUR-GITHUB-USERNAME.github.io/leaderlog`

Save this URL — share it to all your devices.
