# Security Policy

## Supported Versions

We support the latest version of this template. Since this is a template repository, security updates apply to the template itself, not to projects created from it.

| Version | Supported          |
| ------- | ------------------ |
| Latest  | :white_check_mark: |

## Reporting a Vulnerability

We take security seriously. If you discover a security vulnerability in this template, please report it responsibly.

### How to Report

**DO NOT** open a public issue for security vulnerabilities.

Instead, please:

1. **Email**: Send details to the repository maintainer
2. **GitHub Security**: Use GitHub's private vulnerability reporting feature:
   - Go to the repository's **Security** tab
   - Click **"Report a vulnerability"**
   - Fill in the details

### What to Include

Please include:

- Description of the vulnerability
- Steps to reproduce
- Potential impact
- Suggested fix (if you have one)
- Your contact information

### What to Expect

- **Acknowledgment**: We'll acknowledge your report within 48 hours
- **Updates**: We'll keep you informed of our progress
- **Fix Timeline**: We aim to release fixes within 7 days for critical issues
- **Credit**: We'll credit you in the fix announcement (unless you prefer to remain anonymous)

## Security Best Practices for Users

When using this template:

### 1. Keep Dependencies Updated

```bash
# If you add npm packages, keep them updated
npm audit
npm update
```

### 2. Don't Commit Secrets

- Never commit API keys, tokens, or passwords
- Use environment variables for sensitive data
- Review `.gitignore` before committing

### 3. Validate User Input

```javascript
// Always validate and sanitize user input
const input = document.getElementById('userInput').value;
const sanitized = input.replace(/[<>]/g, ''); // Basic example
```

### 4. Use HTTPS

- GitHub Pages provides HTTPS automatically
- Never load external scripts over HTTP

### 5. Be Careful with Puter.js Data

- Remember: Data stored in Puter.js is in the cloud
- Don't store highly sensitive data without additional encryption
- Inform users about data storage and privacy

### 6. Content Security Policy

Consider adding CSP headers to your HTML:

```html
<meta http-equiv="Content-Security-Policy" 
      content="default-src 'self'; script-src 'self' https://js.puter.com; style-src 'self' 'unsafe-inline';">
```

### 7. Regular Audits

- Periodically review your code for security issues
- Check GitHub Security Advisories
- Update the template if new versions are released

## Known Limitations

1. **Client-Side Only**: This template is for client-side apps
2. **Third-Party Dependencies**: Security depends on Puter.js and browser security
3. **GitHub Pages**: Subject to GitHub's security policies

## Security Features

This template includes:

- ✅ No backend = reduced attack surface
- ✅ HTTPS by default on GitHub Pages
- ✅ No server-side code to exploit
- ✅ Minimal dependencies
- ✅ Client-side validation examples

## Questions?

For security questions (non-vulnerabilities), open an issue with the `security` label.

## Attribution

We appreciate responsible disclosure. Contributors who report valid security issues will be:

- Credited in release notes (if desired)
- Listed in security acknowledgments
- Thanked in the community

---

**Last Updated**: 2026-01-09

Thank you for helping keep this template secure! 🔒
