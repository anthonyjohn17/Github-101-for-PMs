# GitHub 101 - PM Starter Kit

A practical bundle for **shipping a hire-ready GitHub profile** plus a **full Git and GitHub reference** you can read end-to-end or jump into by topic.

**24% of PM candidates have a GitHub. The latest PMs I placed at OpenAI, Anthropic, and Meta AI all had one.**

---

## Repository layout

```
github-101/
├── Github-101.md              # Git & GitHub — complete practical guide (TOC + 76 topic areas)
├── CHECKLIST.md               # 3-week roadmap from zero to live
├── templates/
│   ├── PROFILE-README.md        # GitHub profile landing page
│   └── PROJECT-README.md        # README template for each project
├── prompts/
│   ├── create-repo.md           # Cursor / Claude Code: new repo
│   ├── build-project.md         # Cursor / Claude Code: first build
│   ├── commit-and-push.md       # Cursor / Claude Code: save and publish
│   └── write-readme.md          # Cursor / Claude Code: documentation
├── github-readme/README.md    # Example profile README layout (badges, skills strip)
└── .gitignore
```

---

## [Github-101.md](Github-101.md) — Git & GitHub complete practical guide

Single manual-style doc that goes from **basics to enterprise-style workflows**, including safety, recovery, and internals. It covers:

- **Fundamentals:** install and config, mental model, lifecycle, staging, commits, inspect, remotes, push / clone / pull, fetch vs pull  
- **Collaboration:** branches, merges, conflicts, rebase, forks, pull requests  
- **Day-to-day power tools:** undo patterns, reflog, history, tags, stash, `.gitignore`, HTTPS vs SSH, common errors  
- **Team practice:** best practices, professional workflow, commit message standards, exercises, cheat sheet  
- **Scale and platform:** enterprise topics, hooks, CI/CD, monorepos, cherry-pick, large repos, security, worktrees, subtree, semantic versioning  
- **Depth:** object model, merge and diff internals, SHA-1 / content-addressable storage, bisect, performance tuning, monorepo architecture, interview questions, disaster recovery, structured “book” layout  

Open [Github-101.md](Github-101.md) and use its **table of contents** at the top to jump to any section. The prompts and checklist below point back into that file where it helps.

---

## Quick start (profile kit)

1. **Fork this repo** (or clone and use it locally).  
2. **Follow [CHECKLIST.md](CHECKLIST.md)** for the day-by-day plan.  
3. **Use** `templates/` for your profile and project READMEs.  
4. **Paste prompts** from `prompts/` into Cursor or Claude Code to create repos, build, commit, and document.  
5. **Optional:** read [Github-101.md](Github-101.md) in parallel so your commands and recovery steps match how Git actually works.

---

## The 3-week plan

| When | What | Use |
|------|------|-----|
| **Day 1** | Profile setup | `templates/PROFILE-README.md` |
| **Day 2** | First project shipped | `prompts/build-project.md`, `commit-and-push.md` |
| **Week 2** | Flagship project | `prompts/create-repo.md` |
| **Week 3** | Polish and publish | `prompts/write-readme.md` |

Details and checkboxes: [CHECKLIST.md](CHECKLIST.md).

---

## What makes a strong PM GitHub

1. **One flagship project** that solves a real problem — not many tiny throwaways  
2. **Clear positioning** — one-line bio: what you build  
3. **Recent activity** — consistency beats vanity metrics  
4. **Strategic forks and contributions** — tools in your target space  
5. **Documentation that shows product thinking** — tradeoffs, decisions, learnings  
6. **A portfolio story** — repos that fit together

The `PROJECT-README.md` template includes Problem, Solution, Tradeoffs, and What I Learned — sections hiring managers skim for first.

---

## What to avoid

- **Copy-paste repos** you cannot explain  
- **Joke-only projects** if the goal is PM credibility  
- **Empty or cosmetic commits** — activity graphs reward real work  
- **Engineer cosplay** — use AI for code; you own problem framing, UX, and docs  
- **One-and-done** — a stale profile is weaker than none; ship small improvements regularly  

---

## License

This material is provided for educational use. You may copy, adapt, and use it for personal or professional purposes.
