# Currency Converter

A lightweight, browser-based currency converter built with **HTML, CSS, and JavaScript**. Select a source and target currency, enter an amount, and fetch an exchange rate from a public currency API.

## Features

- Convert between a broad range of currency codes.
- Choose source and target currencies from dropdown menus.
- Display a country flag beside each currency selector.
- Fetch exchange-rate data when the **Get Exchange Rate** button is clicked.
- Show the converted amount rounded to two decimal places.
- Use **USD → INR** as the default currency pair.

## Tech Stack

- **HTML5** — page structure and form controls
- **CSS3** — layout and styling
- **Vanilla JavaScript** — dropdown population, flag updates, API requests, and conversion logic
- **Currency API** — exchange-rate data from `@fawazahmed0/currency-api`
- **Flags API** — flag images from `flagsapi.com`
- **Font Awesome** — exchange icon

## Project Structure

```text
currency-converter/
├── index.html   # Main page and converter form
├── style.css    # Layout, colors, and component styling
├── codes.js     # Currency-code to country/region-code mapping
└── app.js       # Dropdown setup, flag updates, and conversion logic
```

## Getting Started

No package installation or build step is required.

1. Download or clone this repository.
2. Keep `index.html`, `style.css`, `codes.js`, and `app.js` in the same directory.
3. Open `index.html` in a modern browser.
4. Enter an amount, select the **From** and **To** currencies, and click **Get Exchange Rate**.

If your browser restricts requests when opening a local file, serve the folder with a simple local web server instead. For example, if Python is installed, run this command from the project directory:

```bash
python -m http.server 8000
```

Then open <http://localhost:8000> in your browser.

## How It Works

1. `codes.js` defines `countryList`, mapping currency codes to country or region codes used to display flags.
2. `app.js` reads that mapping and dynamically fills both currency dropdowns.
3. The default selections are USD for the source currency and INR for the target currency.
4. When a currency selection changes, `updateFlag()` updates the associated flag image.
5. When the form button is clicked, the app requests the selected source currency's data from the currency API.
6. It reads the rate for the selected target currency, multiplies it by the entered amount, rounds the result to two decimal places, and displays the conversion.

The exchange-rate endpoint is built from the selected source currency:

```text
https://cdn.jsdelivr.net/npm/@fawazahmed0/currency-api@latest/v1/currencies/<source-currency>.json
```

For example, selecting USD as the source requests the USD rates and then reads the INR rate if INR is selected as the target.

## Current Limitations

- **Network required:** exchange rates and flag images are loaded from external services.
- **No request error handling yet:** if the API is unavailable, the request fails, or a currency rate is missing, the app may not show a useful error message.
- **Input validation is basic:** empty amounts and values below `1` are reset to `1`; this also prevents converting zero or negative amounts.
- **Currency/region mapping is approximate:** `codes.js` maps each currency to a flag code, but some currencies are shared by multiple countries or use special regional codes. A currency code is not always a one-to-one match for a country.
- **Initial result text is static:** the message in `index.html` (`1 USD = 91.61 INR`) is placeholder text and may not match the current exchange rate until a conversion is performed.
- **No automated tests or build tooling are included** in the supplied project.

## Possible Improvements

- Add `try...catch` and check `response.ok` before parsing API responses.
- Validate that the amount is a finite positive number and clearly explain invalid input.
- Handle missing currency rates and network errors with user-friendly messages.
- Update the result when either currency changes, or add a swap-currencies button.
- Replace the static initial result with a neutral prompt or fetch a rate on page load.
- Add accessibility improvements, including descriptive labels for inputs and flag images.
- Add tests for conversion calculations, input validation, and API failure scenarios.

## API and Attribution

- Exchange-rate data: [`@fawazahmed0/currency-api`](https://github.com/fawazahmed0/currency-api)
- Flag images: [FlagsAPI](https://flagsapi.com/)
- Icons: [Font Awesome](https://fontawesome.com/)

These external services have their own availability, terms, and data-update behavior. Exchange rates can differ from the rates offered by banks, card networks, or money-transfer services, and should not be treated as guaranteed transaction quotes.

## License

No license file was included with the supplied project. Add a `LICENSE` file before presenting the repository as open source, and choose a license that matches how you want others to use the code.
