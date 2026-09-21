# CSIT Vault single-file frontend

All frontend HTML, CSS, and JavaScript lives in `index.html`. No build step, external JavaScript, or separate frontend host is required. The reference font (Plus Jakarta Sans) loads from Google Fonts, with a system-font fallback. All widget CSS and JavaScript remains inline.

## Local use

Keep your backend running on port **5500**, then open **http://localhost:5500/** and click the black chat button in the bottom-right corner. The backend already serves this directory.

You can also open `index.html` directly or serve it with a local preview server on another port. Local previews always send API requests to `http://localhost:5500`.

## Blogger

1. Open `index.html` in your editor.
2. Copy everything between `<!-- BLOGGER WIDGET START ... -->` and `<!-- BLOGGER WIDGET END -->` (the template and script).
3. Paste into a Blogger **HTML/JavaScript gadget** and save.
4. Open your blog and click the black chat button.

On a public site, the widget defaults to `https://the-csit-vault-chatbot.onrender.com`. To change it, edit the template near the top:

```html
<template id="csit-vault-template" data-api-base="https://YOUR-BACKEND.onrender.com">
```

Use a publicly accessible HTTPS backend for Blogger visitors. Your laptop's localhost address only works locally. The URL is public configuration; keep the Gemini API key on the backend. The backend must allow requests from your blog's origin (the existing backend enables CORS).

## Behavior

- Shadow DOM isolates the widget's styles and controls from the Blogger theme.
- Enter sends; Shift+Enter adds a line break.
- Collapse or Escape closes the panel without losing the conversation or draft.
- New conversation clears chat history and cancels any pending browser request.
- Connection failures show a connection-check button. Failed answers can be retried or edited.
- Replies display as safe, clean text with common Markdown markers removed, without CDN dependencies. Code contents stay literal. Copy answer copies the displayed text and shows confirmation centered below that response.
- Only the most recent five completed exchanges are sent with each question. Conversations stay in page memory and disappear on reload.
