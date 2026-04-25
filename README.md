# Awesome Game Design 🎮

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)
[![Last Updated](https://img.shields.io/badge/Updated-April%202026-orange.svg)]()

> 🌐 **Languages**: **English (this file)** · [한국어 (README.ko.md)](./README.ko.md)

> A world-class curated resource for game designers — GDD references, design theory, balancing frameworks, narrative tools, art direction, marketing, AAA production, platform certification, and live-ops. Inspired by the curation philosophy of [awesome-design](https://github.com/gztchan/awesome-design).

---

## 📌 What Is This?

This repository is a **comprehensive knowledge base for game designers** — from indie solo developers to AAA studio leads. It collects the best theories, tools, historical GDDs, and practical frameworks that professional game designers rely on.

**This is a public curation resource**, maintained to be the most useful game design reference on GitHub. Every entry answers a single question: *"What will a designer learn from this that they couldn't get from just Googling the title?"*

---

## 📚 Table of Contents

- [SKILL.md — Game Design Expert System Prompt](#skillmd)
- [Resources](#resources)
  - [Famous GDDs](#-famous-game-design-documents)
  - [Postmortems](#-postmortems)
  - [Narrative Design](#-narrative-design)
  - [Game Balancing](#-game-balancing)
  - [Art Direction](#-art-direction)
  - [Marketing & QA](#-marketing--qa)
  - [Production Pipeline (AAA)](#-production-pipeline-aaa)
  - [Platform Certification](#-platform-certification)
  - [Live Ops Playbook](#-live-ops-playbook)
- [How to Use This Repo](#how-to-use-this-repo)
- [Contributing](#contributing)
- [Trademarks & Legal Notice](#trademarks--legal-notice)

---

## SKILL.md

**[→ SKILL.en.md (English)](./SKILL.en.md)** · **[→ SKILL.md (한국어)](./SKILL.md)** — A complete system prompt for Claude to act as a world-class game designer. Covers:

- Role definition (Systems Designer, Narrative Designer, UX Designer, PM, Visual Director)
- Awesome Design principles adapted for games (color theory, typography, UX patterns, animation)
- GDD writing standards and template (10-section structure)
- Game mechanic classification system
- Monetization strategy framework
- MVP scoping methodology (RICE scoring)
- **Claude Design System Prompt philosophy** — HTML artifact game UI prototyping
- **Narrative design methodology** — Save the Cat, Hero's Journey, branching narrative patterns
- **Balancing theory** — Machinations, economic loops, PvP ELO/MMR, gacha ethics

---

## Resources

### 📄 Famous Game Design Documents

**[→ resources/famous-gdds.md](./resources/famous-gdds.md)**

Historical GDDs and design documents from landmark games, with key lessons from each:

| Game | Studio | Key Lesson |
|------|--------|-----------|
| **Doom Bible** | id Software (1992) | Narrative vs. pure gameplay — when to choose simplicity |
| **Diablo** | Blizzard North (1994) | Prototype over documents — turn-based became real-time in playtesting |
| **BioShock** | Irrational Games (2006) | Philosophy embedded in mechanics, not cutscenes |
| **Deus Ex** | Ion Storm (1998) | True player agency through open systems, not scripted branches |
| **Monaco** | Pocketwatch Games (2013) | Solo dev endurance, role differentiation in co-op design |
| **The Sims** | Maxis (2000) | Follow unexpected fun — the NPCs were more interesting than the houses |

Includes GDC Vault links, Game Developer Magazine archives, design philosophy breakdowns, and universal lessons about GDD writing.

---

### 🪦 Postmortems

**[→ resources/postmortems.md](./resources/postmortems.md)**

What worked and what didn't — from indie hits to AAA productions:

**Indie:**
- **Stardew Valley** — 1-person 4-year development; burnout risk; polishing over marketing
- **Hollow Knight** — Scope expansion decisions; atmosphere-first design; free DLC loyalty
- **Celeste** — Assist Mode as accessibility standard; metaphor-as-mechanic; personal truth
- **Undertale** — Genre subversion; save-data-as-narrative; medium-specific storytelling
- **Hades** — Early Access as co-development; death integrated into story structure

**AAA:**
- **The Last of Us** — Emotion-first mechanic design; companion AI evolution
- **God of War (2018)** — One-shot camera as creative constraint and identity
- **Elden Ring** — Soulslike + open world synthesis; PC optimization pitfalls

Includes GDC Vault links and patterns that appear across multiple postmortems.

---

### 📖 Narrative Design

**[→ resources/narrative-design.md](./resources/narrative-design.md)**

Tools, theory, and dialogue system patterns:

**Tools:** Twine, Ink/Inky (MIT), Yarn Spinner (Unity/Godot), articy:draft, Obsidian (world bible)

**Theory:**
- Save the Cat 15-beat sheet mapped to interactive media
- Hero's Journey 12 steps with game implementation notes
- Non-linear storytelling levels: cosmetic choice → short branch → world state → systemic narrative

**Dialogue patterns:** Emotion spectrum (Disco Elysium style), skill-gated choices (Fallout style), timed responses (Mass Effect style), relationship-state dialogue

**World-building:** Iceberg theory, World Bible chapter template, environmental storytelling techniques (Dead Space, Dark Souls, Firewatch)

---

### ⚖️ Game Balancing

**[→ resources/game-balancing.md](./resources/game-balancing.md)**

From theory to production-ready formulas:

**Machinations Framework:** 6 node types, feedback loop design (positive/negative), economic loop diagrams for RPG and strategy genres

**Numerical Balancing:**
- Linear / exponential / logarithmic / S-curve stat scaling with examples
- DPS vs TTK calculation standards and target values by encounter type
- Rock-paper-scissors triangle balancing

**PvP:** ELO formula with K-value optimization; MMR tier distribution design; win-rate balancing principles; matchmaking speed vs quality tradeoffs

**Idle/Casual:** Upgrade cost curves (`BASE × MULTIPLIER^n`); session length design; offline progress formulas

**Gacha ethics:** Pity system math (soft/hard ceiling), drop table design, global regulatory comparison (Korea/China/Belgium/EU), ethical design checklist

**5-stage process:** Theory → Bot simulation → Internal playtest → External playtest → Live data

---

### 🎨 Art Direction

**[→ resources/art-direction.md](./resources/art-direction.md)**

Visual craft from pixels to sound:

**Pixel Art:** 7 core principles; Aseprite vs Pyxel Edit vs LibreSprite comparison; animation frame counts; learning resources (Lospec, Pedro Medeiros, Pixel Joint)

**UI/UX:** Information hierarchy; HUD zone placement (Fitts's Law); color blindness accessibility (WCAG 2.1); inventory system types; onboarding pattern catalog

**Color Theory:** 5-layer palette structure; value-first design; tool roundup (Coolors, Lospec, Adobe Color, Paletton)

**Sound Design:** FMOD vs Wwise (with indie pricing); free sources (Freesound, BFXR, OpenGameArt); layering, pitch randomization, dynamic range principles

**Animation:** Spine vs DragonBones vs frame animation decision tree; Disney's 12 Principles applied to games

---

### 📣 Marketing & QA

**[→ resources/marketing-qa.md](./resources/marketing-qa.md)**

From first commit to launch week and beyond:

**Launch Checklist:** 6 months → 3 months → 1 month → launch week with concrete actions at each stage

**Steam Optimization:** Title naming, short description formula, tag selection strategy, capsule art principles, wishlist-to-sales conversion estimates

**Trailer Production:** 4 trailer types; "first 5 seconds" principle; music licensing options; 6-part gameplay trailer structure

**Community:** Discord structure; Twitter/TikTok/Reddit platform-specific strategies; influencer/streamer outreach flow

**QA:** Functional/regression/playtest types; bug report standard template (severity + priority); Nielsen's Law (5–8 testers = 95% issue discovery)

**Launch Strategy:** Soft launch vs hard launch; Steam Early Access decision criteria; post-launch week 1 response; long-term update roadmap; sale participation strategy

---

### 🏭 Production Pipeline (AAA)

**[→ resources/production-pipeline.md](./resources/production-pipeline.md)**

The actual production pipeline used by AAA studios — also useful for indie/AA teams trying to understand "why does AAA take 2–5 years?":

- **Stages**: Concept → Pre-production → Production (Alpha / Beta / Code Lock) → Certification → Launch → Live
- **Gate criteria**: explicit pass conditions per stage (blocker count, crash rate, cert pass rate, localization lock)
- **Vertical Slice**: real-world VS scope and checklists from Uncharted 4, Destiny, Spider-Man, AC Valhalla
- **Greenlight**: 10-slide pitch-deck template + publisher-side judging rubric (7 weighted criteria)
- **Milestone payments**: Signing 15% → Prototype 10% → Alpha 20% → Beta 20% → Gold 15% → Launch 10% + royalty (industry-average estimates)
- **RACI / DRI**: responsibility matrix for design pillar changes, scope cuts, platform additions, delays, and crunch decisions
- **Deep cases**: Uncharted 4 director-replacement reboot, Cyberpunk 2077 cert/launch fail, Baldur's Gate 3 EA-as-production, Starfield engine co-development

---

### 🎮 Platform Certification

**[→ resources/platform-certification.md](./resources/platform-certification.md)**

Platform certification is the #1 schedule risk for AAA launches — this single document covers it:

- **Per-platform detail**: PS TRC ~200 / Xbox XR ~150 / Switch Lotcheck / Steam Partner / Apple App Review / Google Play / EGS
- **Top 10 PS5 rejection causes**: save crash, trophy errors, region lock, accessibility, etc.
- **XAGs (Xbox Accessibility Guidelines) — 120+**: Input · Audio · Visual · Cognitive · Motor categories with representative XAG numbers
- **Nintendo Lotcheck specifics**: dual-mode (Docked vs Handheld) performance, JoyCon combination matrix, parental control compliance
- **Rating bodies compared**: ESRB / PEGI / CERO / USK / GRAC (Korea) / ACB / China 판호 — fees, turnaround, submission method
- **Regional regulation**: Korea probability disclosure (GIPA, effective 2024-03-22), China 판호 system, Belgium loot box ban
- **Common cross-platform fail reasons (Top 20)**: rejection causes that recur across platforms
- **Cert timeline**: Gold-master 4 weeks before launch, parallel submission across 3 regions, separate Day-1 patch submission

---

### 🔁 Live Ops Playbook

**[→ resources/live-ops-playbook.md](./resources/live-ops-playbook.md)**

Launch is Day One — a 3-to-10-year live service operations playbook:

- **Service model taxonomy**: Season-based (Fortnite, Apex), Expansion (FF14, WoW), Episodic, Gacha, Hybrid
- **Standard 8–12 week season structure**: Week-by-week event placement with examples from Fortnite, Destiny 2 Episodes, FFXIV cadence
- **Full KPI dashboard**:
  - Engagement: DAU/MAU, sticky ratio, D1/D7/D30 retention
  - Monetization: ARPDAU, ARPPU, conversion, LTV, whale share
  - Economy: inflation index, source/sink ratio, rarity drift
  - Operational: crash-free rate, SLA, MTTR
- **Anti-cheat comparison**: Easy Anti-Cheat / BattlEye / Vanguard / Denuvo / VAC — kernel-level tradeoffs
- **Launch Disaster Recovery**: 3-year Cyberpunk recovery, 8-year No Man's Sky redemption, FFXIV's "A Realm Reborn" full reboot
- **Recovery Failed**: Anthem Next (cancelled 2021, servers off 2026.01), Marvel's Avengers (no recovery attempted, EOL 2023.09), Battleborn / Lawbreakers / Babylon's Fall — three-factor success pattern
- **Sunset Playbook**: D-180 to D+30 service-shutdown checklist (Concord 14-day closure, WildStar, P.T. cases)
- **Monetization Compliance**: Korea probability disclosure 2024.03, China 판호, Belgium total ban, FTC Epic Games $520M settlement (2022.12)
- **Asia Live Service Cases**: Korean MMOs (Lineage, MapleStory ₩116억 2024 settlement, Lost Ark, Umamusume KR protests) and Chinese gacha/SLG (HoYoverse cadence, PUBG Mobile vs Peacekeeper Elite, Honor of Kings, SLG server wars)
- **A/B testing operations**: Riot, Supercell, Epic — traffic allocation, evaluation metrics, decision standards

---

## How to Use This Repo

### As a Claude System Prompt

Paste [SKILL.en.md](./SKILL.en.md) (English) or [SKILL.md](./SKILL.md) (Korean) before your message to Claude to activate full game-designer mode. Claude can then:

- Write complete 10-section GDDs
- Generate HTML artifact game UI prototypes instantly
- Run balance simulations and suggest curve adjustments
- Critique narrative structure against established frameworks
- Write Ink/Yarn Spinner dialogue scripts

### For Solo Indie Developers

1. **SKILL.en.md** → system prompt for all game design work
2. **resources/narrative-design.md** → pick your dialogue tool and script format
3. **resources/game-balancing.md** → copy the progression formulas into a spreadsheet
4. **resources/marketing-qa.md** → run the launch checklist 3 months before release

### For Team Leads

1. **resources/famous-gdds.md** → required reading for new team members
2. **resources/postmortems.md** → retrospective reference ("what has gone wrong before?")
3. SKILL GDD template → standard format for all new project documents

### For AAA / Large Studios

1. **resources/production-pipeline.md** — Use as a template substitute or cross-check for internal pre-prod / production / cert timelines. The greenlight rubric can be applied directly to internal greenlight reviews.
2. **resources/platform-certification.md** — A pre-cert self-audit checklist for QA leads and producers. Use it as a self-audit baseline before first submission. Share regional regulation entries (Korea probability disclosure, China 판호) with publishing/legal teams.
3. **resources/live-ops-playbook.md** — KPI / sunset / A/B framework for live ops directors and PMs. Use the disaster-recovery cases for risk reviews on new projects.
4. **resources/game-balancing.md** — Cross-check the PvP ELO/MMR, gacha pity, and idle cost-curve formulas against your existing balance team's formulas.

### For Students

1. Read all postmortems — honest game design education
2. Study famous GDDs — understand the gap between plan and reality
3. Apply balancing formulas to class projects before guessing numbers
4. Production pipeline — a "how AAA actually works" primer for industry-bound students

---

## Contributing

Contributions are welcome. This repo grows through depth, not breadth.

**We accept:**
- New entries with explanation + key lesson (not just links)
- New resource files for uncovered topics
- Corrections to outdated information or broken links

**We don't accept:**
- Personal game portfolio items
- Promotional content
- Link dumps without context or analysis
- Material that violates platform NDAs (Sony DevNet, Xbox XR, Nintendo Lotcheck, etc.)

**Standard:** Every entry should answer: *"What will a designer learn from this that they couldn't get from just Googling the title?"*

To contribute: Fork → Branch (`resource/your-topic`) → Add content → Pull Request with description. See [CONTRIBUTING.md](./CONTRIBUTING.md) for full standards and [CODE_OF_CONDUCT.md](./CODE_OF_CONDUCT.md) for community expectations.

---

## License

MIT License — see [LICENSE](./LICENSE) for details.

## Trademarks & Legal Notice

All product names, game titles, studio names, and logos referenced in this repository (including but not limited to PlayStation, Xbox, Nintendo Switch, Steam, Epic Games, Unity, Unreal, and any specific game titles) are **trademarks of their respective owners**. This repository is not affiliated with, endorsed by, or sponsored by any of these companies. References are made for educational and analytical purposes only.

This repository is **not legal, regulatory, or contractual advice**. Platform certification requirements, regional regulations (loot-box laws, ratings boards, probability disclosure rules), and publishing contracts change frequently and vary by jurisdiction. Consult official platform documentation, qualified legal counsel, and current regulatory texts before acting on any information here.

---

*Inspired by [awesome-design](https://github.com/gztchan/awesome-design) (★15k+). Applied to the craft of game design.*
