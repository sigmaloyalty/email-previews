# Email Preview Tool

A lightweight GitHub Pages tool for previewing HTML email campaigns in desktop and mobile views, with English/French language toggling. Inspired by Stripo's preview mode.

## Quick Start

1. Clone this repo and enable GitHub Pages (Settings → Pages → Deploy from `main` branch)
2. Create a campaign folder under `emails/` with your HTML files and a `config.json`
3. Share the preview URL with your team

## Adding a Campaign

Create a folder under `emails/` with a short slug name:

```
emails/
  your-campaign-slug/
    config.json
    en.html
    fr.html
```

### config.json format

```json
{
  "name": "Friendly Campaign Name",
  "en": {
    "file": "en.html",
    "subject": "Your subject line here",
    "preheader": "Your pre-header text here"
  },
  "fr": {
    "file": "fr.html",
    "subject": "Votre ligne d'objet ici",
    "preheader": "Votre texte de pré-en-tête ici"
  }
}
```

- **name** – Displayed in the toolbar
- **file** – Path to the HTML file (relative to the campaign folder)
- **subject** – The email subject line (displayed above the preview)
- **preheader** – The hidden pre-header text (displayed above the preview)

If you only have one language, just include that key. The language toggle hides itself automatically when only one language is configured.

## Sharing a Preview

Send your colleagues a direct link:

```
https://your-username.github.io/repo-name/viewer.html?campaign=your-campaign-slug
```

They'll land directly on that campaign — no menus, no other campaigns visible.

## Features

- **Desktop / Mobile toggle** – Switches between 700px and 375px viewport widths
- **EN / FR toggle** – Swaps between language versions; auto-hides if only one language exists
- **Subject & pre-header display** – Shown in a strip above the preview, updates per language
- **Auto-sizing** – The iframe adjusts its height to fit the email content
- **Error handling** – Clear messages if a campaign or file can't be found

## File Structure

```
├── viewer.html                  ← The preview tool (single file, no dependencies)
├── README.md
└── emails/
    ├── privacy-week/            ← Example campaign
    │   ├── config.json
    │   ├── en.html
    │   └── fr.html
    └── another-campaign/
        ├── config.json
        ├── en.html
        └── fr.html
```

## Notes

- The viewer is a single self-contained HTML file with no build step or dependencies
- Email HTML files are loaded into a sandboxed iframe
- Works with any HTML email exported from Stripo, Mailchimp, or hand-coded
