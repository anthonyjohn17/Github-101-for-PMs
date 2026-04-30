# Prompt: Build Your First Project

Copy and paste this into Cursor or Claude Code. Replace the bracketed sections.

---

```
Build a [type of tool] that solves this problem: [describe the pain point in 1-2 sentences].

Here's what it should do:
1. [Input: what the user provides]
2. [Process: what the tool does with it]
3. [Output: what the user gets back]

Use Python. Keep it simple — one main script is fine.
Use [OpenAI / Claude / other] API for the AI parts.
Include error handling for missing API keys.
Add comments explaining what each section does.
```

---

**Starter ideas to fill in the brackets:**

**Email agent:**
- Input: raw email text
- Process: analyze tone and intent, draft a response
- Output: suggested reply the user can edit

**Feedback analyzer:**
- Input: CSV of user feedback or support tickets
- Process: cluster by theme, score sentiment, rank by frequency
- Output: summary report with top 5 themes

**Competitive monitor:**
- Input: list of competitor URLs
- Process: check for changes daily, extract key updates
- Output: weekly digest email or Slack message

---

**Reference in this repo:** [Github-101.md](../Github-101.md) — [Quick start](../Github-101.md#-quick-start-5-steps), [Branching](../Github-101.md#-branching) (if you split experiments), [Best practices](../Github-101.md#-best-practices).
