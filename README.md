# ⚡ GridFIS — Renewable Energy Grid Advisor

A **Type-1 Mamdani Fuzzy Inference System** that advises on the optimal percentage of grid load to supply from renewable energy sources (solar PV + wind turbine + battery storage) based on real-time sensor inputs.

Built as an additional part of the Fuzzy Logic & Evolutionary Computing Assignment that  **Fuzzy Inference System Design** at **De Montfort University (DMU)**, Dubai, UAE.

---

## 🌐 Live Demo

> **[Launch GridFIS Web App](https://nipunkavinda95.github.io/Renewable-Energy-Advisor/)**

Installable as a **Progressive Web App (PWA)** on Android and iOS — works offline after first load.

---

## 🔬 System Overview

The FIS takes 4 real-time sensor inputs and produces a crisp advisory output:

| Input | Range | MF Type | Justification |
|---|---|---|---|
| Solar Irradiance | 0–1000 W/m² | Triangular | Sharp solar day boundaries |
| Wind Speed | 0–25 m/s | Trapezoidal | Turbine rated output plateau |
| Battery Charge | 0–100% | Gaussian | Smooth electrochemical SoC dynamics |
| Grid Demand | 0–100% | Triangular | Diurnal demand peaks |

| Output | Range | MF Terms |
|---|---|---|
| Renewable Output | 0–100% | VeryLow, Low, Medium, High, VeryHigh |

**Rule base:** 15 non-redundant Mamdani rules (Ross 2004, Chapter 9 criteria)  
**Defuzzification:** Centroid method  
**AND operator:** min  
**OR operator:** max

---

## 📊 Key Results

| Test Case | Solar | Wind | Battery | Demand | Output |
|---|---|---|---|---|---|
| TC1 — Ideal day | 800 | 18 | 85 | 30 | **79.96%** |
| TC2 — Peak solar | 900 | 20 | 90 | 50 | **85.55%** |
| TC3 — Moderate | 500 | 12 | 60 | 55 | **50.00%** |
| TC4 — Poor resources | 150 | 4 | 35 | 70 | **21.41%** |
| TC5 — Worst case | 50 | 2 | 15 | 90 | **8.39%** |
| TC6 — High demand | 700 | 15 | 80 | 80 | **59.21%** |
| TC7 — Mid-range | 300 | 8 | 50 | 50 | **50.00%** |
| TC8 — Windy | 600 | 20 | 40 | 30 | **74.14%** |

---

## 🗂️ Project Structure

```
renewable-energy-fis/
│
├── matlab/
│   ├── RenewableEnergyFIS_FINAL.mlx     ← MATLAB Live Script (main FIS code)
│   ├── RenewableEnergyAdvisor.fis        ← Saved FIS file for deployment
│   └── figures/                          ← All 14 generated PNG figures
│       ├── fig1_input_mfs.png
│       ├── fig2_fis_architecture.png
│       ├── fig3_test_cases.png
│       └── ...
│
├── python/
│   └── fig2_fis_architecture.py          ← FIS architecture diagram generator
│
├── src/
│   ├── FuzzyEnergyApp.jsx                ← Main React component + fuzzy engine
│   ├── App.js                            ← App entry point
│   ├── index.js                          ← React root with PWA registration
│   ├── index.css                         ← Global styles
│   └── serviceWorkerRegistration.js      ← PWA service worker registration
│
├── public/
│   ├── index.html                        ← HTML with PWA meta tags
│   ├── manifest.json                     ← PWA manifest (name, icons, theme)
│   ├── service-worker.js                 ← Offline caching service worker
│   └── icons/                            ← App icons (192x192, 512x512)
│
├── report/
│   └── FuzzyLogic_Report_FINAL.docx      ← Assignment report
│
├── package.json                          ← React dependencies + deploy scripts
└── README.md
```

---

## 🚀 Run Locally

**Requirements:** Node.js v16+, npm

```bash
# Clone the repository
git clone https://github.com/NipunKavinda95/Renewable-Energy-Advisor
cd renewable-energy-fis

# Install dependencies
npm install

# Start development server
npm start
```

Open `http://localhost:3000` in your browser.

---

## 📱 PWA Installation

**Android (Chrome):**
1. Open the live URL in Chrome
2. Tap the three dots menu
3. Tap **Add to Home Screen**
4. Tap **Install**

**iOS (Safari):**
1. Open the live URL in Safari
2. Tap the **Share** button
3. Tap **Add to Home Screen**

---

## 🔧 MATLAB Requirements

To run the `.mlx` file:
- MATLAB R2021a or newer
- Fuzzy Logic Toolbox

```matlab
% Load and test the saved FIS
fis = readfis('RenewableEnergyAdvisor.fis');
output = evalfis(fis, [800 18 85 30]);  % Returns 79.96%
```

---

## 📱 App Features

- **Dashboard** — 4 live sliders + real-time gauge output
- **MF Charts** — Visual membership function plots with current μ values
- **Output Curve** — Aggregated fuzzy output distribution with centroid marker
- **Rules Panel** — All 15 rules with firing status and α-cut strength

---

## 🌍 Real-World Relevance

This system is designed with UAE smart grid applications in mind:

- Aligned with **UAE Energy Strategy 2050** (44% clean energy target)
- Relevant to **ADNOC** smart operations and energy management
- Architecture extendable to real-time IoT sensor integration via MQTT
- Future work: Type-2 FIS extension, ROS2 node integration, reinforcement learning rule weight tuning

---

## 📚 Key References

- Zadeh, L.A. (1965). Fuzzy sets. *Information and Control*, 8(3), 338–353.
- Mamdani, E.H. & Assilian, S. (1975). An experiment in linguistic synthesis. *Int. J. Man-Machine Studies*, 7(1), 1–13.
- Ross, T.J. (2004). *Fuzzy Logic with Engineering Applications*, 2nd ed. Wiley.
- Hossain, M.A. et al. (2019). Evolution of microgrids. *Int. J. Electrical Power & Energy Systems*, 109, 160–186.
- Zia, M.F. et al. (2018). Microgrids' energy management systems. *Applied Energy*, 222, 1033–1055.

---

## 📄 Licence

This project was developed by Nipun Kavinda, engaging with a university assignment.  
© 2026 — Fuzzy Logic & Evolutionary Computing 
