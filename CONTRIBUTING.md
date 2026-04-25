# Contributing to Awesome Game Design

Thank you for considering a contribution. This repository aims to be the most useful game design reference on GitHub, and it grows through careful curation — not volume.

Please read this guide before opening an issue or pull request.

---

## 📌 The Standard

Every entry must answer this question:

> **"What will a game designer learn from this that they couldn't get from just Googling the title?"**

If the answer is unclear, the entry is not yet ready.

---

## ✅ What We Accept

- **New entries** that include both the source and a concrete **key lesson** (not just a link)
- **New resource files** for topics not yet covered (e.g., monetization math, playtest methodology, esports ecosystems)
- **Corrections** to outdated information, broken links, or factual mistakes
- **Case studies** from historically significant games, postmortems, or publicly disclosed dev talks
- **Non-English references** with English summaries when the original material is in another language

## ❌ What We Don't Accept

- Personal game portfolio entries (this is a curation resource, not a self-promotion board)
- Promotional content, advertising, affiliate links
- Link dumps without context, explanation, or extracted lessons
- Content that violates confidentiality (e.g., leaked platform TRCs, NDA-bound internal docs)
- Copyrighted screenshots, logos, or trademarks used without proper context
- Unverified rumors or social media hearsay
- AI-generated content submitted without human review

---

## 📝 Resource Entry Format

Each new entry should follow the existing style in `resources/*.md`:

```markdown
### 🎯 [Game Title or Topic] — [Studio/Author, Year]

**Source**: [Primary Link](https://...) | [Archive/Mirror](https://...)
**Status**: [e.g., "Published", "Pre-release cancelled", "Internal leak — do not redistribute"]

### Summary
- 2–5 bullet points distilling the material

### Key Lessons
**Lesson 1 — [Short Title]**
Explanation (2–4 sentences) of what the reader should internalize.

**Lesson 2 — [Short Title]**
...
```

### Tone

- **Opinionated is OK**. "Avoid this pattern" is more useful than "This is a pattern."
- **Cite** when making claims about numbers, dates, or outcomes.
- **Label** industry estimates vs. officially published figures. Do not present estimates as facts.
- **Korean or English** body is acceptable. Match the surrounding file style when adding to existing content.

---

## 🌐 Style Guide

### Markdown
- Emoji in H3 headers is OK (matches existing style).
- Tables for comparisons (mechanics, KPIs, platforms).
- Relative links for internal references (`./resources/file.md`).
- External links as full URLs, preferably with archive.org fallback for unstable sources.

### Facts & Citations
- **Dates**: `YYYY.MM.DD` or `YYYY-MM-DD`.
- **Money**: Specify currency (`$245M`, `₩20만`, `¥100k`).
- **Numbers**: Mark estimates as `(업계 추정)` or `(industry estimate)`.
- **Regulations**: Include jurisdiction and effective date.

### Confidentiality
- **Do not** quote from NDA-bound materials (Sony DevNet, Xbox XR internal docs, Nintendo Lotcheck, publisher panels, private Discord dumps).
- **Do** cite public GDC Vault talks, postmortem articles, ex-dev interviews, and official portals.

---

## 🔁 PR Workflow

1. **Fork** the repository.
2. **Branch** from `master`: `resource/<topic>` or `fix/<description>`.
3. **Write** your contribution following the standards above.
4. **Self-check**:
   - [ ] All links work.
   - [ ] No trademarked images/logos embedded.
   - [ ] Factual claims have sources.
   - [ ] Markdown renders correctly (preview in your fork before PR).
   - [ ] The "what will they learn" question has a clear answer.
5. **Open a PR** to `master` using the PR template.
6. **Respond to review** within a reasonable timeframe. Stale PRs may be closed after 60 days.

### Automated Checks

Every PR runs two GitHub Actions:

- **Lint & Link Check** (`.github/workflows/lint.yml`): markdownlint + lychee link verification on changed Markdown files
- **Sources Verified Freshness** (`.github/workflows/sources-verified-freshness.yml`): monthly cron that opens a maintenance issue when any `Sources Verified (YYYY-MM-DD)` badge is older than 180 days

PRs that fail link check or markdown lint will not be merged. Run `npm install -g markdownlint-cli2 && markdownlint-cli2 '**/*.md'` locally to preview, or open a draft PR to let CI surface issues.

### Commit Style

Conventional Commits preferred but not strictly enforced:

```
docs: add postmortem entry for <game>
fix: correct release date for FFXIV A Realm Reborn
refactor: reorganize live-ops KPI section
```

---

## 🧭 Scope Boundaries

### In Scope
- Game design theory, frameworks, heuristics
- Historical GDDs, postmortems, dev talks
- Balancing, narrative, art direction, UX, sound
- Platform/monetization/regulation topics insofar as they shape design decisions
- AAA / AA / indie / mobile — all budgets welcome

### Out of Scope
- Pure engineering topics (graphics programming, networking optimization) unless they shape design
- Platform cert internals we can't publicly source
- Personal opinion pieces without actionable lessons

---

## 🙏 Code of Conduct

All contributors must abide by the [Code of Conduct](./CODE_OF_CONDUCT.md). Harassment, trolling, or personal attacks will result in PR closure and removal from discussions.

---

## 💬 Questions

- Open a **Discussion** for open-ended questions about scope or direction
- Open an **Issue** for concrete bugs, broken links, or missing content
- For private concerns, use the contact method listed in the CoC

---

*Thank you for helping make this a useful resource for the global game design community.*
