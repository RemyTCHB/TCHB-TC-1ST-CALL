# TC Checklist — Total Cash Home Buyers

A branded, single-file web checklist for **TC (Transaction Coordinator) First Calls** with property sellers. Designed to keep acquisitions reps on-script, capture every answer the dispo and closing teams need, and never lose a note between calls.

> Open the page → type in an address → ask the questions → check the boxes → answers auto-save → print to PDF when done.

---

## ✨ Features

- **Single HTML file** — no build step, no backend, no dependencies to install. Drop it on GitHub Pages, an S3 bucket, or just double-click it locally.
- **Per-address persistence** — every checklist is saved to `localStorage` keyed by the property address. Come back tomorrow, type the address, all checks and notes reload.
- **Inline answer fields** — every question gets its own text input directly below it for capturing the seller's response, not just a binary check.
- **CRM lead link field** — paste the GoHighLevel (or any CRM) lead URL so the call notes stay tied to the deal.
- **Saved Checklists manager** — modal to load or delete any previously saved address.
- **Auto-complete dropdown** for any address you've already worked.
- **Expand / Collapse All** + accordion sections to keep the UI clean during a live call.
- **Print / PDF view** — fully styled print layout that strips controls, expands all sections, and renders notes as bold text under each question.
- **Reset Call** — one click to wipe the current checklist after confirmation.
- **Unsaved Draft recovery** — if you start a checklist without entering an address, it's saved as a draft and recovered next visit.
- **Fully responsive** — works on mobile, tablet, desktop.
- **TCHB-branded** — Inter font, TCHB blue (`#36347A`) and red (`#D32027`) palette, glassmorphism header.

---

## 📋 Sections Covered

| Section | Purpose |
|---|---|
| **Mortgage Questions** | Mortgage company, payoff, pre-foreclosure flags, late payments |
| **Pictures** | Current photos from the seller |
| **Emergency Contact Info** | Backup contact name, phone, preferred channel |
| **HOA / Condo** | Special assessments, monthly fees, rental restrictions, LLC eligibility |
| **SFHs (Single Family Homes)** | Big-ticket items, occupancy, construction, utilities, lot size, flood zone, zoning, pool, parking, schools |
| **Land** | Lot dimensions, zoning, flood zone, utilities, surveys, wetlands, protected species |
| **Income Producing Properties** | Per-unit details, meters, multi-family zoning, parking |
| **Mobile Homes** | Model, manufacturer, title status, foundation, year, single/double wide |

---

## 🚀 Quick Start

### Option 1 — Just open it
Download `tc_checklist.html` and open it in any modern browser. That's it.

### Option 2 — Host on GitHub Pages
1. Push this repo to GitHub.
2. **Settings → Pages → Source: `main` branch / root.**
3. Open `https://<your-user>.github.io/<repo-name>/tc_checklist.html`.

### Option 3 — Host anywhere static
Any static host (Netlify, Vercel, Cloudflare Pages, S3, IIS, Nginx) — the file is self-contained.

---

## 🛠 Tech Stack

- **HTML5** + vanilla JavaScript (no frameworks)
- **Tailwind CSS** via CDN (`cdn.tailwindcss.com`) with custom TCHB theme extension
- **Font Awesome 6** for icons
- **Google Fonts — Inter** for typography
- **Web Storage API** (`localStorage`) for persistence

No build tools. No npm. No bundler.

---

## 💾 How Data Is Saved

All data lives in the browser's `localStorage` under a single key. The schema looks roughly like:

```js
{
  "123 Main St, Miami FL": {
    crm: "https://app.gohighlevel.com/...",
    checks:  { cb_0: true, cb_3: true, ... },
    answers: { ans_0: "Wells Fargo", ans_1: "$182,500", ... }
  },
  "456 Oak Ave, Tampa FL": { ... },
  "Unsaved Draft": { ... }
}
```

**Heads up:**
- Data is **per-browser, per-device.** Clearing site data wipes it.
- Nothing is sent to a server — this is a local-only tool by design.
- If you need cross-device sync, export the data via Print → Save as PDF, or fork the project and wire up a backend.

---

## 🖨 Printing / PDF Export

Click **Print / PDF** → all sections expand → controls hide → print dialog opens. Choose "Save as PDF" to file the call.

The print stylesheet renders:
- Section headers in TCHB blue
- Checked items with their notes as bold text
- A clean, dense layout suitable for attaching to a CRM record

---

## 🎨 Customization

### Change the brand colors
Edit the Tailwind config block near the top of the file:

```js
colors: {
  tchb: {
    blue:  '#36347A',
    red:   '#D32027',
    green: '#00A859',
    dark:  '#1E1E24',
    light: '#F8FAFC'
  }
}
```

### Add / remove / rename a section
Each section is an accordion block in the `<div id="checklist-container">`. Copy an existing `<div class="bg-white rounded-xl ...">` block, change the title, icon (any [Font Awesome 6 icon](https://fontawesome.com/icons)), and the list of `<label class="check-container">` items.

### Add / remove questions
Inside any accordion, add another:

```html
<label class="check-container">
    <input type="checkbox" class="checklist-cb">
    <span class="checkmark"></span>
    <span class="check-text">Your new question here?</span>
</label>
```

Use `nested-1` or `nested-2` on the `<label>` for indented follow-up questions.

---

## 🌐 Browser Compatibility

Tested on the latest Chrome, Edge, Safari, and Firefox. Anything that supports `localStorage`, CSS Grid, and Flexbox will work — basically every browser from the last decade.

---

## 📁 Project Structure

```
.
├── tc_checklist.html   # The entire app
├── icon.svg            # Favicon (referenced from /main/icon.svg)
├── logo.svg            # Header logo (referenced from /main/logo.svg)
└── README.md
```

---

## 🤝 Contributing

This is an internal tool — PRs and issues welcome from the TCHB team. For changes that affect the question set, please confirm with the acquisitions lead before merging.

---

## 📄 License

© Total Cash Home Buyers. All rights reserved. Internal use only unless otherwise noted.
