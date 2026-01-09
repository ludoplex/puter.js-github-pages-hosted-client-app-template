# Contributing to Puter.js GitHub Pages Template

Thank you for your interest in contributing! This document provides guidelines for contributing to this template.

## How to Contribute

### Reporting Issues

If you find a bug or have a suggestion:

1. Check if the issue already exists
2. Create a new issue with:
   - Clear title and description
   - Steps to reproduce (for bugs)
   - Expected vs actual behavior
   - Browser and OS information

### Submitting Changes

1. Fork the repository
2. Create a new branch: `git checkout -b feature/your-feature-name`
3. Make your changes
4. Test your changes thoroughly
5. Commit with clear messages: `git commit -m "Add: feature description"`
6. Push to your fork: `git push origin feature/your-feature-name`
7. Open a Pull Request

### Code Guidelines

- Keep `index.html` as a single-file template
- Maintain compatibility with latest Puter.js version
- Follow HTML5 best practices
- Test across major browsers (Chrome, Firefox, Safari, Edge)
- Keep workflows simple and well-documented
- Update README.md if adding new features

### Workflow Changes

If modifying GitHub Actions workflows:

- Test workflows in your fork first
- Ensure backward compatibility
- Document any new environment variables or secrets
- Keep workflows efficient (minimize API calls)

### Documentation

- Update README.md for user-facing changes
- Add inline comments for complex code
- Provide examples for new features
- Keep language clear and beginner-friendly

## Development Setup

1. Clone your fork:
   ```bash
   git clone https://github.com/YOUR_USERNAME/puter.js-github-pages-hosted-client-app-template.git
   cd puter.js-github-pages-hosted-client-app-template
   ```

2. Test locally:
   ```bash
   # Open index.html in browser or use local server
   python -m http.server 8000
   ```

3. Test workflows:
   - Push to a test branch in your fork
   - Verify GitHub Actions run correctly
   - Check deployment to GitHub Pages

## Pull Request Process

1. Update README.md with details of changes
2. Ensure all CI checks pass
3. Request review from maintainers
4. Address review feedback
5. Squash commits if requested

## Code of Conduct

- Be respectful and inclusive
- Welcome newcomers
- Focus on constructive feedback
- Help others learn

## Questions?

Open an issue with the `question` label or reach out to the maintainers.

Thank you for contributing! 🎉
