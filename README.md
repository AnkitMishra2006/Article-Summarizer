# AI News Summarizer Chrome Extension

[![Chrome Extension](https://img.shields.io/badge/Chrome-Extension-brightgreen.svg)](https://chrome.google.com/webstore)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Version](https://img.shields.io/badge/version-1.0-blue.svg)](https://github.com/AnkitMishra2006/Article-Summarizer)

**AI News Summarizer** is a powerful Chrome extension that intelligently extracts and summarizes article content from any webpage using Google's Gemini AI. Get instant, customizable summaries without leaving your browser.

## 🚀 Features

- **� Smart Text Extraction**: Automatically detects and extracts article content from any webpage
- **� AI-Powered Summarization**: Uses Google Gemini 1.5 Flash for high-quality summaries
- **� Multiple Summary Types**:
  - **Brief**: 2-3 sentence quick summary
  - **Detailed**: Comprehensive overview with all key points
  - **Bullet Points**: 5-7 key insights in easy-to-read format
- **📋 One-Click Copy**: Copy summaries to clipboard instantly
- **⚙️ Easy Configuration**: Simple options page for API key management
- **🎨 Clean Interface**: Intuitive popup design with responsive layout
- **🔒 Secure Storage**: API keys stored securely using Chrome's sync storage

### Extension Popup

The main interface where users select summary type and view results.

### Options Page

Simple configuration page for setting up your Google Gemini API key.

## 🛠️ Installation

### From Source (Developer Mode)

1. **Clone the repository**:

   ```bash
   git clone https://github.com/AnkitMishra2006/Article-Summarizer.git
   cd Article-Summarizer
   ```

2. **Load in Chrome**:

   - Open Chrome and navigate to `chrome://extensions/`
   - Enable **Developer mode** (toggle in top-right corner)
   - Click **Load unpacked** and select the project directory

3. **Configure API Key**:
   - Right-click the extension icon and select "Options"
   - Enter your Google Gemini API key (see [API Setup](#-api-setup) below)
   - Click "Save Settings"

### 🔑 API Setup

1. **Get Google Gemini API Key**:

   - Visit [Google AI Studio](https://makersuite.google.com/app/apikey)
   - Sign in with your Google account
   - Click "Create API Key" and copy the generated key

2. **Configure Extension**:
   - Right-click the extension icon → "Options"
   - Paste your API key in the input field
   - Click "Save Settings"

## 📚 Usage

1. **Navigate to any article** or news webpage
2. **Click the extension icon** in your browser toolbar
3. **Select summary type** from the dropdown:
   - `Brief` - Quick 2-3 sentence overview
   - `Detailed` - Comprehensive summary with all main points
   - `Bullet Points` - Key insights in bulleted list format
4. **Click "Summarize This Page"** and wait for AI processing
5. **Copy the result** using the "Copy Summary" button

### 💡 Tips for Best Results

- Works best on article pages with clear text content
- Ideal for news articles, blog posts, and research papers
- May not work well on heavily JavaScript-rendered content
- Summaries are limited to ~20,000 characters of source text

## 🏗️ Project Structure

```
AI-News-Summarizer/
├── manifest.json          # Extension configuration and permissions
├── popup.html             # Main popup interface HTML
├── popup.js               # Popup logic and API interactions
├── content.js             # Content script for text extraction
├── background.js          # Service worker for extension lifecycle
├── options.html           # Settings page HTML
├── options.js             # Settings page functionality
├── icon.png              # Extension icon
└── README.md             # Project documentation
```

### 📁 File Details

| File            | Purpose                                                        | Key Functions                                       |
| --------------- | -------------------------------------------------------------- | --------------------------------------------------- |
| `manifest.json` | Extension manifest defining permissions, scripts, and metadata | Chrome Extension v3 configuration                   |
| `popup.html`    | User interface for the extension popup                         | Clean, responsive design with dropdown and buttons  |
| `popup.js`      | Main application logic                                         | API calls, text processing, clipboard functionality |
| `content.js`    | Content script injected into web pages                         | Article text extraction using DOM queries           |
| `background.js` | Service worker for background tasks                            | Extension lifecycle management                      |
| `options.html`  | Configuration page for settings                                | API key input form                                  |
| `options.js`    | Settings page functionality                                    | API key storage and validation                      |

## 🔧 Technical Details

### Architecture

- **Manifest V3**: Uses latest Chrome Extension architecture
- **Content Scripts**: Injected into all pages for text extraction
- **Service Worker**: Background script for extension management
- **Chrome APIs**: Storage API for settings, Tabs API for active page access

### API Integration

```javascript
// Example API call structure
const response = await fetch(
  `https://generativelanguage.googleapis.com/v1beta/models/gemini-1.5-flash:generateContent?key=${apiKey}`,
  {
    method: "POST",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify({
      contents: [{ parts: [{ text: prompt }] }],
      generationConfig: { temperature: 0.2 },
    }),
  }
);
```

### Text Extraction Logic

The extension uses intelligent DOM querying to extract article content:

1. **Primary**: Looks for `<article>` tags
2. **Fallback**: Aggregates all `<p>` (paragraph) elements
3. **Processing**: Truncates to 20,000 characters for API efficiency

## 🛡️ Permissions

The extension requires the following permissions:

- `activeTab`: Access current tab content for text extraction
- `scripting`: Inject content scripts for article parsing
- `storage`: Store API keys and user preferences
- `host_permissions`: Access all URLs for universal article support

## 🐛 Troubleshooting

### Common Issues

**"API key not found" error**:

- Ensure you've set your API key in the options page
- Verify the API key is valid and active

**"Could not extract article text"**:

- Page may not have standard article structure
- Try on a different news/article website
- Some heavily JavaScript-rendered sites may not work

**Extension not appearing**:

- Check that Developer mode is enabled
- Verify the extension is loaded and enabled in `chrome://extensions/`

### Debug Mode

Enable Chrome DevTools for the extension:

1. Go to `chrome://extensions/`
2. Find "AI News Summarizer"
3. Click "Details" → "Inspect views: popup"

## 🔮 Future Enhancements

- [ ] **Multiple AI Providers**: Support for OpenAI, Claude, and other LLMs
- [ ] **Custom Prompts**: User-defined summary templates
- [ ] **Summary History**: Save and manage previous summaries
- [ ] **Export Options**: Save summaries as PDF, text, or Markdown
- [ ] **Keyboard Shortcuts**: Quick access hotkeys
- [ ] **Dark Mode**: Theme toggle for better user experience
- [ ] **Language Support**: Multi-language article summarization
- [ ] **Summary Comparison**: Side-by-side different summary types

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

### Development Setup

1. Fork the repository
2. Clone your fork locally
3. Make your changes
4. Test thoroughly with different websites
5. Submit a pull request with clear description

### Guidelines

- Follow existing code style and structure
- Test on multiple website types
- Update documentation for new features
- Ensure backwards compatibility

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **Google Gemini AI**: For providing the powerful summarization capabilities
- **Chrome Extensions Team**: For the excellent extension platform and documentation
- **Open Source Community**: For inspiration and best practices

## 📞 Support

If you encounter any issues or have questions:

- **GitHub Issues**: [Create an issue](https://github.com/AnkitMishra2006/Article-Summarizer/issues)
- **Email**: ankit.kumar.mishra2006@gmail.com
- **Documentation**: Check this README and inline code comments

---

**Made with ❤️ by [Ankit Mishra](https://github.com/AnkitMishra2006)**

_Happy Summarizing! 📚✨_
