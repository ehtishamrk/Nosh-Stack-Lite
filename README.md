# Gristo Lite — Deployment Guide
**Admin Panel + POS Terminal | Pakistan Local Market**

---

## Files
| File | Purpose |
|------|---------|
| `admin.html` | Admin panel — open in any browser |
| `pos.html` | POS terminal — cashier app |
| `sw.js` | Service worker (offline support) |
| `manifest-admin.json` | PWA manifest for admin |
| `manifest-pos.json` | PWA manifest for POS |
| `firestore.rules` | Paste into Firebase → Firestore → Rules |

---

## Deploy a New Client (30 minutes)

### Step 1 — Create Firebase Project
1. Go to console.firebase.google.com
2. Click "Add project" → name it `gristo-[clientname]`
3. Enable **Firestore Database** (start in production mode)
4. Enable **Authentication** → Sign-in method → Email/Password → Enable
5. Go to Project Settings → Your apps → Add web app
6. Copy the `firebaseConfig` object

### Step 2 — Set Firestore Rules
1. Firebase Console → Firestore → Rules tab
2. Delete existing rules, paste contents of `firestore.rules`
3. Click Publish

### Step 3 — Deploy to GitHub Pages
1. Fork this repo on GitHub: `github.com/yourname/gristo-lite`
2. Rename fork to `gristo-[clientname]`
3. Go to repo Settings → Pages → Source: main branch → Save
4. Site is live at: `https://yourname.github.io/gristo-[clientname]/`

### Step 4 — First-Time Admin Setup
1. Open `https://yourname.github.io/gristo-[clientname]/admin.html`
2. You'll see "First time? Create restaurant →"
3. Paste the Firebase config when prompted
4. Fill restaurant name, owner email, password
5. Click "Create Restaurant"

### Step 5 — Configure & Add Products
1. Go to Settings → add logo, brand color, tagline
2. Go to Settings → POS Settings → set PIN length, enable delivery/card
3. Go to Categories → add categories (e.g. Burgers, Drinks, Deals)
4. Go to Products → add menu items with photos and prices
5. Go to Cashiers & PINs → add cashier accounts with PINs

### Step 6 — Set Up POS
1. Open `https://yourname.github.io/gristo-[clientname]/pos.html` on cashier device
2. First time: paste the Firebase config
3. Cashier enters their PIN → ready to take orders

---

## Installing as App (No APK Needed)

### Android (Chrome)
1. Open `pos.html` URL in Chrome
2. Tap menu (⋮) → "Add to Home screen"
3. Tap "Install" → appears as app icon on home screen
4. Opens fullscreen, works offline ✓

### Windows (PC POS)
1. Open `pos.html` in Chrome or Edge
2. Click install icon in address bar (or menu → Install Gristo POS)
3. Opens as standalone window, no browser bar ✓

### iOS (Safari)
1. Open `pos.html` in Safari
2. Tap Share → "Add to Home Screen"
3. Tap Add ✓

---

## Offline Operation
- POS works fully offline after first load
- Orders taken offline are saved locally
- When internet returns, orders auto-sync to Firebase
- Offline orders tagged as `pos_offline` in admin panel
- Menu updates from admin reflect on next POS reload

---

## Updating All Clients
Push a change to your GitHub repo → GitHub Pages auto-deploys → all clients get update on next page load. **No reinstall. No APK. Nothing.**

---

## Pricing Suggestion (Pakistan Market)
| Plan | Price | Includes |
|------|-------|---------|
| Basic | Rs 3,000/month | Admin + POS, up to 2 cashiers |
| Standard | Rs 5,000/month | Admin + POS, unlimited cashiers, inventory |
| Premium | Rs 7,000/month | Everything + priority support + custom domain |

---

## Support Checklist (New Client)
- [ ] Firebase project created
- [ ] Firestore rules published
- [ ] GitHub repo forked and Pages enabled
- [ ] Admin account created
- [ ] Restaurant name, logo, colors set
- [ ] Categories added
- [ ] Products added with photos and prices
- [ ] Cashier PINs set up
- [ ] POS tested on cashier device
- [ ] First test order placed and visible in admin
