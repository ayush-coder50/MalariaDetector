# NLM Malaria Screener — Enhanced Web Frontend

An enhanced web-based frontend for the [NLM Malaria Screener](https://github.com/LHNCBC/MalariaScreener) Android application, developed by the Lister Hill National Center for Biomedical Communications (LHNCBC), an R&D division of the US National Library of Medicine.

---

## Project Structure

```
malaria-screener-enhanced/
├── index.html                    ← Entry point
├── README.md
└── src/
    ├── styles/
    │   ├── variables.css         ← Design tokens (colours, fonts, radii)
    │   ├── base.css              ← Reset & global styles
    │   ├── layout.css            ← Shell, sidebar, topbar, content area
    │   ├── components.css        ← Reusable UI components (buttons, pills, table, etc.)
    │   ├── pages.css             ← Page-specific styles
    │   └── animations.css        ← Keyframes & transitions
    ├── utils/
    │   ├── state.js              ← Global app state (wizard, camera, settings)
    │   ├── notify.js             ← Toast notification system
    │   ├── router.js             ← Client-side page router
    │   └── app.js                ← Bootstrap / init
    ├── components/
    │   ├── Sidebar.js            ← Left navigation sidebar
    │   └── Topbar.js             ← Top navigation bar
    └── pages/
        ├── Dashboard.js          ← Overview — KPIs, recent sessions, positivity donut
        ├── Session.js            ← 5-step new session wizard
        ├── Camera.js             ← Live capture view with cell counter
        ├── Database.js           ← Patient records grid
        ├── Upload.js             ← Box.com sync interface
        ├── Guidelines.js         ← Imaging best-practices reference
        └── Settings.js           ← App configuration panel
```

---

## Pages

| Page | Android Equivalent | Description |
|---|---|---|
| **Dashboard** | `MainActivity` | KPI overview, recent sessions, positivity rate donut |
| **New Session** | `NewSessionActivity` | 5-step wizard: smear type → patient → slide → settings → begin |
| **Camera View** | `CameraActivity` | Circular FOV overlay, real-time cell counter, thumbnail grid |
| **Patient Database** | `DatabaseActivity` | Patient cards with parasitemia % and risk badges |
| **Upload & Sync** | `BoxActivity` | Box.com OAuth connect, session folder management |
| **Imaging Guidelines** | `User_guideline.pdf` | 6 tip cards + good vs bad comparison table |
| **Settings** | `SettingsActivity` | Camera, model, session, upload, and database config |

---

## How to Run

This is a vanilla HTML/CSS/JS project — **no build step required**.

```bash
# Option 1: open directly in browser
open index.html

# Option 2: serve locally (avoids any browser file:// restrictions)
npx serve .
# or
python3 -m http.server 8080
```

Then navigate to `http://localhost:8080`.

---

## Original Android App

| Property | Value |
|---|---|
| Repository | https://github.com/LHNCBC/MalariaScreener |
| Developer | LHNCBC / NIH / NLM |
| Platform | Android API 21+ (Lollipop 5.0+) |
| Detection | OpenCV 3.4.2 + TensorFlow CNN (`.pb` models) |
| Segmentation | Marker-Based Watershed (thin) + C++ native (thick) |
| Classifier | SVM + CNN patch classification |
| Cloud sync | Box.com API |

### Building the Android APK

```bash
git clone https://github.com/LHNCBC/MalariaScreener.git
```

Open in **Android Studio**, then install:
- Android SDK Platform **28**
- Android SDK Build-Tools **27.0.3+**
- CMake **3.4.1+**
- Android NDK (for native OpenCV)

---

## Citation

```bibtex
@article{yu2020malaria,
  title   = {Malaria Screener: a smartphone application for automated malaria screening},
  author  = {Yu, Hang and Yang, Feng and Rajaraman, Sivaramakrishnan and others},
  journal = {BMC Infectious Diseases},
  volume  = {20},
  pages   = {1--8},
  year    = {2020},
  publisher = {BioMed Central}
}
```
