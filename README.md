# puter.js-github-pages-hosted-client-app-template

A GitHub template repository for deploying single-file, client-side "serverless" [Puter.js](https://docs.puter.com/) apps to GitHub Pages.

## What is Puter.js?

Puter.js is a JavaScript library that brings free, serverless cloud storage, AI capabilities (GPT, Claude, Gemini), authentication, NoSQL databases, and web hosting directly to your frontend JavaScript applications—without requiring any backend code, API keys, or registration.

## Getting Started

1. Click the "Use this template" button to create a new repository from this template
2. Enable GitHub Pages in your repository settings (Settings → Pages → Source: GitHub Actions)
3. Edit `index.html` with your Puter.js app code
4. Push your changes and your app will be deployed automatically!

## Example Usage

```html
<script src="https://js.puter.com/v2/"></script>
<script>
  // Write to cloud storage
  puter.fs.write('hello.txt', 'Hello, world!').then(file => {
    puter.print(`File written at: ${file.path}`);
  });

  // Use AI to chat with models
  puter.ai.chat("Explain quantum computing").then(puter.print);
</script>
```

## Community Showcase

The following projects were created using this template. They are automatically updated daily based on their star counts.

<!-- STARS_100000_START -->
### 🌟 100,000+ Stars

*No projects yet. Be the first to reach this milestone!*

<!-- STARS_100000_END -->

<!-- STARS_10000_START -->
### ⭐ 10,000+ Stars

*No projects yet. Be the first to reach this milestone!*

<!-- STARS_10000_END -->

<!-- STARS_1000_START -->
### ✨ 1,000+ Stars

*No projects yet. Be the first to reach this milestone!*

<!-- STARS_1000_END -->

<!-- STARS_100_START -->
### 💫 100+ Stars

*No projects yet. Be the first to reach this milestone!*

<!-- STARS_100_END -->

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.