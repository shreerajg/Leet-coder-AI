# Leet-coder-AI
This is a chrome extension that helps with lead code problem solving and logic building with various features like dry run, hints , explanations and more doesn't need any premium..lol




# DSA Mentor AI — Installation Guide

## Prerequisites

Before you begin, ensure you have:
- **Node.js** v18 or higher → https://nodejs.org/
- **npm** v9 or higher (comes with Node.js)
- **Google Chrome** 114+

Verify with:
```bash
node --version   # Should show v18.x.x or higher
npm --version    # Should show 9.x.x or higher
```

---

## Step 1: Install Dependencies

Open a terminal in the project folder and run:

```bash
npm install --legacy-peer-deps
```

> `--legacy-peer-deps` is required because CRXJS Vite plugin has some peer dep conflicts that don't affect functionality.

---

## Step 2: Generate Icons

Run the icon generator (no external dependencies needed):

```bash
node scripts/make-placeholder-icons.cjs
```

This creates:
- `public/icons/icon16.png`
- `public/icons/icon32.png`
- `public/icons/icon48.png`
- `public/icons/icon128.png`

### Optional: Higher-quality icons

If you want icons from the SVG source (requires Python):

```bash
pip install cairosvg
python scripts/generate_icons.py
```

Or use any image editor to convert `public/icons/icon.svg` to PNG at 16, 32, 48, and 128px.

---

## Step 3: Build the Extension

```bash
npm run build
```

This creates the `dist/` folder with the compiled extension.

To watch for changes during development:
```bash
npm run build:watch
```

---

## Step 4: Load in Chrome

1. Open Chrome and go to: `chrome://extensions`
2. Enable **Developer mode** (toggle in the top-right corner)
3. Click **Load unpacked**
4. Browse to and select your `dist/` folder
5. Click **Select Folder**

You should see "DSA Mentor AI" appear in your extensions list with the robot icon 🤖

---

## Step 5: Configure Your API Key

1. Click the DSA Mentor AI icon in your Chrome toolbar
2. Click **Open Settings ⚙**
3. Enter your API Key (OpenAI, Groq, or any compatible provider)
4. Select your preferred model
5. Click **Save Settings**

### Getting API Keys

| Provider | URL | Free Tier |
|----------|-----|-----------|
| OpenAI | https://platform.openai.com/api-keys | No (pay-as-go) |
| Groq | https://console.groq.com/ | Yes (generous) |
| Together AI | https://api.together.xyz/ | $25 credit |

> **Groq is recommended for beginners** — it's free, very fast, and the Llama 3.3 70B model is excellent for DSA explanations.

---

## Step 6: Start Using It

1. Go to any LeetCode problem, e.g.:
   `https://leetcode.com/problems/two-sum/`

2. The panel automatically opens (or press **Alt+Shift+A**)

3. Choose your mode:
   - **💡 Hints** — Progressive guidance, no spoilers
   - **📖 Explain** — Full explanation across all tabs

4. Start learning! 🎓

---

## Troubleshooting

### "Cannot read manifest" error
Make sure you're loading the `dist/` folder, not the project root.

### Panel doesn't appear on LeetCode
1. Check that the extension is enabled in `chrome://extensions`
2. Refresh the LeetCode page
3. The extension only works on `leetcode.com/problems/*` URLs

### Build fails
```bash
# Try clearing everything and rebuilding
rm -rf node_modules dist
npm install --legacy-peer-deps
npm run build
```

### "API key not configured" message
Open Settings via the extension icon and enter your API key.

### Icons not showing
Run: `node scripts/make-placeholder-icons.cjs`
Then rebuild: `npm run build`

---

## Updating

After making code changes:
1. Rebuild: `npm run build`
2. Go to `chrome://extensions`
3. Click the reload icon ↺ on the DSA Mentor AI card
4. Refresh your LeetCode tab

---

## Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Alt+Shift+A` | Toggle panel |
| `Enter` | Send chat message |
| `Shift+Enter` | New line in chat |
| Drag left edge | Resize panel |

---

*The API key is stored encrypted by Chrome and never leaves your browser except when calling your chosen AI provider.*
