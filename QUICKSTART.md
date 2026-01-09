# Quick Start Guide

Get your Puter.js app running in 5 minutes!

## Step 1: Use This Template

1. Click the green **"Use this template"** button at the top of the repository
2. Choose **"Create a new repository"**
3. Give your repository a name (e.g., `my-puter-app`)
4. Make it public or private
5. Click **"Create repository from template"**

## Step 2: Enable GitHub Pages

1. Go to your new repository
2. Click **Settings** (top menu)
3. Click **Pages** (left sidebar)
4. Under **"Source"**, select **"GitHub Actions"**
5. Done! No need to save, it updates automatically

## Step 3: Trigger First Deployment

Your app will auto-deploy when you push to the `main` branch. To trigger the first deployment:

**Option A: Make a small change**
1. Click on `README.md` in your repository
2. Click the pencil icon (✏️) to edit
3. Add your project description
4. Commit directly to `main` branch
5. GitHub Actions will start automatically

**Option B: Push from local**
```bash
git clone https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git
cd YOUR_REPO_NAME
# Make some changes to index.html
git add .
git commit -m "Initial customization"
git push
```

## Step 4: Wait for Deployment

1. Go to the **Actions** tab in your repository
2. Watch the **"Deploy to GitHub Pages"** workflow run
3. Wait for the green checkmark ✓ (usually takes 1-2 minutes)

## Step 5: Visit Your App

Your app will be live at:
```
https://YOUR_USERNAME.github.io/YOUR_REPO_NAME/
```

For example:
- Username: `johndoe`
- Repo: `my-puter-app`
- URL: `https://johndoe.github.io/my-puter-app/`

## Step 6: Customize Your App

Now edit `index.html` to build your application!

### Simple Example: Change the Title

```html
<!-- Find this line in index.html -->
<h1>🚀 Puter.js App Template</h1>

<!-- Change it to: -->
<h1>My Awesome App</h1>
```

### Add Your Own Features

Use Puter.js APIs to add functionality:

```javascript
// AI Chat
const response = await puter.ai.chat('Your prompt here');

// Cloud Storage
await puter.fs.write('myfile.txt', 'Hello World');

// Key-Value Store
await puter.kv.set('mykey', 'myvalue');
const value = await puter.kv.get('mykey');

// Authentication
await puter.auth.signIn();
const user = await puter.auth.getUser();
```

## Troubleshooting

### Deployment Failed?

**Check the Actions tab:**
1. Go to **Actions** in your repository
2. Click on the failed workflow
3. Click on the job to see error details

**Common issues:**
- GitHub Pages not enabled correctly
- Workflow permissions not set
- Branch name mismatch

**Fix permissions:**
1. Go to **Settings** → **Actions** → **General**
2. Scroll to **Workflow permissions**
3. Select **"Read and write permissions"**
4. Check **"Allow GitHub Actions to create and approve pull requests"**
5. Click **Save**

### App Not Loading?

**Check your repository settings:**
1. Ensure GitHub Pages source is set to **"GitHub Actions"**
2. Wait a few minutes after deployment
3. Clear browser cache and try again
4. Check browser console for errors (F12)

### Puter.js Not Working?

**Verify the script is loaded:**
```javascript
// Add this to your HTML to check
window.addEventListener('load', () => {
    if (typeof puter !== 'undefined') {
        console.log('✓ Puter.js loaded');
    } else {
        console.error('✗ Puter.js failed to load');
    }
});
```

## Next Steps

- [ ] Customize `index.html` with your app
- [ ] Update `README.md` with your project info
- [ ] Test Puter.js features locally
- [ ] Deploy and share your app
- [ ] Check out `EXAMPLES.md` for code examples
- [ ] Read the [Puter.js docs](https://docs.puter.com/)

## Need Help?

- 📚 Read [EXAMPLES.md](EXAMPLES.md) for code samples
- 🐛 [Open an issue](https://github.com/ludoplex/puter.js-github-pages-hosted-client-app-template/issues)
- 💬 Check [Puter.js documentation](https://docs.puter.com/)
- 🌟 Star the template if it helped you!

## Tips for Success

1. **Start Small**: Begin with the example code, then build up
2. **Test Locally**: Open `index.html` in your browser before deploying
3. **Use Console**: Open browser DevTools (F12) to debug
4. **Read Errors**: Error messages usually tell you what's wrong
5. **Check Examples**: See `EXAMPLES.md` for working code
6. **Commit Often**: Small, frequent commits are easier to debug

## Resources

- [Puter.js Documentation](https://docs.puter.com/)
- [GitHub Pages Guide](https://docs.github.com/pages)
- [GitHub Actions Docs](https://docs.github.com/actions)
- [HTML/CSS/JS Tutorials](https://developer.mozilla.org/)

---

**Happy building! 🚀**

If you create something cool, please share it with the community!
