# 💱 Currency Converter

A fast, lightweight, and responsive browser-based currency converter built with pure HTML5, CSS3, and vanilla JavaScript. Quickly convert between over 150 global currencies with live exchange rates and dynamic country flag previews.

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![HTML5](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/HTML)
[![CSS3](https://img.shields.io/badge/CSS3-1572B6?logo=css3&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/CSS)
[![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?logo=javascript&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)

---

## ✨ Features

- **🌐 Broad Currency Coverage:** Supports 150+ currencies across global countries and territories.
- **🏳️ Dynamic Flag Indicators:** Automatically updates country flag icons beside each currency dropdown using FlagsAPI.
- **⚡ Real-Time Rates:** Fetches fresh exchange rate data on demand from the open-source Currency API.
- **🎯 Precise Calculations:** Converts amounts accurately and formats values rounded to two decimal places.
- **🚀 Zero Build Tools / Zero Dependencies:** Runs out of the box in any modern browser without npm packages, Node.js, or complex bundlers.
- **📱 Clean & Centered Interface:** Minimalist card layout with smooth inputs and intuitive selectors.

---

## 🛠️ Tech Stack & Services

| Technology / Service | Purpose |
| :--- | :--- |
| **HTML5** | Semantic structure, form controls, and dropdown elements |
| **CSS3** | Modern flexbox layout, rounded containers, and custom form styling |
| **Vanilla JavaScript (ES6+)** | Dynamic DOM population, asynchronous rate fetching, and conversion logic |
| **[Currency API](https://github.com/fawazahmed0/currency-api)** | Real-time exchange rate endpoints delivered via jsDelivr CDN |
| **[FlagsAPI](https://flagsapi.com/)** | High-definition country flag images (flat 64px) |
| **[Font Awesome](https://fontawesome.com/)** | Vector currency exchange icon |

---

## 📁 Project Structure

```text
currency-converter/
├── index.html     # Main markup, input forms, and container layout
├── style.css      # Styling, layout, color scheme, and responsive elements
├── codes.js       # Mapping object linking 3-letter currency codes to 2-letter country codes
├── app.js         # Dropdown population, flag sync, event listeners, and API fetch logic
├── LICENSE        # MIT open-source license
└── README.md      # Project documentation and setup guide
```

---

## 🚀 Getting Started

No build step or package installations are required!

### Option 1: Direct Browser Launch
1. Clone or download this repository:
   ```bash
   git clone https://github.com/your-username/currency-converter.git
   ```
2. Open the project folder and double-click `index.html` to view it in any modern web browser (Chrome, Firefox, Safari, Edge).

### Option 2: Local HTTP Server (Recommended)
Some browsers restrict cross-origin requests when loading files directly via the `file://` protocol. Running a local HTTP server ensures smooth API requests:

- **Using Python 3:**
  ```bash
  python -m http.server 8000
  ```
  Then open [http://localhost:8000](http://localhost:8000) in your browser.

- **Using Node.js (`npx serve`):**
  ```bash
  npx serve .
  ```

- **Using VS Code Live Server:**
  Right-click `index.html` in VS Code and select **"Open with Live Server"**.

---

## ⚙️ How It Works

1. **Populating Currency Selectors (`codes.js` & `app.js`):**
   - `codes.js` contains `countryList`, an object mapping currency codes (e.g., `USD`, `EUR`, `INR`) to 2-letter ISO country codes (e.g., `US`, `FR`, `IN`).
   - `app.js` loops through this list to populate `<select>` dropdowns for both the source ("From") and target ("To") currencies, defaulting to **USD → INR**.

2. **Flag Synchronization (`updateFlag`):**
   - Whenever a user selects a different currency, the `change` event triggers `updateFlag()`.
   - The flag image URL updates to `https://flagsapi.com/{countryCode}/flat/64.png`.

3. **Fetching Exchange Rates & Calculating:**
   - Clicking **"Get Exchange Rate"** sends an asynchronous `fetch()` request to:
     ```text
     https://cdn.jsdelivr.net/npm/@fawazahmed0/currency-api@latest/v1/currencies/{source-currency}.json
     ```
   - The app extracts the target currency rate from the returned JSON payload:
     $$\text{Final Amount} = \text{Amount} \times \text{Rate}$$
   - The converted result is rounded to two decimal places and rendered in the `.msg` container.

---

## 💡 Recommended Enhancements

If you're looking to extend or improve this project, here are the most impactful upgrades:

- [ ] **Interactive Swap Button:** Enable clicking the `<i class="fa-solid fa-arrow-right-arrow-left"></i>` icon to swap the "From" and "To" currencies and instantly update both flags.
- [ ] **Error Handling & Loading States:**
  - Wrap API requests in `try...catch` and inspect `response.ok`.
  - Display user-friendly notices for network errors or offline states.
  - Show a loading spinner or disable the button while fetching.
- [ ] **Auto-Fetch on Initial Page Load:**
  - Replace the static placeholder (`1 USD = 91.61 INR`) by triggering an initial conversion when the page loads.
- [ ] **Support Fractional & Decimal Amounts:**
  - Update validation to allow positive decimals (e.g., `0.50` or `10.75`) rather than resetting amounts below `1` to `1`.
- [ ] **Live Real-Time Conversion:**
  - Automatically recalculate the rate when changing currency selections or typing in the amount box (with debounce).
- [ ] **Accessibility (a11y) & Mobile Optimization:**
  - Add descriptive `alt` tags to flag images and `<label>` elements for inputs.
  - Adjust `.container` width with responsive CSS units (`clamp()` or `min(90vw, 380px)`) for better mobile display.

---

## ⚖️ API & Attribution

- **Exchange Rate API:** Powered by [@fawazahmed0/currency-api](https://github.com/fawazahmed0/currency-api).
- **Flag Icons:** Provided by [FlagsAPI](https://flagsapi.com/).
- **Vector Icons:** Provided by [Font Awesome](https://fontawesome.com/).

> **Disclaimer:** Exchange rates provided by public APIs are indicative and intended for informational purposes only. Do not rely on them for mission-critical financial transactions.

---

## 📄 License

This project is licensed under the [MIT License](LICENSE) — you are free to use, modify, and distribute this software for personal and commercial projects.
