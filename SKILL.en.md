# SKILL: Game Design Expert — World-Class Game Designer Role

> 🇰🇷 Korean version: [SKILL.md](./SKILL.md)
> This document is the English adaptation. The Korean original remains canonical for KR-specific cases (regulation, market, language); the English version is calibrated for international readers and adds Western-market context where helpful.

---

## Role Definition

A Claude that loads this skill operates as a **world-class game designer** combining the following simultaneous competencies:

- **Systems Designer** — Mechanics, loops, and balance
- **Narrative Designer** — Worldbuilding, story, and character arcs
- **UX/UI Designer** — Player experience flow and interface
- **Product Manager** — MVP scope, monetization strategy, roadmap
- **Visual Director** — Art direction, color theory, typography

**Reference standards**: design philosophy at the level of Miyamoto, Will Wright, Jonathan Blow, Jenova Chen, Hideo Kojima, and modern voices like Amy Hennig, Neil Druckmann, Yoko Taro, Tetsuya Mizuguchi, and Yoshi-P.

---

## Game Design Principles Distilled from Awesome Design

### 🎨 Color Theory

Principles for expressing emotion and worldbuilding through color:

- **Palette consistency**: Material Design–style three-tier hierarchy (Primary / Secondary / Accent)
- **Emotion mapping**: Color-to-emotion (red = tension/danger, blue = exploration/calm, gold = reward/achievement)
- **Contrast accessibility**: Colorable's 4.5:1 foreground-to-background luminance ratio (WCAG AA minimum)
- **Gradient layering**: WebGradients-style multi-color gradients for atmospheric depth
- **Cultural palettes**: Reference Nippon Colors (Japanese tradition), Chinese Colors, or Pantone Color of the Year for worldbuilding fidelity
- **Brand color discipline**: Single authoritative hex codes across UI, art, and marketing (Brand Colors–style database)

**Tool references:**
- [Coolors](https://coolors.co/) — palette generation
- [uiGradients](https://uigradients.com/) — gradient inspiration
- [Color Hunt](http://colorhunt.co/) — trending palettes
- [Paletton](http://paletton.com/) — complementary/analogous calculations
- [Nippon Colors](http://nipponcolors.com/) — traditional Japanese palette

### 🔤 Typography

Principles for legibility and tone in game text:

- **Hierarchy**: Four-level scale (Title / Header / Body / Caption)
- **Genre fit**: Typewolf-style genre-appropriate selection (fantasy = serif, sci-fi = sans-serif, horror = display)
- **Readability first**: Butterick's *Practical Typography* — line height 1.4–1.6, careful tracking
- **Pairings**: Google Font Combinations–style two-font (heading + body) systems
- **Multi-language**: Always specify separate Korean / Japanese / Chinese font stacks for CJK markets; ensure variable-width handling for Arabic/Hebrew if applicable

**Tool references:**
- [Google Fonts](https://fonts.google.com/) — free web fonts
- [Adobe Fonts](https://fonts.adobe.com/) — premium fonts
- [Font Squirrel](https://www.fontsquirrel.com/) — commercial-free
- [Game Icons](http://game-icons.net/) — game-specific icons

### 🎮 UX Patterns

Core principles for player-experience design:

- **Zero Friction Onboarding**: Krug's *Don't Make Me Think* — surface the core loop within the first 5 minutes
- **Mental Model alignment**: respect interaction patterns the player already expects from the genre
- **Hick's Law**: limit choices to 3–5 at a time
- **Fitts's Law**: place critical buttons large and at screen edges
- **Feedback Loop**: every player action gets immediate visual/audio/haptic feedback
- **Progressive Disclosure**: reveal complex systems in stages
- **Empty State Design**: design empty inventories and fresh-start states with intent
- **Error Prevention**: confirmation dialogs before destructive actions; undo where possible

**Tool references:**
- [UX Project Checklist](http://uxchecklist.github.io/)
- [Little Big Details](http://littlebigdetails.com/)
- [Pttrns](https://pttrns.com/) — mobile UI patterns
- [UX Movement](http://uxmovement.com/)

### ✨ Animation & Motion

Principles that make game feedback land:

- **Disney's 12 Principles**: squash & stretch, anticipation, follow-through
- **"Juice"**: every interaction earns particles, shake, scale punches
- **Easing curves**: prefer ease-in-out and spring curves over linear
- **60 fps baseline**: design every animation against a 60 fps target
- **State transitions**: 150–300 ms transitions between UI states
- **Micro-interactions**: icon clicks, count-up numbers, progress bar fills

**Tool references:**
- [Adobe After Effects](http://www.adobe.com/products/aftereffects.html)
- [Framer X](https://framer.com/) — interactive prototypes
- [Principle](http://principleformac.com/)
- [Haiku](https://www.haiku.ai/)

### 🖼️ Inspiration & References

- [Dribbble](https://dribbble.com/) — game UI trends
- [Behance](https://www.behance.net/) — art and UX portfolios
- [Awwwards](https://www.awwwards.com/) — interactive design showcase
- [Game Icons](http://game-icons.net/) — 4,000+ free game icons
- [Codrops](https://tympanus.net/codrops/) — creative interaction reference

### 🎨 Icons & Assets

- [Game Icons](http://game-icons.net/) — game-specific SVG icons
- [The Noun Project](https://thenounproject.com/) — universal icons
- [Material Design Icons](https://materialdesignicons.com/) — UI icons
- [Font Awesome](http://fontawesome.io/) — generic UI icons
- [Simple Icons](https://simpleicons.org/) — brand icons

### 📐 Prototyping

- [Figma](https://www.figma.com/) — UI/UX collaboration (recommended default)
- [InVision](https://www.invisionapp.com/) — clickable prototypes
- [Protopie](https://www.protopie.io/) — advanced interaction prototyping
- [Marvel](https://marvelapp.com/) — fast wireframes

---

## Standard GDD Template

All game design documents follow this structure:

```
# [Game Name] — [One-line concept]

## 1. Game Overview
  1.1 Core concept (2–3 sentence elevator pitch)
  1.2 Genre & platform
  1.3 Target player (named persona)
  1.4 Three differentiators
  1.5 Three reference games (and what is borrowed)

## 2. Core Game Loop
  2.1 Core loop diagram (text flowchart)
  2.2 Meta loop (between sessions)
  2.3 Game over conditions & rewards

## 3. Systems
  3.1 Core mechanics (detailed)
  3.2 Supporting mechanics
  3.3 Economy (resource in/out flow)
  3.4 Progression (level / unlock / upgrade)

## 4. Content Design
  4.1 Map / level structure
  4.2 Enemy & boss design
  4.3 Items / skills catalog
  4.4 Story & worldbuilding

## 5. UX / UI
  5.1 Screen flow
  5.2 HUD layout
  5.3 Menu structure
  5.4 Accessibility considerations

## 6. Art Direction
  6.1 Visual concept & references
  6.2 Color palette (Primary/Secondary/Accent/Neutral)
  6.3 Typography stack
  6.4 Animation guidelines

## 7. Monetization
  7.1 Business model
  7.2 Monetization touch points
  7.3 Value proposition
  7.4 Ethical considerations

## 8. MVP Scope
  8.1 Must-have (in MVP)
  8.2 Nice-to-have (excluded from MVP)
  8.3 Priority matrix

## 9. Development Roadmap
  9.1 Milestones
  9.2 Risks
  9.3 Success metrics (KPIs)

## 10. Appendix
  10.1 Glossary
  10.2 References
  10.3 Change log
```

---

## Game Mechanic Taxonomy

### Core Mechanic Types

| Type | Definition | Example |
|------|------|------|
| **Locomotion** | How characters/objects move | 8-direction, physics-based, grid |
| **Combat** | Resolving conflict with enemies | Real-time action, turn-based, rhythm |
| **Collection** | Acquiring items/resources | Drops, farming, crafting |
| **Construction** | Building structures/systems | Tower, city, character build |
| **Exploration** | Discovering space | Procedural, metroidvania |
| **Puzzle** | Logical problem solving | Match, physics, sequence |
| **Management** | Resource/time optimization | Idle, tycoon, RTS |
| **Social** | Player-to-player interaction | PvP, co-op, trading |

### Progression Types

| Type | Characteristic | Suited Genres |
|------|------|------|
| **Vertical** | Stat growth, item tiers | RPG, MMORPG |
| **Horizontal** | Variety expansion, more options | Builder, sandbox |
| **Cyclical** | Reset with permanent gains | Roguelike, Idle |
| **Branching** | Different paths from choices | RPG, visual novel |

---

## Monetization Framework

### Business Model Selection Matrix

| Model | Suited Genres | Retention Required | Revenue Stability |
|------|------|------|------|
| **Paid** | Single-player, indie | Low | Medium |
| **F2P + IAP** | Mobile, casual | High | High |
| **F2P + Cosmetic** | Multiplayer | High | Medium |
| **Subscription** | GaaS, MMO | Very high | Very high |
| **Battle Pass** | Live service | High | High |
| **Premium + DLC** | AAA, mid-core | Medium | Medium |

### Monetization Design Principles

1. **Ethical Monetization** — purchases must not obstruct gameplay (avoid pay-to-win)
2. **Value Clarity** — players must clearly see what they receive before paying
3. **Minimize FOMO** — limited-time content should reward time, not gameplay advantage
4. **Whaling Protection** — offer monthly spend caps as opt-in
5. **Cosmetics First** — cosmetics over gameplay-affecting items

### Monetization Funnel

```
Awareness → Install → First Session → Retention → First Purchase → LTV Maximization
   ↓          ↓           ↓                ↓              ↓                 ↓
Marketing   UAC      Onboarding UX    Core Loop     "Aha" Moment   Subscription/BP
```

---

## MVP Scope Methodology

### RICE Prioritization Score

```
RICE Score = (Reach × Impact × Confidence) / Effort
```

- **Reach** — number of affected players (1–10)
- **Impact** — uplift to game experience (0.25 / 0.5 / 1 / 2 / 3)
- **Confidence** — % certainty of estimate (20–100%)
- **Effort** — development cost in person-weeks

### MVP Feature Bucketing

**Must Have (in MVP)**
- Core game loop (one core mechanic)
- Basic UI/HUD (lives, score, progress)
- Tutorial (first 5 minutes)
- Save/load
- Basic audio (1 BGM, core SFX)

**Should Have (post-launch v1)**
- Content volume (10+ levels)
- Meta progression (permanent upgrades)
- Achievements
- Leaderboards

**Could Have (post-launch v2)**
- Social features
- Customization
- Season pass

**Won't Have (out of scope this version)**
- Multiplayer (separate project)
- User-generated content
- Esports features

---

## GDD Quality Standards

When writing a GDD, Claude must adhere to:

### Design Quality

1. **Specificity** — replace vague phrases ("fun combat") with numbers and mechanics ("3 action points per turn, basic attack costs 1")
2. **Visualization** — render major systems as ASCII diagrams or tables
3. **References** — every mechanic cites the prior game it borrows from
4. **Player-first framing** — describe player experience before technical detail
5. **Consistency** — color/typography/UX principles stay coherent across the document

### Document Standards

- English by default; Korean (or other languages) parallel sections for region-specific GDDs
- Strict Markdown
- 800–1,500+ characters per major section
- Tables, code blocks, and ASCII diagrams generously
- Emoji section markers for scannability

---

## Reference Resources

- [Game Icons](http://game-icons.net/) — 4,000+ free game icons
- [Material Design](https://material.io/guidelines/) — UI guidelines
- [Apple Human Interface Guidelines](https://developer.apple.com/ios/human-interface-guidelines/) — mobile UX standards
- [Smashing Magazine](https://www.smashingmagazine.com/) — UX/UI articles
- [Codrops](https://tympanus.net/codrops/) — interaction patterns
- [Awwwards](https://www.awwwards.com/) — top design showcases
- [Dribbble](https://dribbble.com/) — game UI trends
- [Little Big Details](http://littlebigdetails.com/) — micro-interaction inspiration
- [Ant Design](http://ant.design) — component philosophy

---

## Claude Design System Prompt Philosophy

How Claude is framed as a professional game designer:

### Role Layering

When handling a game design request, Claude operates through this hierarchy:

```
Level 1: Game Designer (functional design)
Level 2: UX Designer (player experience)
Level 3: Visual Director (art / UI direction)
Level 4: Product Manager (business value)
```

Every deliverable is structured **player-first → system-second**.

### HTML Artifact Game UI Prototyping

Claude can produce instant HTML-artifact prototypes using:

```html
<!-- Recommended stack -->
- HTML5 Canvas / SVG — game render surface
- CSS Custom Properties — theme color/font variables
- Vanilla JS / requestAnimationFrame — game loop
- Web Audio API — SFX / BGM synthesis
- CSS Grid/Flexbox — HUD layout
- Tailwind CSS (CDN) — fast UI components
```

**Prototype types:**

| Prototype | Core tech | Validation goal |
|---|---|---|
| Core loop test | Canvas + JS game loop | Is it fun? |
| HUD/UI layout | CSS Grid + dummy data | UX flow |
| Menu/inventory | React/HTML components | Information architecture |
| Effects / juice | Canvas particle system | Feel |
| Economy simulator | JS numerical sim | Balance test |

**Production guidelines:**
- Single HTML file, only CDN externals (cdnjs.cloudflare.com)
- Responsive layout for mobile + desktop
- Use realistic dummy values for grounded feel
- Interactive buttons/sliders for instant feedback

---

## Narrative Design Methodology

### Story Structure Frameworks

#### Save the Cat Beat Sheet (game adaptation)

Blake Snyder's structure adapted for interactive media:

```
1. Opening Image (1%) — first impression of the world; pre-tutorial mood
2. Theme Stated (5%) — what the game is about (delivered in NPC dialogue)
3. Setup (1–10%) — protagonist's lack/desire, world introduction
4. Catalyst (10%) — first major event (quest trigger)
5. Debate (10–25%) — player hesitation (weight of choice)
6. Break Into Two (25%) — world expands, new region/system unlocked
7. B Story (30%) — supporting character arc, emotional support line
8. Fun and Games (30–55%) — the core content, "promise of the premise"
9. Midpoint (50%) — false victory or false defeat; stakes raised
10. Bad Guys Close In (55–75%) — protagonist pressed; difficulty peak
11. All is Lost (75%) — lowest point; mentor death or worst choice
12. Dark Night of the Soul (75–80%) — internal reflection, emotional climax
13. Break Into Three (80%) — twist or solution discovered, final breakthrough
14. Finale (80–99%) — final boss, climactic sequence
15. Final Image (99–100%) — changed world, ending sequence
```

#### Hero's Journey (Joseph Campbell / Christopher Vogler)

In games, the player is the hero and the game world is the special world:

```
Ordinary World → Call to Adventure → Refusal → Meeting Mentor
→ Crossing First Threshold → Tests/Allies/Enemies → Approach Inmost Cave
→ Ordeal → Reward (Sword) → Road Back → Resurrection → Return with Elixir
```

**Game implementation hooks:**
- "Ordinary World" = starting town/state
- "Mentor" = tutorial NPC or guide system
- "Inmost Cave" = mid-game dungeon or peak challenge
- "Resurrection" = post-game-over respawn or consequence of choice

### Dialogue System Patterns

#### 1. Dialogue Wheel (Mass Effect style)
```
Pros: Intuitive, emotional state visible at a glance
Cons: Limited to 4–8 choices
Suited: Action RPGs, real-time conversation
Build: Radial menu + timed options
```

#### 2. Linear Dialogue Tree (classic RPG)
```
Pros: Rich branching, deep narrative
Cons: Massive writing effort, dead-end risk
Suited: Visual novels, JRPGs, point-and-click
Build: Yarn Spinner / Ink scripts
```

#### 3. Keyword System (Disco Elysium style)
```
Pros: Free exploration, world-depth feel
Cons: Risk of player getting lost
Suited: Detective / mystery, world-exploration games
Build: Tag-based dialogue filter
```

#### 4. Silent Protagonist (Dark Souls style)
```
Pros: Maximum player projection
Cons: Hard to build emotional connection
Suited: Action, atmosphere-driven games
Build: Heavy environmental storytelling required
```

#### Dialogue Writing Principles (game writer standard)

1. **Subtext first** — NPCs always have something unspoken
2. **Distinct voices** — each NPC has a unique vocabulary, rhythm, concern
3. **Information triplet** — repeat critical info 3 times (introduce → reinforce → confirm)
4. **Illusion of choice** — even when outcomes converge, preserve player agency in process
5. **Emotional state memory** — prior choices echo in NPC reactions

### Branching Narrative Methodology

#### Narrative Structure Types

```
1. Railroad
   A → B → C → D → Ending
   Example: most JRPGs
   Pros: strong story, production efficient
   
2. Multiple Endings
   A → B → C → [Ending1/Ending2/Ending3]
   Example: Chrono Trigger, Detroit: Become Human
   Pros: replay value, choice weight
   
3. Branching
   A → [B1/B2] → [C1/C2/C3] → D
   Example: Disco Elysium, Planescape: Torment
   Pros: extreme freedom, world depth
   Cons: production cost grows exponentially
   
4. World State (persistent consequences)
   Choices accumulate in the world
   Example: Dragon Age, The Witcher 3
   Pros: realism, player ownership
   
5. Episodic
   Independent episodes + cumulative state
   Example: Life is Strange, The Walking Dead
   Pros: distributed production, feedback-driven
```

#### Ink/Inky Script Pattern Example

```ink
=== meeting_guard ===
The guard blocks the path.
* [Show your ID]
    -> show_id
* [Turn back]
    -> retreat
* {has_bribe} [Offer a bribe]
    -> bribe_guard

=== show_id ===
The guard inspects your ID.
{player_has_valid_id:
    - "Pass through." -> pass_through
    - "This is a forgery." -> caught
}
```

### Worldbuilding Methodology

#### Iceberg Theory

What players see = 10% of the iceberg; the other 90% must remain submerged but consistent:

```
[Above the surface — player experience]
- Main story line
- NPC dialogue
- Environmental art / level design
- Item descriptions

[Below the surface — designer-only]
- Deep history (millennia)
- Political structure of factions/nations
- Language, religion, culture systems
- Detailed character backstories
- Economic system fundamentals
- Geography & ecology
```

#### Worldbuilding Consistency Checklist

- [ ] Exceptions to physical laws are clearly defined
- [ ] Every faction's motivation is rational
- [ ] Historical events explain the present state
- [ ] Cultural and technological levels match
- [ ] Scarcity principle (no drama if everything is abundant)

---

## Balancing Theory in Depth

### Machinations Framework

Joris Dormans (2012) — visualizing game economies as diagrams:

#### Core Node Types

```
[Source] ── produces ──> (Pool) ──> consumes ──> [Drain]
   ↓                       ↓
   └── Converter ──> another Pool

Symbols:
○ Pool: resource container
□ Source: resource generator
△ Drain: resource sink
◇ Converter: resource transformer
● Trader: resource exchanger
```

#### Feedback Loop Types

```
Positive feedback (reinforcing):
gold → gear → more gold acquisition
→ Effect: snowball, hard to catch up
→ Counter: taxes, diminishing returns, enemy scaling

Negative feedback (balancing):
high score → tougher enemies → harder to maintain
→ Effect: stabilization, soft ceiling
→ Counter: skill gap allowance, expressive freedom
```

#### Economic Loop Example (RPG)

```
[Quest Complete]
    ↓ XP
(XP Pool) → Level Up → [Stat Increase]
    ↓ Gold                    ↓
(Resource Pool) → Shop → [Equipment]
    ↑                         ↓
[Inflation prevention]   Defeat tougher enemies
Drains: repair / tax / consumables
```

### Numerical Balancing Formulas

#### RPG Stat Scaling

```
HP formula (geometric growth):
HP(level) = BASE_HP × (1 + GROWTH_RATE) ^ level

Example: BASE_HP=100, GROWTH_RATE=0.08
Lv1: 100 / Lv10: 215 / Lv50: 4,690 / Lv99: 195,360

Damage formula (logarithmic):
DMG(level) = BASE_DMG × log(level + 1) × SCALE

TTK (Time to Kill) targets:
- Trash: 3–5 seconds at player DPS
- Elite: 10–20 seconds
- Boss: 60–180 seconds
```

#### Balance Verification Matrix

| Stage | Method | Goal |
|---|---|---|
| Theoretical | Spreadsheet math | Remove extremes |
| Bot simulation | Algorithmic playthroughs | Statistical distribution |
| Internal playtest | Team play | Intuitive feel |
| External playtest | Target audience | Subjective difficulty calibration |
| Live data | Analytics dashboard | Retention / drop-off points |

### PvP Balancing Theory

#### ELO System

```
new_ELO = current_ELO + K × (actual_result − expected_result)

expected_result = 1 / (1 + 10^((opponent_ELO − my_ELO) / 400))

K-value tuning:
- New players (< 30 games): K=40 (fast initial placement)
- Standard players: K=20
- Top players (ELO 2,400+): K=10 (stability priority)
```

#### MMR Tier Design Principles

1. **Distribution** — target % per tier (e.g., Bronze 30%, Silver 35%, Gold 25%, Platinum 8%, Diamond 2%)
2. **Match speed vs quality** — widen ELO range after 30s wait
3. **Duo penalty** — average ELO + offset (e.g., +100)
4. **Decay protection** — define inactivity grace period before MMR drops

### Idle Game Numerical Design

#### Progression Curve Design

```
Recommended upgrade-cost curve:
cost(n) = BASE_COST × MULTIPLIER ^ n

Example: BASE_COST=10, MULTIPLIER=1.15
Upgrade 1:  10 gold
Upgrade 5:  20 gold
Upgrade 10: 40 gold
Upgrade 20: 164 gold
Upgrade 50: 1,083 gold

Inflation prevention strategies:
- Soft cap: efficiency drops past a level
- Prestige system: reset + permanent bonus
- Bottleneck: only one resource throttles growth
```

#### Offline Progression Design

```
Offline gain formula:
offline_gain = online_rate × offline_time × efficiency_cap

Recommended efficiency caps:
- Casual: 100% (no offline penalty)
- Mid-core: 50% (encourages active play)
- Hardcore: 25% (active play required)

Recommended max offline accrual: 8–24 hours
(longer reduces incentive to log back in)
```

### Gacha / Random Reward Probability Design Ethics

#### Transparency Requirements (legal context)

| Region | Regulation | Requirement |
|---|---|---|
| **South Korea** | GIPA Enforcement Decree (effective 2024-03-22) | All probabilities must be disclosed in-app. Failure to comply with a corrective order: up to 2 years imprisonment or KRW 20 million fine |
| **China** | Online game regulation (2017–) | Maximum-rarity guarantee within 50 pulls; full probability disclosure |
| **Belgium** | Gaming Act | **Loot boxes effectively prohibited** (most Western games exclude BE region) |
| **Netherlands** | KSA regulation | FIFA pack-opening prohibited (2020) |
| **United Kingdom** | UKGC self-regulatory guidance | Probability disclosure + parental notice |
| **EU** | Pending | Disclosure and age-restriction discussions ongoing |
| **United States** | State-by-state | No federal standard; FTC settlements (Epic Games $520M total, 2022.12) set precedent |

#### Ethical Design Guidelines

1. **Probability disclosure** — show drop rates per rarity tier in-app
2. **Pity ceiling** — maximum-rarity guarantee within N pulls
3. **Duplicate handling** — alternate reward when duplicate received
4. **Spend caps** — opt-in monthly spending limit
5. **Underage protection** — age verification + guardian controls
6. **Avoid pay-to-win** — gacha rewards should not provide direct PvP advantage

#### Psychological Mechanics Designers Must Recognize

```
FOMO (Fear of Missing Out) — limited-time items drive compulsive purchase
Variable Reward — irregular rewards trigger addiction (slot machine principle)
Sunk Cost — "I've spent this much, I have to keep going"
Social Proof — "your friend pulled it" notifications
```

**Responsible design**: be aware these mechanics exist and intentionally avoid exploitative tuning.

---

## Companion Resources in This Repository

This skill works best when paired with:

- [resources/famous-gdds.md](./resources/famous-gdds.md) — Doom Bible, Diablo, BioShock, Deus Ex, Monaco, The Sims design history
- [resources/postmortems.md](./resources/postmortems.md) — Stardew Valley, Hollow Knight, Celeste, Undertale, Hades, TLOU, GoW, Elden Ring postmortems
- [resources/narrative-design.md](./resources/narrative-design.md) — tools (Twine, Ink, Yarn Spinner), theory, dialogue patterns, worldbuilding
- [resources/game-balancing.md](./resources/game-balancing.md) — Machinations, numerical scaling, PvP ELO/MMR, gacha ethics
- [resources/art-direction.md](./resources/art-direction.md) — pixel art, UI/UX, color theory, sound design, animation
- [resources/marketing-qa.md](./resources/marketing-qa.md) — launch checklist, Steam optimization, trailer production, QA, launch strategy
- [resources/production-pipeline.md](./resources/production-pipeline.md) — AAA pre-prod / production / cert / launch / live with greenlight rubric, milestone payments, real-world reboots
- [resources/platform-certification.md](./resources/platform-certification.md) — PS TRC, Xbox XR + XAGs (120+), Nintendo Lotcheck, Steam, Apple/Google policies, regional ratings
- [resources/live-ops-playbook.md](./resources/live-ops-playbook.md) — service models, season structure, KPI dashboards, anti-cheat, sunset playbook, recovery success/failure cases, Korea/China case studies

---

*This skill reinterprets [gztchan/awesome-design (★15k+)](https://github.com/gztchan/awesome-design) for the craft of game design.*
*Source: https://github.com/gztchan/awesome-design*
