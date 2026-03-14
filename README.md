# 🏦 Payment Testing Challenge

> A live, competitive quiz game for payment testing professionals — test your knowledge, beat the clock, and top the leaderboard!

## 🌐 Live URLs

| Page | URL |
|------|-----|
| 🎮 **Quiz** | https://shubhaje.github.io/payment-gathering-quiz/ |
| 🏆 **Leaderboard** | https://shubhaje.github.io/payment-gathering-quiz/leaderboard |

---

## 🎯 About the Quiz

The **Payment Testing Challenge** is a live, browser-based quiz covering software testing concepts applied to real-world payment scenarios. Players answer 6 randomly selected questions from a pool of 22 and compete for the top 5 spots on the live leaderboard.

### Topics covered
CPP · SEPA Instant · HVP · PPR2 · BOX · PDS · SEK Batch · Target DKK · Testing · Automation · AI

### Question types
- **What is this test type?** — definitions and concepts (Smoke, Regression, UAT, Load, Stress, Security, etc.)
- **Which test? 💳** — real payment scenario questions where you pick the right test approach

### Scoring

| Points | Condition |
|--------|-----------|
| 100 pts | Standard question correct |
| 150 pts | Mid-tier question correct |
| 200 pts | Advanced question correct |
| +10 pts per answer | Streak bonus (consecutive correct answers) |
| **Max: 1,050 pts** | All 6 correct with full streak |

### Ranking
Players are ranked by **score (highest first)**, then by **time (fastest first)** as tiebreaker.

---

## 📱 How to use at an event

1. Display `leaderboard.html` on a projector or large screen
2. Players scan the **QR code** on the quiz page to play on their phones
3. Players enter a **unique name** — duplicate names are blocked
4. Scores save automatically after completing all 6 questions (~30s delay)
5. Leaderboard auto-refreshes every 15 seconds
6. To reset between sessions — empty `scores.json` to `[]` and commit

---

## 🏗 Architecture

```
Player completes quiz
       ↓
Quiz triggers GitHub repository_dispatch (save-score event)
       ↓
save-score.yml Action runs → updates scores.json → commits to repo
       ↓
deploy.yml Action runs → injects token secret → deploys to GitHub Pages
       ↓
Leaderboard reads scores.json via GitHub API → updates every 15s
```

### Files

| File | Purpose |
|------|---------|
| `index.html` | Quiz game — 22 questions, 6 random per session |
| `leaderboard.html` | Live leaderboard — top 5, auto-refreshes |
| `scores.json` | Score storage — updated by GitHub Action |
| `404.html` | Clean URL routing |
| `.github/workflows/deploy.yml` | Deploys to GitHub Pages, injects secrets |
| `.github/workflows/save-score.yml` | Writes scores to `scores.json` |

---

## 🔒 Security

- The GitHub PAT is stored in **GitHub Secrets** only — never committed to any file
- The deploy workflow injects the token at build time only
- After the event, revoke the token at https://github.com/settings/tokens

---

## 🛠 Setup

1. Go to **Settings → Secrets and variables → Actions → New repository secret**
   - Name: `DISPATCH_TOKEN` · Value: your GitHub PAT (classic, `repo` scope)
2. Go to **Settings → Pages → Source → GitHub Actions**
3. Push to `main` — deploy workflow triggers automatically

---

## 🔄 Reset leaderboard

Edit `scores.json` → replace with `[]` → commit. Leaderboard clears within 15 seconds.

---

*Built for payment testing teams · Powered by GitHub Pages + GitHub Actions*