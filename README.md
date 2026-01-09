# 🚀 Puter.js GitHub Pages Template

A ready-to-deploy template for building **serverless, cloud-powered applications** using [Puter.js](https://puter.com) and GitHub Pages. No backend required!

[![Deploy to GitHub Pages](https://github.com/ludoplex/puter.js-github-pages-hosted-client-app-template/actions/workflows/deploy.yml/badge.svg)](https://github.com/ludoplex/puter.js-github-pages-hosted-client-app-template/actions/workflows/deploy.yml)
[![CI](https://github.com/ludoplex/puter.js-github-pages-hosted-client-app-template/actions/workflows/ci.yml/badge.svg)](https://github.com/ludoplex/puter.js-github-pages-hosted-client-app-template/actions/workflows/ci.yml)
[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)

## ✨ What is This?

This template provides everything you need to create and deploy single-file Puter.js applications to GitHub Pages with zero configuration. It includes:

- 📄 Pre-configured `index.html` with Puter.js integration
- 🔄 Automated GitHub Pages deployment workflow
- ✅ CI/CD pipeline for validation
- 🎉 Automatic milestone promotion system (100, 1K, 10K, 100K+ stars)
- 📚 Comprehensive documentation and examples

## 🎯 Features Powered by Puter.js

- **☁️ Cloud Storage** - Access a secure file system in the browser
- **🤖 AI Integration** - ChatGPT, Claude, Gemini, and more built-in
- **🔐 Authentication** - User auth without backend code
- **💾 Database** - NoSQL key-value store
- **🌐 Networking** - Raw TCP, TLS, HTTP support
- **📦 Completely Serverless** - Runs entirely in the browser
- **🔒 Privacy-First** - No tracking, no data mining

## 🚀 Quick Start

### Option 1: Use This Template (Recommended)

1. Click the **"Use this template"** button at the top of this repository
2. Name your new repository
3. Clone your new repository:
   ```bash
   git clone https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git
   cd YOUR_REPO_NAME
   ```
4. Enable GitHub Pages:
   - Go to your repository **Settings** → **Pages**
   - Under "Source", select **GitHub Actions**
5. Push to `main` branch - your app will auto-deploy! 🎉

### Option 2: Manual Setup

1. Create a new repository on GitHub
2. Copy `index.html` from this template
3. Copy `.github/workflows/` directory
4. Push and enable GitHub Pages (see above)

## 📝 Customization

### Modify index.html

Edit `index.html` to build your application:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <script src="https://js.puter.com/v2/"></script>
</head>
<body>
    <h1>My Puter.js App</h1>
    <script>
        // Your application code here
        puter.ai.chat('Hello!').then(response => {
            console.log(response);
        });
    </script>
</body>
</html>
```

### Available Puter.js APIs

```javascript
// Cloud Storage
await puter.fs.write('file.txt', 'content');
await puter.fs.read('file.txt');

// AI Chat
const response = await puter.ai.chat('Your prompt');

// Key-Value Store
await puter.kv.set('key', 'value');
const value = await puter.kv.get('key');

// Authentication
const user = await puter.auth.getUser();
await puter.auth.signIn();

// Web Hosting
const site = await puter.hosting.create('mysite', 'directory');
```

## 🔧 GitHub Actions Workflows

### 1. Deploy to GitHub Pages (`deploy.yml`)

**Trigger**: Push to `main` branch or manual trigger

Automatically deploys your `index.html` to GitHub Pages.

### 2. Continuous Integration (`ci.yml`)

**Trigger**: Push or Pull Request

Validates:
- HTML syntax
- Puter.js script presence
- README existence

### 3. Star Milestone Promotion (`milestone-promotion.yml`)

**Trigger**: Daily check or when starred

When your project reaches 100, 1K, 10K, or 100K stars:
- Creates a celebration issue
- Promotes the template repository
- Acknowledges your community

This helps spread awareness of Puter.js and this template! 🌟

## 📖 Examples

### Simple AI Chatbot

```html
<button onclick="chat()">Ask AI</button>
<div id="response"></div>

<script>
async function chat() {
    const answer = await puter.ai.chat('Tell me a joke');
    document.getElementById('response').textContent = answer;
}
</script>
```

### Cloud File Storage

```html
<input type="file" id="fileInput">
<button onclick="uploadFile()">Upload</button>

<script>
async function uploadFile() {
    const file = document.getElementById('fileInput').files[0];
    await puter.fs.write(file.name, file);
    alert('File uploaded!');
}
</script>
```

### User Authentication

```html
<button onclick="login()">Sign In</button>
<div id="user"></div>

<script>
async function login() {
    await puter.auth.signIn();
    const user = await puter.auth.getUser();
    document.getElementById('user').textContent = `Welcome, ${user.username}!`;
}
</script>
```

## 🛠️ Local Development

Simply open `index.html` in your browser:

```bash
# Option 1: Direct open
open index.html

# Option 2: Local server (optional)
python -m http.server 8000
# or
npx serve .
```

Visit `http://localhost:8000` in your browser.

## 🎨 Customization Ideas

- **Productivity Apps**: Todo lists, note-taking, project management
- **AI Tools**: Chatbots, content generators, image analysis
- **Creative Apps**: Drawing tools, music makers, design utilities
- **Games**: Browser-based games with cloud save
- **Developer Tools**: Code editors, API testers, documentation sites
- **Social Apps**: Chat applications, collaborative tools

## 📚 Documentation & Resources

- **Puter.js Docs**: https://docs.puter.com/
- **Puter.js GitHub**: https://github.com/HeyPuter/puter
- **GitHub Pages Guide**: https://docs.github.com/pages
- **GitHub Actions Docs**: https://docs.github.com/actions

## 🤝 Contributing

Contributions are welcome! Feel free to:

- 🐛 Report bugs
- 💡 Suggest features
- 🔧 Submit pull requests
- 📖 Improve documentation

## 💖 Support & Community

If this template helps you build something awesome:

1. ⭐ Star this repository
2. 🔄 Share it with others
3. 🐦 Tweet about your project
4. 💬 Join the [Puter community](https://puter.com)

## 📋 Checklist for Your Project

After using this template:

- [ ] Update README.md with your project description
- [ ] Customize index.html for your application
- [ ] Test locally before deploying
- [ ] Enable GitHub Pages in repository settings
- [ ] Add your own branding and styling
- [ ] Update meta tags (title, description, etc.)
- [ ] Add a favicon
- [ ] Test Puter.js features you're using
- [ ] Share your project!

## 📄 License

This template is licensed under the GNU General Public License v3.0. See [LICENSE](LICENSE) for details.

## 🌟 Projects Using This Template

Built something cool? Open a PR to add your project here!

- *Your project could be here!*

---

**Made with ❤️ using [Puter.js](https://puter.com)**

*Template by [ludoplex](https://github.com/ludoplex)*