# Hanzi Trail (local version) — setup

This is the same reading app, but running as a plain local file instead of a
Claude.ai artifact — so Chrome will show the normal microphone permission
prompt, and the 🎤 button can automatically check Jacob's reading against
the correct sentence (no manual tapping needed).

## Run it (Windows)

Chrome's speech recognition needs a "secure" address (`http://localhost...`),
not a bare double-clicked file — so a tiny local server is the reliable way
to run this. You already have Python if you've used it before; if not,
install it from python.org first.

1. Unzip/save this folder somewhere, e.g. `C:\Users\Hariyono\hanzi-trail`
2. Open **Command Prompt** (search "cmd" in the Start menu)
3. Navigate into the folder:
   ```
   cd C:\Users\Hariyono\hanzi-trail
   ```
4. Start a local server:
   ```
   python -m http.server 8000
   ```
   (leave this window open — closing it stops the app)
5. Open **Chrome** and go to:
   ```
   http://localhost:8000
   ```
6. Tap 🎤 on any sentence — Chrome will ask for microphone permission the
   first time. Click **Allow**. Have Jacob read the sentence aloud; it'll
   automatically highlight any hanzi he misread or skipped.

## Next time

You don't need to redo any setup — just repeat steps 3–5 (open Command
Prompt in the folder, run the server command, open the localhost address).

## If Python isn't installed

Install it from https://www.python.org/downloads/ (check "Add python.exe
to PATH" during setup), then follow the steps above. Any other way of
serving a local folder over `http://localhost` works too, if you already
have one you prefer (e.g. VS Code's "Live Server" extension).

# Hanzi Trail — getting it onto Jacob's home screen

This version is just the "type your own sentences" tool — no built-in
story stops, just the add-a-sentence box and the list of sentences
you've added, each with 🔊 listen, 🎤 auto reading-check, tap-for-pinyin,
and 🗑️ remove.

The easiest, most reliable way to get it onto his phone — and the one
that actually fixes the microphone problems for good — is to put it on
a real `https://` address for a minute, rather than running it from
`localhost` or a local file.

## Step 1 — put it online (takes ~1 minute, free, no signup needed)

1. On your computer, go to **https://app.netlify.com/drop** in a browser
2. Drag the whole `hanzi-trail-local` folder (the one with `index.html`
   in it) onto that page
3. It'll give you a live link like `https://random-name-123.netlify.app`
   — that's now a real, secure website hosting the app

(This free link can disappear after a while if left completely idle, but
you can always drag the folder again to get a fresh one — or make a free
Netlify account first if you want a permanent link.)

## Step 2 — install it on Jacob's phone/tablet

1. Open that `https://...netlify.app` link in **Chrome** on his device
2. Tap the **⋮** menu (top right) → **Add to Home screen** (Chrome may
   also show this as a banner/button automatically)
3. Confirm — a "Hanzi Trail" icon with the 汉 logo appears on his home
   screen, just like a normal app
4. Opening it from that icon runs full-screen, no browser bar

## Why this also fixes the mic

Everything we tried before (`file://`, `localhost`, a phone reaching a PC
over Wi-Fi) ran into browser security rules that only fully trust a real
`https://` address. Once it's on one, 🎤 should Just Work — tap it,
allow the microphone the first time, and it checks Jacob's reading
automatically, from his own home screen icon, no computer required.

## Notes

- Progress, stars, and any sentences you've added under "➕ My Sentences"
  are saved on that specific device/browser — they won't follow to a
  different phone or browser automatically.
- If Netlify is blocked on your network too, the same idea works with
  any free static host (GitHub Pages, Vercel, Cloudflare Pages) — the
  folder just needs to end up served over `https://` somewhere.
