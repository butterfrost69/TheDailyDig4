# The Daily Dig — Investigative Journalism Mystery Website

> *"Veritas Fodere Non Timet" &mdash; Truth Does Not Fear The Spade*

A complete, responsive, and deeply atmospheric fictional investigative journalism website built for tabletop roleplaying games, murder mysteries, and interactive detective scenarios.

Published by **Dignan Dough**, Senior Investigative Correspondent and Editor in Blackwood County.

---

## 🗞 Highlights & Features

- **Credible Editorial Broadsheet Aesthetic**: Traditional newspaper typography (`Playfair Display`, `Source Serif 4`, `Courier Prime`), warm newsprint cream background, charcoal black text, and restrained dark red accents (`#8b1e1e`).
- **Complete Multi-Page Structure**:
  - `index.html`: Broadsheet homepage featuring the Senior Correspondent Photojournalism Portfolio, the Wilhelm memorial lead article, Paul George MVP sports bulletin, and the active editor's desk.
  - `articles/photojournalism-archive.html`: Full 8-plate visual retrospective and photojournalism portfolio with interactive lightbox zoom.
  - `articles/tragic-death-of-wilhelm.html`: Satirical memorial broadsheet tribute to Wilhelm (Borderlands 2), framed as a fallen noble hero slain in unknown gang violence at the End of the Line rail crossing.
  - `articles/paul-george-mvp.html`: Celebratory sports desk dispatch detailing Paul George's historic MVP coronation in a landslide vote with voting breakdown.
  - `archives.html`: Streamlined, curated article vault focusing on primary news dispatches and visual portfolios.
  - `about.html`: Biographical profile and photographic dossier of the Senior Correspondent & Publisher.
  - `investigations.html` & `research-notes.html`: Archival investigative dossiers and research notes.
  - `404.html`: Authentic newspaper judicial injunction notice.
- **Interactive Roleplaying Features**:
  - **Quick Search (Ctrl+K or 🔍 button)**: Real-time search across all dispatches and clues.
  - **Clickable Redactions**: Blacked-out text that unseals on click or hover.
  - **Audio Wiretap Simulation**: Playable 911 emergency call dispatch with animated audio waveforms.
  - **Confidential Tip Line Modal**: Interactive whistleblower form that issues randomized tracking tokens (`#TIP-8849-CONF`).
  - **Theme & Font Scaler**: Switch between *Newsprint Cream*, *Crisp White*, and *Night Desk*, with live text resizing (`A-` / `A+`).
  - **Print Stylesheet (`print.css`)**: Strips digital navigation and formats any page into an authentic broadsheet newspaper handout ready for in-person tabletop gaming sessions!
- **Zero Dependencies**: 100% static HTML5, CSS3, and vanilla JavaScript. No database, no Node server, no API keys, and no paid services required.
- **Ready for Netlify**: Includes `netlify.toml` and `_headers` for instant 1-click deployment.

---

## 🚀 Quick Start & Local Testing

### Option 1: Direct File Opening
Double-click `index.html` in file explorer. The site opens directly in any modern browser with all styling and interactions working.

### Option 2: Local HTTP Server (Python)
```powershell
python -m http.server 8000
```
Open [http://localhost:8000](http://localhost:8000).

### Option 3: Node / npx
```powershell
npx serve .
```

---

## 🌐 Deploying to Netlify

### Drag & Drop (Fastest)
1. Navigate to [app.netlify.com/drop](https://app.netlify.com/drop).
2. Drag and drop the `DailyDig` folder onto the page.
3. Your site is live immediately with a free HTTPS URL.

### Via Git Repository
Connect your GitHub/GitLab repo to Netlify. Netlify will read `netlify.toml` automatically (`publish = "."`, zero build command).

---

## 🕵️ Customizing the Mystery

See [MYSTERY_CUSTOMIZATION_GUIDE.md](MYSTERY_CUSTOMIZATION_GUIDE.md) for step-by-step instructions on replacing names, dates, crime scenes, suspect alibis, and clues with your own custom campaign details.
