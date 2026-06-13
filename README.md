# Census Field Mapper

A mobile-friendly web app for India Census field survey work. Runs entirely in the browser — no app install needed. Built for enumerators to track their path, mark houses, save survey areas, and share them with supervisors or team members.

---

## Features

- **Live GPS tracking** — draws your path on the map as you walk
- **House marking** — mark each house as Done, Skipped, or Revisit with optional notes
- **Manual mode** — tap the map to place markers without GPS (useful indoors or in low signal areas)
- **Save layouts** — save a completed survey area to Firebase with a name
- **Share via link** — anyone with the link can open it and see the exact path and markers on their map
- **WhatsApp sharing** — share layout links directly via WhatsApp in one tap
- **Session restore** — app remembers your current session even if you close the browser
- **Saved layouts list** — access all your past saved layouts anytime from the 📂 Layouts button
- **Works on any phone** — no install, just open the link in Chrome (Android) or Safari (iPhone)

---

## How to Use

### Starting a survey
1. Open the app link in Chrome or Safari
2. Tap **Open Map** on the welcome screen
3. Tap **▶ Start** — allow location permission when the browser asks
4. Walk your survey area — the blue line traces your path automatically

### Marking houses
1. Select the marker type from the bottom bar:
   - **✓ Done** — survey completed at this house
   - **— Skip** — nobody home or refused
   - **↩ Revisit** — needs a follow-up visit
2. Tap **🏠 Mark** to place a marker at your current GPS position
3. Add an optional note (house number, reason, etc.) and tap Confirm
4. Tap any marker on the map to see its details or delete it

### Manual mode
- Tap **✋ Manual** in the bottom bar to toggle manual mode on
- In manual mode, tap anywhere on the map to place a marker at that location
- Useful when GPS signal is weak or you want to mark a location you already passed
- Toggle it off to go back to GPS tracking

### Saving and sharing a layout
1. After mapping an area, tap **💾 Save**
2. Enter a name (e.g. "Ward 4 – Block B, Sector 12")
3. Tap **Save & Get Link** — the layout uploads to Firebase
4. Use **📋 Copy Link** or **💬 WhatsApp** to share the link
5. Anyone who opens the link sees the full path and all markers on their map

### Viewing saved layouts
- Tap **📂 Layouts** in the top right to see all your saved layouts
- **👁 View** — loads the layout onto the map
- **📤 Share** — share the link again anytime
- **🗑** — removes it from your list (the shared link still works)

---

## Setup

### 1. Firebase (required for Save & Share)

The app uses Firebase Realtime Database to store and share layouts. You need to create a free Firebase project and paste your database URL into the code.

**Steps:**
1. Go to [console.firebase.google.com](https://console.firebase.google.com) and sign in with a Google account
2. Click **Add project** → name it (e.g. `census-mapper`) → click through → **Create project**
3. In the sidebar click **Build → Realtime Database → Create Database**
4. Choose any region → select **Start in test mode** → click Enable
5. Copy the database URL shown (looks like `https://census-mapper-default-rtdb.firebaseio.com`)
6. Open `census_mapper.html` in a text editor and find this line:

```js
var FIREBASE_DB_URL = 'YOUR_FIREBASE_DATABASE_URL_HERE';
```

7. Replace `YOUR_FIREBASE_DATABASE_URL_HERE` with your URL
8. Save the file

> **Note:** Test mode allows open read/write for 30 days. After that, go to Firebase Console → Realtime Database → Rules and set both `read` and `write` to `true` to keep it open for internal use.

### 2. GitHub Pages (hosting)

1. Create a repository on GitHub (e.g. `census-mapper`)
2. Upload `census_mapper.html` to the repository
3. Go to **Settings → Pages → Source → main branch → / (root)** → Save
4. Your app will be live at `https://yourusername.github.io/census-mapper/census_mapper.html`
5. Share this link with all enumerators — they just open it in their phone browser

---

## Data & Privacy

- **Current session** (path + markers) is saved in the phone's local browser storage — it stays on the device and is never uploaded unless you tap Save
- **Saved layouts** are uploaded to your Firebase project when you tap 💾 Save — only people with the link can access them
- **No login required** — the app has no accounts or authentication
- All map tiles are loaded from OpenStreetMap

---

## Tech Stack

- [Leaflet.js](https://leafletjs.com) — map rendering
- [OpenStreetMap](https://openstreetmap.org) — map tiles
- [Firebase Realtime Database](https://firebase.google.com) — layout storage and sharing
- Browser Geolocation API — GPS tracking
- localStorage — local session persistence
- Pure HTML/CSS/JS — no build tools, no frameworks, no dependencies to install

---

---

## Known Limitations

- Map tiles require an internet connection to display (GPS tracking and marker placement still works offline, tiles just won't load)
- localStorage is browser-specific — clearing browser data will erase the current session
- Firebase test mode rules expire after 30 days — update rules manually after that (see Setup above)
- Shared layout links are public — anyone with the link can view the layout

---

## Credits

Built for India Census 2025 field survey operations.  
Map data © [OpenStreetMap contributors](https://www.openstreetmap.org/copyright)

## About

I am currently studying in 12th grade and this was just a personal project.
I started this project due to my parents being assigned the duty in india census 2026.
As they needed to map their area too and also mark the houses done. This could also help in keeping track of their own progress.
Existing mapping tools were either too complex, required app installs, 
or didn't work well for simple field survey use on a basic smartphone browser. 
So i built this instead — a lightweight, no-install tool that any enumerator can open on their phone and start using immediately.

**The entire app was designed and built with the help of **Claude** (by Anthropic)**, 

developed over multiple iterations based on real feedback from actual field use requirements — fixing GPS permission issues, 
adding layout saving, Firebase integration, and WhatsApp sharing along the way.
If you're an enumerator, supervisor, or anyone doing similar field mapping work and find this useful, feel free to use it.
