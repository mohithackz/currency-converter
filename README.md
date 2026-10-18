<div align="center">

# 💱 Currency Converter

### Convert currencies. Understand the rate. Keep it simple.

A lightweight, responsive currency converter built with **HTML5, CSS3, and vanilla JavaScript**.

Convert between supported currencies, view dynamic country flags, and retrieve exchange rates from a public currency API — all directly in your browser, with no build tools required.

<p>
  <a href="https://github.com/mohithackz/currency-converter">
    <img src="https://img.shields.io/badge/GitHub-Repository-181717?style=for-the-badge&logo=github" alt="GitHub repository">
  </a>
  <img src="https://img.shields.io/badge/HTML5-Markup-E34F26?style=for-the-badge&logo=html5&logoColor=white" alt="HTML5">
  <img src="https://img.shields.io/badge/CSS3-Styling-1572B6?style=for-the-badge&logo=css3&logoColor=white" alt="CSS3">
  <img src="https://img.shields.io/badge/JavaScript-Vanilla-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black" alt="JavaScript">
  <a href="https://github.com/mohithackz/currency-converter/blob/main/LICENSE">
    <img src="https://img.shields.io/badge/License-MIT-2ea44f?style=for-the-badge" alt="MIT License">
  </a>
</p>

</div>

---

## 📌 Overview

Currency Converter is a front-end web project that makes currency conversion quick and accessible. Choose a source currency, select the currency you want to convert to, enter an amount, and request the latest rate available from the configured public API.

The project focuses on the fundamentals of web development: **DOM manipulation, event handling, asynchronous JavaScript, API integration, and responsive interface design**.

> **Default conversion:** 🇺🇸 USD → 🇮🇳 INR

## ✨ Highlights

<table>
  <tr>
    <td width="50%">
      <h3>🌍 Multiple currencies</h3>
      Select from the currency codes provided by the project's mapping.
    </td>
    <td width="50%">
      <h3>🏳️ Dynamic flags</h3>
      Flag previews update when the selected currency changes.
    </td>
  </tr>
  <tr>
    <td width="50%">
      <h3>⚡ API-based rates</h3>
      Retrieve exchange-rate data on demand from a public API.
    </td>
    <td width="50%">
      <h3>🧮 Quick conversion</h3>
      Calculate the converted amount and display it to two decimal places.
    </td>
  </tr>
  <tr>
    <td width="50%">
      <h3>📱 Responsive interface</h3>
      A compact converter interface designed for straightforward use.
    </td>
    <td width="50%">
      <h3>🪶 No build step</h3>
      Uses plain HTML, CSS, and JavaScript without a package installation step.
    </td>
  </tr>
</table>

## 🧰 Built With

| Technology / Service | Role in the project |
|---|---|
| **HTML5** | Page structure, inputs, and currency selectors |
| **CSS3** | Layout, spacing, colors, and interface styling |
| **Vanilla JavaScript (ES6+)** | Dropdown population, event handling, API requests, and conversion calculations |
| [Currency API](https://github.com/fawazahmed0/currency-api) | Public exchange-rate data served through jsDelivr |
| [FlagsAPI](https://flagsapi.com/) | Country flag images shown beside currency selectors |
| [Font Awesome](https://fontawesome.com/) | Exchange icon used in the interface |

## 🗂️ Project Structure

```text
currency-converter/
├── index.html      # Main page and converter interface
├── style.css       # Layout and visual styling
├── codes.js        # Currency-to-country/region mapping
├── app.js          # Dropdowns, flags, API calls, and conversion logic
├── LICENSE         # License file (if included in the repository)
└── README.md       # Project documentation
```

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/mohithackz/currency-converter.git
cd currency-converter
```

### 2. Run the project

**Option A — Open directly**

Open `index.html` in a modern browser.

**Option B — Use a local server (recommended)**

If your browser restricts API requests from local files, start a server in the project directory:

```bash
python -m http.server 8000
```

Then visit <http://localhost:8000>.

Alternatively, use the Live Server extension in Visual Studio Code.

### 3. Convert currencies

1. Enter the amount.
2. Choose the source currency.
3. Choose the target currency.
4. Click **Get Exchange Rate**.
5. Read the converted result displayed by the app.

## ⚙️ Under the Hood

### 1. Currency dropdowns

`codes.js` provides the `countryList` mapping used by `app.js` to populate the **From** and **To** selectors. The initial selections are configured as USD and INR.

### 2. Flag synchronization

When a selector changes, the app calls `updateFlag()` and updates the flag image using the corresponding country/region code.

```text
https://flagsapi.com/{countryCode}/flat/64.png
```

A currency code does not always map uniquely to one country, so the displayed flag depends on the mapping included in the project.

### 3. Exchange-rate request

When the user requests a conversion, `app.js` builds a request for the selected source currency:

```text
https://cdn.jsdelivr.net/npm/@fawazahmed0/currency-api@latest/v1/currencies/{source-currency}.json
```

The app reads the rate associated with the target currency and calculates the result.

### 4. Conversion formula

\[
\text{Converted Amount} = \text{Input Amount} \times \text{Exchange Rate}
\]

The result is formatted to two decimal places for display.

## 🔌 External Services

| Service | Used for | Dependency |
|---|---|---|
| Currency API | Exchange-rate data | Internet connection and API availability |
| FlagsAPI | Flag images | Internet connection and image endpoint availability |
| Font Awesome | Interface icon | Depends on how the icon stylesheet is loaded in `index.html` |

This is a client-side project. It does not require a dedicated backend server or database for its core conversion flow.

## ⚠️ Current Limitations

- **Internet access is required** to retrieve rates and load remote flag images.
- **API failures need clear handling.** A network error or missing rate should be handled with a helpful message.
- **Initial exchange-rate text may be static.** Any hardcoded sample rate should not be treated as a live quote.
- **Currency-to-flag mapping is approximate.** Some currencies are used by multiple countries or territories.
- **Rate availability and freshness depend on the external API.** The result may differ from a bank, card provider, or money-transfer service's offered rate.
- **No automated test suite or build pipeline is included** in the basic project.

## 🛣️ Roadmap

Potential next steps to make the application more robust:

- [ ] Add loading feedback while a rate is being fetched.
- [ ] Handle HTTP errors, network failures, and missing currency rates.
- [ ] Validate amounts and support positive decimal values.
- [ ] Add a swap button for reversing the selected currencies.
- [ ] Fetch a valid rate on initial page load instead of showing a hardcoded example.
- [ ] Improve accessibility with explicit labels and meaningful image alternative text.
- [ ] Add tests for conversion calculations and error cases.
- [ ] Add a screenshot or short GIF to the README.

## 🧪 Ideas for Testing

Before extending the project, manually verify:

- [ ] USD → INR returns a result when the API is available.
- [ ] Changing either currency updates the correct flag.
- [ ] Switching the source currency requests the correct endpoint.
- [ ] A missing target rate does not silently display an incorrect result.
- [ ] Empty, invalid, and decimal amounts behave as expected.
- [ ] The layout remains usable on a narrow mobile screen.

## 🔐 Security & Reliability Notes

- No API secret should be placed in front-end JavaScript. Public client-side endpoints are visible to anyone using the browser.
- Treat external API responses as untrusted input and validate the values before calculating or rendering a result.
- Do not use indicative public exchange rates as guaranteed financial quotes.

## 📚 References

- [Currency API — source and documentation](https://github.com/fawazahmed0/currency-api)
- [FlagsAPI](https://flagsapi.com/)
- [Font Awesome](https://fontawesome.com/)
- [MDN: Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API)
- [MDN: JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)

## 🤝 Contributing

Ideas, bug reports, and improvements are welcome. If you want to contribute:

1. Fork the repository.
2. Create a branch for your change.
3. Keep changes focused and test the converter in a browser.
4. Open a pull request explaining what changed and why.

If you add a `CONTRIBUTING.md` file, link it here.

## ⚖️ Disclaimer

Exchange rates are provided for informational purposes and may not match the rates offered by financial institutions or payment providers. This project is intended for learning and general use, not as a source of guaranteed transaction prices.

## 📄 License

The repository should include a `LICENSE` file describing the terms under which the code may be used. If this project is distributed under the MIT License, see [`LICENSE`](LICENSE).

---

<div align="center">

**Built to practise the fundamentals of front-end development.**

If you find the project useful, consider giving the repository a ⭐.

</div>
