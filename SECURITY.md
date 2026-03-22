# Security Policy

## Reporting a Vulnerability

If you discover a security vulnerability in this software, please report it responsibly:

1. **Do not** create a public GitHub issue
2. Contact us directly via [Telegram @configbys](https://t.me/configbys)
3. Include a detailed description of the vulnerability and steps to reproduce

We will acknowledge receipt within 48 hours and provide a timeline for a fix.

## Supported Versions

| Version | Supported |
|---------|-----------|
| 1.0.x   | Yes       |

## Security Measures

- All client-server communication is encrypted with AES-256-GCM
- License keys are validated server-side with hardware ID binding
- Admin panel protected by JWT authentication
- No credentials are stored locally — only the license key
- Embedded server binds to `127.0.0.1` only (not network-accessible)
