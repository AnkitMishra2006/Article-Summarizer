# AI News Summarizer Chrome Extension

**AI News Summarizer** is a Chrome extension that extracts and summarizes the content of any article you're reading using AI. Choose between brief, detailed, or bullet point summaries directly from your browser.

## Features

- 📄 Extracts article text from any webpage.
- 🧠 Summarizes using AI (via Gemini or any LLM API).
- 🔘 Multiple summary options: brief, detailed, or bullet points.
- 📋 Copy summary to clipboard with one click.
- 🛠️ Simple and clean popup interface.

## Installation

1. Clone or download this repository.
2. Open Chrome and go to `chrome://extensions/`.
3. Enable **Developer mode** in the top right.
4. Click **Load unpacked** and select the project directory.
5. On first install, you'll be prompted to enter your API key via `options.html`.

## File Structure

- `manifest.json` - Extension manifest and permissions.
- `popup.html` - UI for interacting with the extension.
- `popup.js` - Handles popup interactions and Chrome API calls.
- `content.js` - Extracts article text from the current page.
- `background.js` - Handles initial setup and API key storage.
- `options.html` - Lets users enter and store their API key.
- `options.js` - Handles click Events in options.html

## How It Works

1. User clicks the extension icon.
2. The popup loads with options for summary type.
3. When "Summarize This Page" is clicked:
   - It grabs article text from the current tab using `content.js`.
   - Sends the text to your AI API for summarization.
   - Displays the summarized result in the popup.

## License

MIT License
