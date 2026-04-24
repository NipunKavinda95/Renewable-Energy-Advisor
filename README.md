# ⚡ GridFIS — Renewable Energy Grid Advisor

A **Type-1 Mamdani Fuzzy Inference System** that advises on the optimal percentage of grid load to supply from renewable energy sources (solar PV + wind turbine + battery storage) based on real-time sensor inputs.

Built as part of the **Fuzzy Logic & Evolutionary Computing** module at **De Montfort University (DMU)**, Leicester, UK.

**Supervised by:** Prof. Francisco Chiclana & Dr. Zacharias Anastassi
**Institute:** Institute of Artificial Intelligence (IAI), DMU

---

## 👨‍💻 Author

**Nipun Kavinda**

Postgraduate student at De Montfort University, Leicester, UK, specialising in Artificial Intelligence and Machine Learning. Background in software engineering with hands-on experience in fuzzy logic systems, IoT integration, React web development, and smart energy applications. Actively seeking opportunities in AI-driven smart systems and energy technology, particularly within UAE markets including ADNOC and the broader Gulf energy sector.

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue?style=flat&logo=linkedin)](https://linkedin.com/in/YOUR-LINKEDIN)
[![GitHub](https://img.shields.io/badge/GitHub-Follow-black?style=flat&logo=github)](https://github.com/YOUR-USERNAME)

---

## 🌐 Live Demo

> **[Launch GridFIS Web App](https://YOUR-USERNAME.github.io/renewable-energy-fis)**

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
├── src/
│   ├── FuzzyEnergyApp.jsx            ← Main React component + JS fuzzy engine
│   ├── App.js                        ← App entry point
│   ├── index.js                      ← React root with PWA registration
│   ├── index.css                     ← Global styles
│   └── serviceWorkerRegistration.js  ← PWA service worker registration
│
├── public/
│   ├── index.html                    ← HTML with PWA meta tags
│   ├── manifest.json                 ← PWA manifest
│   └── service-worker.js             ← Offline caching
│
├── package.json                      ← Dependencies + deploy scripts
└── README.md
```

---

## 🚀 Run Locally

**Requirements:** Node.js v16+, npm

```bash
# Clone the repository
git clone https://github.com/YOUR-USERNAME/renewable-energy-fis
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

## 📱 App Features

- **Dashboard** — 4 live sensor sliders + real-time gauge output
- **MF Charts** — Membership function plots with live μ values
- **Output Curve** — Aggregated fuzzy output with centroid marker
- **Rules Panel** — All 15 rules with firing status and α-cut strength

---

## 🌍 Real-World Relevance

Designed with UAE smart grid applications in mind:

- Aligned with **UAE Energy Strategy 2050** (44% clean energy target)
- Relevant to **ADNOC** smart operations and energy management
- Extendable to real-time IoT sensor integration via MQTT
- Future work: Type-2 FIS, ROS2 node integration, reinforcement learning

---

## 📚 Key References

- Zadeh, L.A. (1965). Fuzzy sets. *Information and Control*, 8(3), 338–353.
- Mamdani & Assilian (1975). Linguistic synthesis. *Int. J. Man-Machine Studies*, 7(1).
- Ross, T.J. (2004). *Fuzzy Logic with Engineering Applications*, 2nd ed. Wiley.
- Hossain et al. (2019). Evolution of microgrids. *Int. J. Electrical Power & Energy Systems*.
- Zia et al. (2018). Microgrids energy management. *Applied Energy*, 222.

---

## 📄 Licence

Developed for academic purposes at De Montfort University.
© 2026 Nipun Kavinda — Fuzzy Logic & Evolutionary Computing
