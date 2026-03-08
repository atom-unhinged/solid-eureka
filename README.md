# 🚧 OTM Book 7 — Ontario Work Zone Planner

**[▶ Open the App](https://atom-unhinged.github.io/solid-eureka/)**

An interactive, offline-ready web app for planning temporary traffic control in Ontario, based on the **Ontario Traffic Manual Book 7: Temporary Conditions (April 2022 Edition)**.

Built as a single HTML file — no install, no server, no dependencies to manage. Open it in any browser and go.

---

## What It Does

This tool walks you through the full OTM Book 7 planning workflow step by step — from classifying your road environment to selecting a typical layout, calculating taper and buffer distances, and generating a printable work zone plan summary.

It's designed for field use: fast, mobile-friendly, and works completely offline once loaded.

---

## Getting Started

1. **Download** `otm7-improved.html`
2. **Open it** in any modern browser (Chrome, Safari, Firefox, Edge)
3. That's it — no installation required

> **Note:** The 📌 My Location button requires the file to be served over `https://` or `localhost`. If you open it directly from your desktop (`file://`), geolocation will be blocked by the browser. Everything else works fine locally.

To run it locally with geolocation:
```bash
python3 -m http.server 8000
# then open http://localhost:8000/otm7-improved.html
```

---

## Features

### ⚡ Quick Calc
Enter a speed and lane width on the home screen for instant results — no setup required.
- Merging taper length (§3.4.3)
- Longitudinal Buffer Area / LBA (§3.4.4)
- Advance warning sign spacing (§4.3)
- One tap to apply results to the full plan

### 📋 Full Planning Workflow
Nine-step guided workflow covering:
- **Location** — map pin or address search
- **Road Environment** — area type, highway type, cross-section, volume (§3.2)
- **Configuration** — shoulder, lane closure, detour, rolling, sidewalk (§3.3)
- **Duration** — mobile, VSD, SD, ID, LD categories (§3.5)
- **Devices & Signs** — checklist, sign library, HVSA table, TCP requirements (§4)
- **Typical Layouts** — all 28 OTM Book 7 schematics with smart filtering (§6)
- **Calculators** — taper, LBA, sign spacing with full formula display (§3.4)
- **My Plan** — complete printable summary with validation warnings

### 📐 Smart Layout Filtering
Layouts matching your road type, config, and duration are shown first. Non-matching layouts are collapsed below with a "Show all" toggle.

### ✅ Validation Warnings
Flags dangerous or non-compliant combinations before you finalize your plan:
- Mobile operation on freeways
- TMA requirements at high speeds
- Layout/configuration mismatches
- Missing selections for long-duration work

### 🌙 Night Work Mode
Toggle on the Devices tab to add §3.8 night-specific requirements to your checklist — retroreflective cone bands, lighting minimums, PVMS brightness, and more.

### 🔗 Share Plan by URL
Encodes your entire plan state into a shareable link. Paste it into a text or email — recipients open it and your plan loads instantly.

### 📚 Reference Tabs
Quick-access dropdown for three reference sections:
- **Active Road Users §3.7** — pedestrian and cyclist requirements
- **Speed Management §3.6** — construction zone fines, speed limits
- **Setup & Removal §5** — safe installation and take-down procedures

### ⌨️ Keyboard Navigation
- `Enter` — advance to next step
- `↑ ↓ ← →` — move between selection cards
- `Space` — select the focused card
- `Escape` — close any open modal

---

## Technical Notes

- **Single file** — all HTML, CSS, and JavaScript in one `~3000 line` file. No build step, no framework, no npm.
- **Offline ready** — all assets load from CDN on first open; after that the app works without internet (except map tiles and address search)
- **State persistence** — plan state is saved to `localStorage` automatically. Closing and reopening the browser restores your work.
- **Share by URL** — state is Base64-encoded into the URL query string (`?plan=...`) for easy sharing
- **Map** — Leaflet.js with OpenStreetMap tiles; address search via Nominatim
- **Print/PDF** — uses browser print dialog with a clean white print stylesheet; no server-side rendering

---

## Limitations

- **Not a substitute for an engineered TCP.** This is a planning aid based on OTM Book 7 typical layouts. All work zones must comply with the official OTM Book 7, the Highway Traffic Act, and applicable Ontario legislation.
- **Always verify measurements on site.** Taper and buffer calculations are formula-based estimates. Field geometry governs.
- **Map is for reference only.** Confirm jurisdiction, authority approvals, and permit requirements before commencing work.
- **Geolocation requires HTTPS.** The My Location button won't work when opening the file directly from your filesystem.

---

## Based On

> Ontario Traffic Manual — Book 7: Temporary Conditions  
> Office Edition · April 2022  
> Ontario Ministry of Transportation  
> [Official PDF ↗](https://otc.org/wp-content/uploads/2023/01/OTM-Book-7-Temporary-Conditions-Office-Edition-April-2022.pdf)

---

## License

This tool is an independent planning aid and is not affiliated with or endorsed by the Ontario Ministry of Transportation or the Ontario Traffic Council.

---

## Credits

Designed and built in collaboration with **[Claude](https://claude.ai)** (Anthropic) — who wrote every line of code, debugged every edge case, and never once complained about being asked to fix the dropdown for the fourth time.

