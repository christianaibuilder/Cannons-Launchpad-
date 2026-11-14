# Cannon's Launchpad

Cannon's personal site, with his banking app living inside it at `/bank/`.
Plain HTML, CSS and JavaScript. No build step, no dependencies, no server code.

## Putting it live (GitHub Pages)

1. Upload **everything in this folder** to the repo — keep the folder shape exactly as it is
2. Repo **Settings → Pages → Source: Deploy from a branch → `main` / `(root)`** → **Save**
3. A minute later: `https://<username>.github.io/<repo>/`

The bank is then at `https://<username>.github.io/<repo>/bank/`

## What's here

| Path | What it is |
|---|---|
| `index.html` | The Launchpad. Rocket, facts, 25-photo gallery, button through to the bank |
| `photos/` | The 25 gallery photos |
| `media/` | The clip behind the secret code |
| `bank/index.html` | Bank of Cannon, behind a password screen |
| `bank/icon.png` | The BC logo, 512x512 |
| `bank/manifest.json` | Lets phones install the bank as a real app |
| `.nojekyll` | Tells GitHub Pages to serve the files as-is |

## About the password screen — read this

The bank asks for a password. **It is a keep-out sign, not a safe.**

- The password itself is **not** in the page. Only a SHA-256 hash of it is, so nobody
  reading the source can learn the password or try it on Cannon's other accounts.
- But the check runs in the browser, so somebody who knows what they are doing can skip
  past it and read the page. **Do not put anything genuinely private behind it.**
- It only asks once per browser session.
- It needs `https` (GitHub Pages is https) because it uses the browser's crypto API.

To change the password, replace `GATE_HASH` in `bank/index.html` with the SHA-256 of the
new one.

## About the money

The bank saves with `localStorage` — **per browser, on that one device**. Money entered on
the laptop will not appear on the phone. Clearing site data wipes it.

The Claude artifact version is the other trade: it syncs everywhere, but asks people to
sign in to Claude. Same app, different storage.
