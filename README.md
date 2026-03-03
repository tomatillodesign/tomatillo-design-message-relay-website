# Message Relay Landing Page

A polished single-page website for `message-relay.org`, designed to clearly explain the purpose of Message Relay and build trust with recipients who see the sending domain in transactional emails.

This site is built as a lightweight static page for easy hosting on GitHub Pages.

## What this repo contains

- `index.html` - Full semantic page markup.
- `styles.css` - Complete visual system, layout, and responsive styles.
- `content.md` - Source content used to build the landing page.

## Purpose

Message Relay is infrastructure for secure, website-generated transactional email on behalf of nonprofit and institutional organizations.

The page explains:

- What Message Relay is
- Why recipients may see `@message-relay.org`
- What the service does and does not do
- High-level technical and security posture
- Operator/contact information
- Common FAQ responses

## Design and UX approach

The page styling is intentionally:

- Human and warm (soft neutrals, gentle surfaces, clear spacing)
- Professional and trustworthy (clean hierarchy, restrained accents, polished typography)
- Highly readable (comfortable line length, strong contrast, structured sections)

Typography:

- Headings: `Fraunces`
- Body: `Inter`
- Includes resilient fallbacks for rendering stability

## Accessibility and quality standards

The implementation includes:

- Semantic landmarks (`header`, `main`, `section`, `footer`)
- Logical heading hierarchy
- Skip link for keyboard users
- Focus-visible states for interactive elements
- Accessible link handling and contrast-minded palette
- Mobile-first responsive layout

## Local preview

Since this is a static site, you can preview it by opening `index.html` directly in a browser.

For a more production-like preview, run a local static server from the repo root (example with Python):

```bash
python3 -m http.server 8000
```

Then open:

`http://localhost:8000`

## Deployment

Deployment steps are documented in:

`GH_PAGES_DEPLOYMENT.md`
