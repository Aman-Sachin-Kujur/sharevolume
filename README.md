# SEC Common Stock Shares Outstanding Viewer

This is a single-file HTML web application designed to fetch and display the highest and lowest Common Stock Shares Outstanding for a given U.S. SEC company, based on data available via the SEC EDGAR API.

## Features

*   **Dynamic Data Fetching:** Retrieves `EntityCommonStockSharesOutstanding` data from the SEC EDGAR API.
*   **CIK Support:** Defaults to Cisco (CIK 0000858877) but can be updated via URL query parameters.
*   **Data Filtering:** Filters share outstanding data for fiscal years greater than 2020 and includes valid numeric values.
*   **Min/Max Calculation:** Identifies and displays the highest and lowest shares outstanding within the filtered data, along with their respective fiscal years.
*   **Responsive UI:** Built with Tailwind CSS for a modern, mobile-friendly design.
*   **No Page Reload:** Updates content dynamically without reloading the page when a new CIK is specified in the URL on initial load.
*   **Error Handling:** Displays user-friendly error messages if data fetching or processing fails.

## Usage

To run this application, simply open the `index.html` file in your web browser.

### Default View

By default, the application will load and display data for **Cisco (CIK 0000858877)**.

### Viewing Data for Other Companies

You can view data for other companies by appending a `CIK` query parameter to the URL. The CIK (Central Index Key) is a 10-digit number assigned by the SEC to all entities that submit filings.

**Example:**

To view data for Apple Inc. (CIK 0000320193), open the file like this:

`file:///path/to/your/index.html?CIK=0000320193`

Or if served from a web server:

`http://localhost:8000/index.html?CIK=0000320193`

## Technical Details & Notes

*   **SEC User-Agent:** The application adheres to SEC guidance by including a descriptive `User-Agent` header in its API requests.
*   **CORS Proxy for Dynamic CIKs:** When fetching data for a CIK provided in the URL query parameter, the application attempts to use a CORS proxy (`https://api.allorigins.win/raw?url=`) to bypass potential Cross-Origin Resource Sharing (CORS) restrictions. **Please note:** Public CORS proxies may have usage limits, reliability issues, or might be blocked. For production environments, consider setting up your own dedicated CORS proxy or ensuring your deployment strategy addresses CORS.
*   **"Save data.json" Interpretation:** The prompt requested to "Save `data.json`". In the context of a client-side HTML application, direct saving to the user's filesystem is not typically possible without explicit user interaction (e.g., download prompt). This application processes the data into the specified JSON structure and logs it to the browser's developer console for inspection.
*   **`uid.txt`:** This file was mentioned in the context but is not directly used or referenced by the client-side `index.html` application itself. It is presumed to be an external project file.

## Development

No build steps are required. Simply open `index.html` in a modern web browser.

## License

This project is open-sourced under the MIT License. See the `LICENSE` file for full details.