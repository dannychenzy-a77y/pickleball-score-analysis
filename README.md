[README.md](https://github.com/user-attachments/files/25606702/README.md)
# 🏓 Pickleball Pro Tracker

A feature-rich Progressive Web App (PWA) for scoring pickleball matches, tracking player statistics, and running full tournaments — all from a single HTML file with no installation required.

---

## Live Demo

Deploy to Netlify by dragging the HTML file into your dashboard, or host on any static file server.

---

## Features

### 🏓 Match Scoring
- **Rally scoring** and **Side-Out (traditional) scoring** modes
- Singles and Doubles support
- Live scoreboard with animated score updates
- Undo last point
- Manual server switching
- Best of 1, 3, or 5 games
- Win score configurable (11, 15, or 21 points)

### 📋 Point Logging & Attribution
- Two-step point logging flow — tap to score, then optionally categorise and attribute
- **Winner Shot** categories: Forehand Winner, Backhand Winner, Service Winner, Lob Winner, Drop Shot Winner, Overhead Smash Winner, Volley Winner, Unreturnable Slice Winner, Return of Serve Winner
- **Opponent Error** categories: Forehand Error, Backhand Error, Return of Serve Error, Lob Error, Drop Error, Smash Error, Serve Error, Volley Error, Unforced Error, Kitchen Fault, Foot Fault, Net Error, Forced Error
- Per-player attribution — track which player hit the winner or made the error
- Live point log feed with colour-coded badges

### 📊 Statistics
- Match overview with points won breakdown
- Point quality rings (winner % vs error %)
- Per-player stats: Winners, Errors, Team Points, Serve Win %
- Best shot type and most common error per player
- Serve points won by team
- Full category breakdown with horizontal bar charts

### 🥇 Tournaments
- Create named tournaments (Singles or Doubles format)
- Add any number of players or teams during sign-up
- **Serpentine seeding** distributes players evenly across groups
- **Round Robin group stage** — every player plays everyone in their group
- Live standings table: W / L / Points / Points Difference
- Top 2 from each group automatically qualify (marked with **Q**)
- One-tap score entry for every fixture
- **Knockout bracket** auto-generates once all group games are played
- Cross-group seeding avoids same-group rematches in Quarter-Finals
- Full bracket: Quarter-Finals → Semi-Finals → **Final** + **3rd Place Play-Off**
- Bye management for non-power-of-2 bracket sizes
- Results propagate automatically through the bracket
- **Podium display** showing 🥇 🥈 🥉 and 4th place on completion

### 📁 Match History
- All completed matches saved to local storage
- Browse past matches with scores and player details

### ☁️ Firebase Cloud Sync *(optional)*
- Connect a free Firebase Firestore project to sync match history across devices
- Automatic background sync on save
- Merge local and remote history on reconnect

### 📤 CSV Export
- Export full point log with categories, player attribution, server info, and timestamps
- Includes per-player summary and category breakdown sections

### 📱 PWA — Installable on Any Device
- Works offline after first load
- Add to Home Screen on iOS (Safari) and Android (Chrome) for a native app feel
- Full-screen mode, no browser chrome

---

## Getting Started

### Option 1 — Open directly in a browser
Download `pickleball-pro-app.html` and open it in any modern browser. No server required.

### Option 2 — Deploy to Netlify (recommended)
1. Rename the file to `index.html`
2. Create a folder and place `index.html` inside it
3. Drag the folder into your [Netlify dashboard](https://app.netlify.com)
4. Your app is live instantly at a `*.netlify.app` URL

### Option 3 — GitHub Pages
1. Upload `index.html` to a GitHub repository
2. Go to **Settings → Pages**
3. Set source to **Deploy from a branch → main → / (root)**
4. Your app will be available at `https://YOUR-USERNAME.github.io/REPO-NAME`

---

## How to Use

### Starting a Match
1. Enter player names and team names on the **Home** screen
2. Choose **Rally** or **Side-Out** scoring
3. Set win score and best-of format
4. Tap **Start Match**

### Logging Points During a Match
1. Tap the **＋ Team Name** button for whichever team scored
2. The point detail sheet slides up — choose a category:
   - **⚡ Winner Shot** — your team hit a clean winner
   - **✗ Opponent Error** — the other team made a mistake
3. Tap a player card to attribute the point, or **Skip** to log without attribution
4. The score updates and the point is added to the log

### Running a Tournament
1. Tap the **Tourney** tab
2. Tap **＋ New Tournament**
3. Enter a name, format, and win score
4. Add all players or teams using the sign-up form (Enter key to add quickly)
5. Tap **Generate Groups & Start Tournament**
6. Enter scores for each group fixture using **+ Enter Score**
7. Once all group games are done, tap **Start Knockout Stage**
8. Continue entering scores through QFs, SFs, and the Final
9. The 3rd Place Play-Off runs automatically alongside the Final

---

## Firebase Setup *(optional)*

To enable cloud sync across devices:

1. Go to [console.firebase.google.com](https://console.firebase.google.com)
2. Create a new project
3. Add a **Web App** to the project and copy the config values
4. Enable **Firestore Database** in test mode
5. In the app, tap **☁ Cloud** on the History tab
6. Paste your API Key, Auth Domain, Project ID, and App ID
7. Tap **Connect**

---

## File Structure

This app is intentionally a **single self-contained HTML file** — all CSS, JavaScript, and markup are bundled together for simplicity and portability.

```
pickleball-pro-app.html   ← The entire app
```

A `sw.js` service worker file can optionally be placed alongside it for full offline PWA support:

```javascript
self.addEventListener('install', e => e.waitUntil(caches.open('pb-v1').then(c => c.addAll(['/']))));
self.addEventListener('fetch', e => e.respondWith(caches.match(e.request).then(r => r || fetch(e.request))));
```

---

## Browser Support

Works in all modern browsers. Tested on:
- Chrome / Edge (desktop + Android)
- Safari (desktop + iOS)
- Firefox

---

## Roadmap Ideas

- [ ] Shareable tournament bracket links (read-only public view)
- [ ] Real-time multi-device scoring via Firebase live listeners
- [ ] Player profiles with career statistics across matches
- [ ] QR code sign-up for tournaments
- [ ] Native iOS/Android app via Capacitor

---

## Tech Stack

- **Vanilla HTML / CSS / JavaScript** — zero dependencies, zero build tools
- **localStorage** — all data persisted locally in the browser
- **Firebase Firestore** *(optional)* — cloud sync via dynamic import
- **Google Fonts** — Archivo & Archivo Black
- **PWA** — Web App Manifest + Service Worker

---

## Licence

MIT — free to use, modify, and distribute.
