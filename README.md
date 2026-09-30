# 🚀 GitHub Explorer

A feature-rich, responsive web application that allows users to seamlessly search, discover, and inspect GitHub profiles, public repositories, commit activity, and contribution metrics using the GitHub REST API.

🌐 **Live Demo:** [karonieehash.github.io/github-exporer](https://karonieehash.github.io/github-exporer/)

---

## 📑 Table of Contents

* [Overview](https://www.google.com/search?q=%23-overview)
* [Key Features](https://www.google.com/search?q=%23-key-features)
* [Tech Stack](https://www.google.com/search?q=%23-tech-stack)
* [Architecture & Design](https://www.google.com/search?q=%23-architecture--design)
* [Getting Started](https://www.google.com/search?q=%23-getting-started)
* [Prerequisites](https://www.google.com/search?q=%23prerequisites)
* [Installation](https://www.google.com/search?q=%23installation)
* [Environment Variables & API Token Setup](https://www.google.com/search?q=%23environment-variables--api-token-setup)


* [Usage Guide](https://www.google.com/search?q=%23-usage-guide)
* [API Rate Limits & Authentication](https://www.google.com/search?q=%23-api-rate-limits--authentication)
* [Folder Structure](https://www.google.com/search?q=%23-folder-structure)
* [Customization & Styling](https://www.google.com/search?q=%23-customization--styling)
* [Roadmap](https://www.google.com/search?q=%23-roadmap)
* [Contributing](https://www.google.com/search?q=%23-contributing)
* [License](https://www.google.com/search?q=%23-license)
* [Author & Acknowledgments](https://www.google.com/search?q=%23-author--acknowledgments)

---

## 🔍 Overview

**GitHub Explorer** is built to provide developers, recruiters, and tech enthusiasts with an effortless way to navigate through GitHub user statistics, public repositories, primary languages used, and community engagement. By tapping directly into the official GitHub REST API, the application fetches real-time metadata and transforms raw JSON payloads into clean, actionable dashboards.

---

## ✨ Key Features

* 👤 **Instant Profile Search:** Find any valid GitHub user instantly using real-time search queries.
* 📊 **Detailed Metrics:** View follower counts, following stats, public repository count, bio, and location details.
* 📂 **Repository Insights:** Display public repositories sorted by recent activity, stars, or forks.
* 🎨 **Language Visualizations:** Highlight primary programming languages used across public projects.
* ⚡ **Optimized Performance:** Minimal external dependencies for fast page load times and efficient DOM rendering.
* 📱 **Fully Responsive:** Styled using modern CSS flexbox/grid for mobile, tablet, and desktop viewports.
* 🔒 **Graceful Error Handling:** Provides clear user feedback for non-existent profiles, rate limit breaches, or network failures.

---

## 🛠️ Tech Stack

| Layer | Technology | Description |
| --- | --- | --- |
| **Frontend** | HTML5, CSS3, JavaScript (ES6+) | Core layout, responsive styling, dynamic DOM updates |
| **API Interface** | GitHub REST API v3 | Fetches user, repository, and organization metrics |
| **Hosting & CI/CD** | GitHub Pages | Automated continuous deployment via GitHub repository |

---

## 📐 Architecture & Design

```
+------------------+         +-----------------------+         +--------------------+
|                  |  HTTP   |                       |  JSON   |                    |
|   User Browser   | ------> |  GitHub Explorer App  | ------> |  GitHub REST API   |
|  (User Interface)| <------ |  (DOM & JS Processing)| <------ | (api.github.com)   |
|                  | Render  |                       | Data    |                    |
+------------------+         +-----------------------+         +--------------------+

```

---

## 🚀 Getting Started

Follow these step-by-step instructions to get a local copy of GitHub Explorer up and running on your development machine.

### Prerequisites

* A modern web browser (Google Chrome, Mozilla Firefox, Brave, Microsoft Edge, or Safari).
* A code editor (e.g., [VS Code](https://www.google.com/search?q=https://code.visualstudio.com/)).
* *(Optional)* [Node.js](https://www.google.com/search?q=https://nodejs.org/) installed if you prefer running a local HTTP server using `npx serve` or `live-server`.

### Installation

1. **Clone the repository:**
```bash
git clone https://github.com/karonieehash/github-exporer.git

```


2. **Navigate into the project directory:**
```bash
cd github-exporer

```


3. **Launch the app locally:**
* **Method A:** Double-click `index.html` to open it directly in your preferred web browser.
* **Method B (Recommended):** Use VS Code's **Live Server** extension, or run a quick local web server:
```bash
npx serve .

```





---

### Environment Variables & API Token Setup

By default, unauthenticated requests to the GitHub REST API are limited to **60 requests per hour per IP address**. To increase this limit to **5,000 requests per hour**, you can attach a GitHub Personal Access Token (PAT).

1. **Generate a Token:**
* Go to your GitHub account **Settings** > **Developer Settings** > **Personal Access Tokens** > **Tokens (classic)**.
* Click **Generate new token**.
* Select minimal read-only permissions (or no scopes for basic public data).
* Copy your generated token.


2. **Attach Token to API Requests:**
Include the token in your fetch header inside your JavaScript application file:
```javascript
const GITHUB_TOKEN = "your_personal_access_token_here";

async function fetchGitHubUser(username) {
  const response = await fetch(`https://api.github.com/users/${username}`, {
    headers: {
      Authorization: `Bearer ${GITHUB_TOKEN}`,
      Accept: "application/vnd.github.v3+json"
    }
  });
  return await response.json();
}

```



> ⚠️ **Warning:** Never commit personal access tokens directly into public repositories. Use environment variables or local secret management if expanding this into a server-side app.

---

## 💡 Usage Guide

1. Open the application in your browser or access the [Live Demo](https://karonieehash.github.io/github-exporer/).
2. Enter a GitHub username (e.g., `torvalds` or `karonieehash`) into the search field.
3. Press **Enter** or click the **Search** button.
4. Explore user bio details, top public repositories, star counts, primary languages, and profile links.

---

## 📊 API Rate Limits & Authentication

| Request Type | Rate Limit | Header Required |
| --- | --- | --- |
| **Unauthenticated** | 60 requests / hour | Standard `fetch` |
| **Authenticated (PAT)** | 5,000 requests / hour | `Authorization: Bearer <TOKEN>` |

When the rate limit is exceeded, the API returns a `403 Forbidden` response. The app detects this state and prompts the user to wait or supply an authenticated header.

---

## 📁 Folder Structure

```
github-exporer/
├── index.html          # Main HTML markup and UI structure
├── assets/
│   ├── css/
│   │   ├── style.css   # Main stylesheet & responsive layout rules
│   │   └── theme.css   # Theme variables (colors, fonts, layout spacing)
│   ├── js/
│   │   ├── api.js      # GitHub REST API fetch utilities
│   │   ├── ui.js       # DOM rendering functions
│   │   └── app.js      # Main event handlers and application entry point
│   └── images/
│       ├── logo.png    # Application logo
│       └── favicon.ico # Site favicon
├── README.md           # Documentation
└── LICENSE             # Software license details

```

---

## 🎨 Customization & Styling

The interface utilizes CSS Custom Properties (Variables) located in `assets/css/theme.css` to allow easy customization of colors, typography, and card layouts:

```css
:root {
  --primary-color: #0969da;
  --bg-color: #0d1117;
  --card-bg: #161b22;
  --text-main: #c9d1d9;
  --text-muted: #8b949e;
  --border-color: #30363d;
  --font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
}

```

Feel free to tweak these variables to switch between Dark Mode, Light Mode, or custom branding accents.

---

## 🗺️ Roadmap

* [ ] Add dark / light mode toggle switch.
* [ ] Implement pagination for user repositories.
* [ ] Add interactive charts for programming language statistics (Chart.js integration).
* [ ] Enable profile comparison tool (side-by-side comparison of two developers).
* [ ] Add PDF export for generated user profile cards.

---

## 🤝 Contributing

Contributions are welcome! If you'd like to improve **GitHub Explorer**:

1. **Fork** the repository.
2. **Create** a new branch (`git checkout -b feature/AmazingFeature`).
3. **Commit** your changes (`git commit -m 'Add some AmazingFeature'`).
4. **Push** to the branch (`git push origin feature/AmazingFeature`).
5. Open a **Pull Request**.

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](https://www.google.com/search?q=LICENSE) file for full details.

---

## 👨‍💻 Author & Acknowledgments

**Karoniee Hash**

* GitHub: [@karonieehash](https://www.google.com/search?q=https://github.com/karonieehash)
* Project Repository: [karonieehash/github-exporer](https://www.google.com/search?q=https://github.com/karonieehash/github-exporer)

Special thanks to **GitHub** for providing public access to the REST API data.
