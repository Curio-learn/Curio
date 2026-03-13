# Deploying Curio to Netlify

## What's in this folder
- index.html   — the app
- manifest.json — PWA configuration
- sw.js         — service worker (offline support)
- icon-192.png  — app icon (Android / PWA)
- icon-512.png  — app icon (large)
- apple-touch-icon.png — app icon (iPhone home screen)

---

## Step 1 — Create a free Netlify account
Go to https://netlify.com and sign up (free tier is plenty).

---

## Step 2 — Deploy the folder (drag and drop — no coding required)

1. Log in to Netlify
2. Go to the "Sites" tab
3. Drag the entire **curio-pwa** folder into the drag-and-drop area
   (it says "drag and drop your site folder here")
4. Netlify will give you a URL like: https://quirky-name-123456.netlify.app
5. Done — the app is live.

To give it a nicer URL, go to Site Settings → Domain Management → Change site name.
Example: https://curio-learn.netlify.app

---

## Step 3 — Share the link with friends (iPhone instructions)

Send your friends this message:

> "Open [your-url] in Safari on your iPhone.
> Tap the Share button (the box with an arrow at the bottom of the screen).
> Tap 'Add to Home Screen'.
> Tap 'Add'.
> Curio will appear on your home screen like a normal app."

**Important:** It must be opened in Safari (not Chrome) for the
Add to Home Screen option to install it properly as a PWA on iPhone.

---

## Step 4 — Updating the app later

If you make changes to the HTML:
1. Drag the updated folder onto your Netlify site dashboard again
2. Netlify will deploy the new version in seconds
3. Your friends' apps will update automatically next time they open it
   with an internet connection

---

## Offline behaviour

The app caches itself on first load. After that:
- The app shell always works offline
- Previously loaded Wikipedia cards are cached and may show offline
- New cards require an internet connection

---

## Optional: custom domain

If you own a domain (e.g. curio.yourdomain.com):
1. Netlify → Site Settings → Domain Management → Add custom domain
2. Follow the DNS instructions — takes about 10 minutes to go live
3. Netlify provides free HTTPS automatically (required for PWA)

---

## Troubleshooting

**"Add to Home Screen" doesn't appear on iPhone**
→ Make sure they're using Safari, not Chrome or Firefox

**App doesn't update after you deploy a new version**
→ The user can force-refresh by closing the app fully and reopening
→ Or you can bump the cache name in sw.js from 'curio-v1' to 'curio-v2'
   to force all clients to update on next load

**Wikipedia cards not loading**
→ This requires an internet connection — the service worker caches
   previously seen articles but can't fetch new ones offline
