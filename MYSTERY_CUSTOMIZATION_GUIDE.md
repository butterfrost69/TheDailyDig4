# The Daily Dig — Mystery Customization & Game Master Guide

Welcome to **The Daily Dig**, an investigative journalism website designed for murder mysteries, tabletop roleplaying games (Call of Cthulhu, Gumshoe, Delta Green, D&D modern, Vaesen, or custom murder mystery parties), and immersive escape experiences.

This guide explains how to quickly replace the fictional names, locations, clues, and crimes with your own mystery details, how to test the site locally, and how to publish it for free to **Netlify**.

---

## Table of Contents
1. [Mystery Architecture Overview](#1-mystery-architecture-overview)
2. [Quick Reference: Where to Edit What](#2-quick-reference-where-to-edit-what)
3. [Step-by-Step Customization](#3-step-by-step-customization)
   - [A. The Reporter & Publication](#a-the-reporter--publication)
   - [B. The Victim & Incident](#b-the-victim--incident)
   - [C. The Suspects & Persons of Interest](#c-the-suspects--persons-of-interest)
   - [D. The Clues & Field Scratchpad](#d-the-clues--field-scratchpad)
   - [E. Updating the Quick Search Database](#e-updating-the-quick-search-database)
4. [How Players Discover Clues](#4-how-players-discover-clues)
5. [Local Testing Instructions](#5-local-testing-instructions)
6. [Netlify Deployment Instructions](#6-netlify-deployment-instructions)

---

## 1. Mystery Architecture Overview

The site is built entirely with **clean, dependency-free static HTML, CSS, and vanilla JavaScript**. It requires **no database, no backend server, no login system, and no API keys**.

### File Map
- **`index.html`**: Broadsheet front page with lead homicide story, breaking ticker, recent watchdog dispatches, crime scene schematic, wiretap audio mockup, and sidebar dossier.
- **`investigations.html`**: Central dossier hub containing active cases, timelines, suspect dossiers, and forensic exhibits.
- **`archives.html`**: Interactive, searchable archive with live topic filtering and keyword search.
- **`about.html`**: Biography of Senior Investigative Reporter **Dignan Dough**, his editorial credo, PGP security fingerprint, and office details.
- **`research-notes.html`**: **The discreetly linked research-notes / clue repository**. Contains Dignan’s working field scratchpad, interactive clue checkboxes that persist in `localStorage`, clickable redacted evidence, and a **"Game Master Mode"** toggle that reveals hidden solutions and GM tips.
- **`articles/alder-creek-drowning.html`**: The full flagship murder investigation article.
- **`articles/sterling-manor-breakin.html`**: Secondary investigation (estate intrusion & property codicils).
- **`articles/railway-ghost-manifest.html`**: Third investigation (nocturnal chemical transit & contractor payoffs).
- **`articles/blotter-cold-trail.html`**: Police blotter with timestamped dispatches and 911 transcript.
- **`404.html`**: Authentic newspaper retraction / injunction notice.

---

## 2. Quick Reference: Where to Edit What

Every file contains clearly labeled HTML comments:
```html
<!-- ======================================================== -->
<!-- MYSTERY EDIT ZONE: [Section Name]                        -->
<!-- Replace the text below with your custom details          -->
<!-- ======================================================== -->
```

| Detail You Want to Change | Primary Files to Edit |
|---|---|
| **Publication Name / Motto** | `index.html`, `investigations.html`, `archives.html`, `about.html`, `research-notes.html` |
| **Reporter Name ("Dignan Dough")** | `about.html`, `index.html`, and `articles/*.html` |
| **The Victim & Crime Scene** | `index.html`, `investigations.html`, `articles/alder-creek-drowning.html` |
| **Suspects & Alibis** | `investigations.html` (Suspect Ledger) & `research-notes.html` |
| **Clues, Codes & Safe Combinations** | `research-notes.html` (Cards 1–8) |
| **GM Secret Solution** | `research-notes.html` (Bottom `<section class="gm-secret-block">`) |
| **Search Autocomplete Results** | `js/main.js` (`SEARCH_DATABASE` array) |

---

## 3. Step-by-Step Customization

### A. The Reporter & Publication
- **Default Publication**: *The Daily Dig* ("Veritas Fodere Non Timet")
- **Default Reporter**: **Dignan Dough**, Senior Investigative Correspondent
- To customize:
  1. Open `about.html`. Replace Dignan's biography, typewriter brand, and bureau office with your character's background.
  2. To change the woodcut portrait, simply replace `assets/images/dignan-dough-portrait.svg` or drop in your own `.png`/`.jpg` and update the `src=""` attribute.

### B. The Victim & Incident
- **Default Victim**: Arthur "Artie" Pendelton, 61, Chief Archivist of Blackwood County.
- **Default Crime**: Found in the sluice weir at Alder Creek Mill; police claim he slipped while fishing, but he hated water, winch cables were sheared with hydraulic cutters, and a 1924 title deed was stolen from the county sub-vault.
- To customize:
  1. Open `articles/alder-creek-drowning.html`.
  2. Replace the headline, dateline, and paragraphs with your mystery's victim and death scene.
  3. Update the matching summary on `index.html` under `class="lead-headline"`.

### C. The Suspects & Persons of Interest
Open `investigations.html` and scroll to `<!-- SUSPECTS & KEY FIGURES LEDGER -->`:
1. **Mayor Thaddeus Vance** (Motivated by a $40M resort deal that the victim's documents would block).
2. **Sheriff Harlan Cross** (Compromised by gambling debts, hastily ruled the death an accident).
3. **Helena Sterling** (Mayoral rival who secretly earns 12% royalties if the land is rezoned).
4. **Julian "Grit" Finch** (Scrap hauler whose flatbed truck was spotted at the mill).

Simply change their names, ages, motives, and stated alibis to match your RPG campaign's cast!

### D. The Clues & Field Scratchpad (`research-notes.html`)
Open `research-notes.html`. Each clue card is structured as:
```html
<div class="clue-card" data-category="physical" data-clue-id="winch-cable">
  <div class="clue-meta-row">
    <span>EVIDENCE #01 • SCENE OF DEATH</span>
    <span class="stamp stamp-red">FORENSIC</span>
  </div>
  <h3 class="clue-title">Sheared Sluice Gate Control Cable</h3>
  <div class="clue-body">
    <!-- Player-facing clue description -->
    The steel cable showed clean diagonal shear marks...
  </div>
  
  <!-- GM Secret Block (Visible only when GM Toggle is ON) -->
  <div class="gm-secret-block">
    <strong>GM TRUTH:</strong> Julian Finch owns the hydraulic cutter model...
  </div>
</div>
```
- **Player Clues**: Edit `.clue-body`. You can use `<span class="redacted">Secret Text</span>` for text that players can click to reveal!
- **GM Spoilers**: Edit `.gm-secret-block` to write notes for yourself explaining how the clue works, what skill check is required, or where to find the physical prop.

### E. Updating the Quick Search Database
In `js/main.js`, update the `SEARCH_DATABASE` array near the top of the file so that instant search (Ctrl+K) searches your new article titles and keywords.

---

## 4. How Players Discover Clues

The site provides multiple authentic ways for players to find clues:
1. **Discreet Links**:
   - In the main navigation bar: a discreet link titled `📁 Desk Notes (DN-402)`.
   - In the footer: under Legal & FOIA: `¶ Reporter Desk Dossier [Log DN-402]`.
   - In Dignan Dough's bio on `about.html`: a link directing readers to cross-reference Case Dossier DN-402.
2. **Interactive Redactions**:
   - Any text wrapped in `<span class="redacted">...</span>` appears as black marker redaction.
   - Hovering or clicking reveals the hidden clue!
3. **Working Wiretap Player**:
   - On `index.html`, clicking **Play (▶)** starts an interactive audio simulation with animated waveform and 911 dispatch transcript.
4. **Confidential Tip Line**:
   - Clicking **"Secure Tip Line"** opens a modal where players can enter statements. Upon submitting, it generates a unique receipt token (e.g., `#TIP-8849-CONF`).
5. **Print Handouts**:
   - Clicking **"🖨 Print Dispatch"** on any page formats it cleanly for black-and-white printing as a physical handout.

---

## 5. Local Testing Instructions

You can test the website locally in seconds without installing any complex software.

### Option 1: Double-Click
Simply navigate to your `DailyDig` folder and double-click `index.html`. It will open in Chrome, Firefox, Edge, or Safari with all styles, links, and search features fully operational.

### Option 2: Local Python Server (Recommended)
Open PowerShell in the `DailyDig` directory and run:
```powershell
python -m http.server 8000
```
Then visit [http://localhost:8000](http://localhost:8000) in your web browser.

### Option 3: Node / npx serve
```powershell
npx serve .
```

---

## 6. Netlify Deployment Instructions

The site is prepared specifically for Netlify with zero build configuration (`netlify.toml` and `_headers` are already included).

### Method A: Netlify Drop (Instant — No Git Required)
1. Go to [https://app.netlify.com/drop](https://app.netlify.com/drop).
2. Log in or create a free Netlify account.
3. Drag and drop the entire `DailyDig` folder directly into the Netlify drop zone in your browser.
4. Netlify will deploy your site in ~5 seconds and give you a live URL (e.g. `https://the-daily-dig-mystery.netlify.app`).
5. (Optional) In **Site configuration > Change site name**, give it a custom name like `blackwood-daily-dig`.

### Method B: Via GitHub / GitLab
1. Initialize a git repository:
   ```powershell
   git init
   git add .
   git commit -m "Initial commit of The Daily Dig mystery site"
   ```
2. Push to your GitHub repository.
3. In Netlify, click **"Add new site" > "Import an existing project" > "GitHub"**.
4. Select your repository.
5. Netlify will automatically detect the settings:
   - **Build command**: (leave blank)
   - **Publish directory**: `.`
6. Click **Deploy**. Any future commits to `main` will automatically redeploy!
