# sun-quilt-calculator

A locally run web tool to maximize quilt sunlight exposure — combining sunlight, balance and wind conditions to compute the optimal folding scheme.

[English](README_EN.md) | [中文](README.md)

> **Live demo**: https://bibipiano.github.io/sun-quilt-calculator/ (available once GitHub Pages is enabled)

> **In one sentence**: this is a fully local web tool. Based on solar geometry and a physical model, it computes how to fold and hang your quilt — at a given latitude, season, line orientation and under gravity constraints — so that it catches the most sunlight (sunlit area × time) on every day of the year.

## ✨ Core Features

* **Accurate solar path**: built-in Spencer / NOAA simplified formulas compute sunrise/sunset, solar elevation and azimuth for your location (latitude, longitude, altitude) and date.
* **Optimal folding algorithm**: automatically searches whether to hang the quilt by its long edge or short edge, and computes the best fold ratio (e.g. 66:34) to maximize the exposed sunlit area.
* **Safe physical constraints**: combines the capstan friction model and ground-clearance limits to find the best hanging ratio that catches more sun without slipping or touching the ground.
* **Full visualization**:
  * **3D scene**: drag to rotate; sunlit and shaded faces shown; draggable time scrubber.
  * **Top-view azimuth chart**: line direction, normals, sunrise/sunset azimuths and the sun's current position.
  * **Year / day charts**: compare the whole year's daily exposure to find the best drying days.
* **Fully local computing**: no backend, no external dependencies — all computation and rendering happen in your browser, protecting your privacy.

---

## 🚀 How to Use

### Option 1: Run locally (recommended)

1. Download `光照模拟器.html` (Chinese) or `Quilt Sun-Drying Simulator.html` (English) from this repository.
2. Double-click the file to open it in any modern browser (Chrome, Edge, Safari, etc.). You can also open `index.html` as a landing page to pick your preferred language.

### Option 2: Access online (GitHub Pages)

1. Go to your GitHub repository's `Settings` -> `Pages`.
2. Under `Build and deployment`, choose branch `main` and folder `/ (root)`, then click `Save`.
3. Wait 1–2 minutes and refresh — you will get an online URL like `https://bibipiano.github.io/sun-quilt-calculator/`, ready to open.

### Step-by-step Guide

1. **Set your location**: enter latitude, longitude and altitude (optional), or click "Use my location".
2. **Set the line orientation**: read your clothesline azimuth with a phone compass and type it in, or simply drag the dot on the compass in the left panel.
3. **Set quilt parameters**: your quilt's length/width (e.g. 2.0 × 1.5 m), folded thickness, and the clothesline height and length.
4. **Read the recommendation**: the top of the right panel shows the recommended sun-drying scheme — which edge to hang on the line, the fold ratio, and why.

**Want a quick look first?** After opening the page, click **"Load demo (Beijing)"** in the red box below — sample data is loaded and a full recommendation appears instantly:

<img src="docs/guide-demo.png" alt="Click Load demo for a quick try">

**Setting the line orientation (step 2)**: hold and drag the orange dot on the compass — the line direction and the two lit sides update in real time:

<img src="docs/guide-compass.png" width="430" alt="Drag the compass dot to set the line direction">

---

## 🛠️ Technical Notes & Limitations

* **Solar position**: Spencer / NOAA simplified formulas with atmospheric refraction and altitude horizon-dip corrections.
* **Exposure model**: silhouette × incidence cosine (approximating the mutual shading of the two layers), unit m²·h.
* **Friction & slipping**: uniform-mass assumption with the capstan friction model (contact arc π); a 1.3× safety margin by default.
* **Energy estimate**: based on air mass (AM) and direct normal irradiance (DNI), with a sky-clarity factor kc.
* **Known limitations**:
  * Direct sunlight only — diffuse skylight, ground reflection, clouds, wind and humidity are not included (these affect real drying speed on cloudy or cold days).
  * The quilt is idealized as a rigid flat panel; fabric bulging and layer contact are ignored.
  * No obstacles (buildings, trees, balcony railings) are modeled.
  * Results are meant for **comparing schemes, time windows and seasons** — not equal to measured drying time.

---

## 👨‍💻 Credits

Assisted by deepseek-V4.1-Flash (WorkBuddy); requirement design, physics-logic optimization, UI tuning and final testing by the author (Bibipiano).

## 📄 License

Released under the [MIT License](LICENSE).
