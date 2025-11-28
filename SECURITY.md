# Security Policy

## Overview

Crystal Blitz is a client-side browser game contained entirely within a single HTML file. It runs locally in your browser and does not:
- Make external API calls
- Store or transmit personal data (only anonymous high scores)
- Require authentication
- Use cookies (minimal localStorage for high scores only)
- Connect to external servers

## Supported Versions

| Version | Supported          |
| ------- | ------------------ |
| 0.99.x  | :white_check_mark: |
| < 0.99  | :x:                |

## Security Considerations

### Safe to Use
- ✅ **Minimal data collection**: Only anonymous high scores stored locally (no PII)
- ✅ **No external dependencies**: All code is self-contained
- ✅ **No network requests**: Runs completely offline
- ✅ **Minimal persistent storage**: Only localStorage for high scores (no cookies or indexedDB)
- ✅ **Input sanitization**: Text inputs are sanitized to prevent injection attacks
- ✅ **Safe parsing**: All number parsing uses safe defaults

### Browser Security Features
The game utilizes standard browser security features:
- Canvas rendering (sandboxed)
- Web Audio API (sandboxed)
- Standard DOM manipulation
- No eval() or Function() constructors
- No inline event handlers (all addEventListener)

### Recommended Content Security Policy (CSP)

If you host Crystal Blitz on your own server, consider adding these CSP headers:

```http
Content-Security-Policy:
  default-src 'none';
  script-src 'unsafe-inline';
  style-src 'unsafe-inline';
  img-src 'self' data:;
  connect-src 'none';
```

**Note**: `'unsafe-inline'` is required because the game is a single HTML file with embedded scripts and styles. This is acceptable for self-contained, client-side games without user-generated content.

## Reporting a Vulnerability

If you discover a security vulnerability in Crystal Blitz, please report it responsibly:

### How to Report

1. **Email**: [Your Email Here] (Replace with your contact)
2. **GitHub**: Open a [security advisory](https://github.com/Zacsluss/crystal_blitz/security/advisories/new)
3. **LinkedIn**: Message via [LinkedIn profile](https://www.linkedin.com/in/zacharyjsluss/)

### What to Include

- **Description**: Clear explanation of the vulnerability
- **Steps to Reproduce**: Detailed reproduction steps
- **Impact**: Potential security impact
- **Suggested Fix**: If you have recommendations
- **Browser/OS**: Environment where discovered

### Response Timeline

- **24-48 hours**: Initial acknowledgment
- **1 week**: Preliminary assessment
- **2-4 weeks**: Patch development and testing
- **Immediate**: Critical issues (XSS, RCE, data exposure)

### Responsible Disclosure

Please:
- ✅ Allow reasonable time for a fix before public disclosure
- ✅ Provide detailed reproduction steps
- ✅ Act in good faith to avoid data loss or service disruption

Please don't:
- ❌ Publicly disclose the vulnerability before a patch is available
- ❌ Exploit the vulnerability beyond proof-of-concept
- ❌ Access, modify, or delete data belonging to others

## Security Best Practices for Users

### Safe Usage
- Download directly from [official GitHub repository](https://github.com/Zacsluss/crystal_blitz)
- Verify file integrity if security is critical
- Open only in modern, updated browsers
- Use official GitHub Pages deployment: https://zacsluss.github.io/crystal_blitz/

### Hosting Your Own Copy
If you want to host Crystal Blitz yourself:
1. Clone from official repository
2. Serve with appropriate CSP headers
3. Use HTTPS if deployed to web
4. Keep your web server software updated
5. Consider implementing Subresource Integrity (SRI) if splitting into separate files

## Security Changelog

### [0.99.0] - 2025-01-27
- Initial SECURITY.md created
- Documented security posture
- Established vulnerability reporting process

---

## Additional Resources

- [OWASP HTML5 Security Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/HTML5_Security_Cheat_Sheet.html)
- [MDN Web Security](https://developer.mozilla.org/en-US/docs/Web/Security)
- [Content Security Policy Reference](https://content-security-policy.com/)

---

**Last Updated**: January 27, 2025
**Maintained By**: Zachary Sluss
**License**: MIT (See [LICENSE](LICENSE))
