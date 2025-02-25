# Spotify Referral Code

This project is a simple web application for distributing **Spotify audiobook redemption codes** to users. It allows an administrator or content creator to share unique codes that give a free copy of an audiobook on Spotify ([Redemption codes - Spotify](https://support.spotify.com/us/authors/article/redemption-codes/#:~:text=Share%20redemption%20codes%20with%20your,free%20copy%20of%20your%20audiobook)). Users can visit the web page to instantly obtain a code and are provided with a direct link to Spotify's official redemption site ([Redemption codes - Spotify](https://support.spotify.com/us/authors/article/redemption-codes/#:~:text=Listeners%20can%20redeem%20codes%20at,direct.com%2Fspotify)) to redeem their audiobook. The tool fetches codes from a dedicated backend service (ensuring each code is only used once) and presents them with a user-friendly interface.

## Features

- **Automatic Code Fetching:** On page load, the application automatically requests a new Spotify redemption code from the backend API.
- **Code Display with Link:** The retrieved code is displayed prominently and is hyperlinked to the official Spotify redemption page (opens in a new tab with the code pre-filled for redemption).
- **One-Click Copy:** A **Copy Code** button lets users copy the code to their clipboard with one click, for easy manual redemption if needed.
- **Out-of-Codes Alert:** If no codes remain in the system, the interface shows a clear alert message *("No more codes available")* instead of an empty result, informing the user that no codes are left.
- **Responsive UI:** The page uses Bootstrap 5 for styling, ensuring a clean and responsive design that works on desktop and mobile browsers.

## Installation

1. **Clone the repository:** Clone this repository to your local machine using Git:  
   ```bash
   git clone https://github.com/pantoner/spotify.git
   ```  
   Alternatively, you can download the ZIP of the repository and extract it.
2. **Open the project directory:** Navigate to the cloned project folder. You should see an `index.html` file (and possibly other assets if added in the future).
3. **Serve the page (recommended):** For the code fetching to work properly, it's best to serve the page over HTTP. You can use a simple static server. For example, run:  
   ```bash
   python3 -m http.server 8000
   ```  
   in the project directory, then open `http://localhost:8000/index.html` in your web browser.
4. **Or open directly:** You can also simply open the `index.html` file in your browser by double-clicking it. (Note: in some cases, browsers may block the fetch request when using the file:// protocol for security. Using a local server as in step 3 avoids this issue.)
5. **Ensure connectivity:** Make sure your computer is connected to the internet. The app needs internet access to request the Spotify code from the backend service.

## Usage

- **Opening the app:** Once the page is served (or opened) in a browser, it will automatically trigger a request to fetch a new code from the server. You don't need to click anything to load the code – the process starts on page load.
- **Getting a code:** If a code is available, it will be displayed on the page in large text. The code itself appears as a clickable link. You can:
  - Click on the code to open the Spotify redemption website in a new tab with the code pre-filled (via the URL query parameter).
  - Or click the **Copy Code** button below the code to copy it to your clipboard. You can then manually navigate to the redemption site and paste the code if you prefer.
- **Redeeming the code:** The redemption happens on Spotify’s official site. By clicking the provided link (or by visiting [authors-direct.com/spotify](https://authors-direct.com/spotify) and entering the code manually), you will be guided to log into your Spotify account and confirm the audiobook redemption. Once redeemed, the audiobook will be added to your Spotify library/account (subject to Spotify’s terms).
- **No codes available:** If the backend has run out of codes, the page will display a red alert box stating "No more codes available" instead of a code. In this case, no further codes can be retrieved until the backend's code supply is refreshed.

## Configuration

- **Backend API Endpoint:** By default, the frontend is configured to fetch codes from a specific URL (`https://spotback.onrender.com/get-code`). If you want to use your own backend service or a different endpoint, you will need to modify this URL in the `index.html` file. Look for the JavaScript function `fetchCode()` – the fetch call URL can be changed to your endpoint of choice.
- **Backend Response Format:** Ensure your backend returns a JSON response in the format this app expects. The code assumes the response will be either an object with a `code` field (e.g. `{"code": "ABCDE12345"}`) or an object with an `error` field if no code is available (e.g. `{"error": "none available"}`). Adjust the frontend logic if your API uses a different response structure.
- **CORS Configuration:** If you deploy your own backend, make sure to enable CORS for the domain where this page will be hosted or for local testing. The default backend (`spotback.onrender.com`) is presumably configured to allow requests from the GitHub Pages or other hosting used for this project. If using a different backend, you might need to allow `http://localhost` (for local testing) or your domain in the backend's CORS settings.
- **UI Customization:** You can change visible text (like the heading or alert message) or styling by editing the HTML file. For example, the main heading "Your Spotify Referral Code" in the page can be changed in the HTML, and Bootstrap classes can be adjusted if you want to tweak the appearance.

## Contributing

Contributions are welcome! If you'd like to improve this project or fix an issue, please follow these guidelines:

- **Bug Reports & Feature Requests:** Open an issue on this repository to report a bug or suggest a new feature. Provide as much detail as possible, including steps to reproduce bugs or the use-case for new features.
- **Pull Requests:** If you want to contribute code, you can fork the repository, create a new branch for your changes, and submit a pull request. Please ensure your code is clean and that you have tested your changes. If your contribution is significant, consider opening an issue first to discuss the idea with the maintainer.
- **Consistency:** Try to follow the coding style present in the project (HTML/JS formatting) and maintain clarity in comments or documentation. For any UI changes, keep the design simple and user-friendly consistent with the current look.
- **Community Conduct:** Be respectful and constructive in communications. Ensure contributions do not include any sensitive information or break any of Spotify's terms of service.

## License

*(No license information is provided in this repository.)* This project has no explicit license at the moment. That means by default all rights are reserved to the author. If you wish to use or adapt this project, please contact the author/maintainer for permission. In the future, a license may be added to clarify usage rights.

*If a LICENSE file is added to the project later, that license will determine how the code can be used or contributed to. Always check the repository for the latest licensing information.*

## Contact

For questions, support, or to report an issue, you can reach out through the following channels:

- **GitHub Issues:** The quickest way to get help or report a problem is to open an issue on this repository. The maintainer will respond as soon as possible.
- **Email:** You may contact the project maintainer via the email address listed on their GitHub profile. (Visit the [GitHub profile of pantoner](https://github.com/pantoner) and find the email contact if available.)
- **LinkedIn:** The project creator, *Erich Orozco*, can also be contacted through LinkedIn. Feel free to connect or send a message via [Erich Orozco on LinkedIn](https://www.linkedin.com/in/erich-orozco/).

Please include relevant details when reaching out (for example, screenshots of an issue or clarification of a request) to help address your query more effectively. Thank you for using and contributing to **Spotify Referral Code**! ([Redemption codes - Spotify](https://support.spotify.com/us/authors/article/redemption-codes/#:~:text=Share%20redemption%20codes%20with%20your,free%20copy%20of%20your%20audiobook))
