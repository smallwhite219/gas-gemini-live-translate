# Gemini Live Translate Practice Frontend

Static top-level browser frontend for personal Gemini Live Translate conversation practice.

The long-lived Gemini API key is not stored here. It stays in Google Apps Script Script Properties. This page asks Apps Script for a short-lived Gemini Live ephemeral token, then connects directly to Gemini Live API from the browser.

## How It Works

```text
GitHub Pages frontend
  -> Apps Script /exec?mode=token with your access key
  -> short-lived auth_tokens/... response
  -> Gemini Live API WebSocket
```

## Local Storage

The page can remember:

- GAS Web App URL
- Access key, only if you check "Remember access key on this device"

These values are stored in your browser `localStorage`, not in GitHub. Do not enable access-key remembering on shared computers.

## Required GAS Backend

Use the companion Apps Script `Code.gs` from your private setup. Configure Script Properties:

```text
GEMINI_API_KEY = your Gemini API key
ACCESS_KEY_SHA256 = sha256 hash of your private access key
```

The frontend expects your GAS deployment to support:

```text
GET /exec?mode=token&callback=...&accessKey=...&targetLanguageCode=en&echoTargetLanguage=true
```

## GitHub Pages

After pushing this repo:

1. Open GitHub repository settings.
2. Go to Pages.
3. Source: Deploy from a branch.
4. Branch: `main`.
5. Folder: `/root`.
6. Save.

The page should become available at:

```text
https://smallwhite219.github.io/gas-gemini-live-translate/
```

## Security Notes

- Do not commit Gemini API keys.
- Do not hard-code your GAS URL or access key in `index.html`.
- The access key is a lightweight personal gate, not full authentication.
- If this becomes multi-user, move token issuance behind real authentication and rate limiting.
