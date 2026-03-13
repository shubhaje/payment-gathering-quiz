# 🧪 Test This! — Payment Testing Quiz

Live quiz game with a **real shared leaderboard** stored in GitHub.

## 🌐 Live URLs

| Page | URL |
|------|-----|
| **Quiz** | https://shubhaje.github.io/payment-gathering-quiz/ |
| **Leaderboard** | https://shubhaje.github.io/payment-gathering-quiz/leaderboard.html |

---

## 🚀 Setup (one-time)

### Step 1 — Enable GitHub Pages
1. Go to your repo → **Settings → Pages**
2. Branch: `main` / Folder: `/ (root)` → **Save**
3. Wait ~60 seconds

### Step 2 — Create a GitHub Personal Access Token (PAT)
1. Go to: https://github.com/settings/tokens/new
2. Note: `test-this-quiz` · Expiry: 90 days · Scope: ✅ `repo`
3. Click **Generate token** and copy it immediately

### Step 3 — Add your token to both HTML files
In both `index.html` and `leaderboard.html`, find and replace:
```
var GITHUB_TOKEN = 'PASTE_YOUR_PAT_HERE';
```
with your actual token.

### Step 4 — Commit all 4 files to GitHub
`index.html` · `leaderboard.html` · `scores.json` · `README.md`

---

## 📱 At your event
- Show `leaderboard.html` on the big screen — auto-refreshes every 15s
- Players scan the QR code to play on their phones
- Scores write live to `scores.json` in this repo
- Use **Reset Leaderboard** to clear between sessions

## 🔒 After the event
Revoke the PAT at https://github.com/settings/tokens
