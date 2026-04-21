# 게임 기획서 풀 (Game Design Pool)

**최종 업데이트**: 2026년 4월 21일

---

## 📌 섹션 1: 개요

### 게임 기획서 풀 소개

이 풀(Pool)은 **기존 게임 15개 + 신규 기획 10개**으로 구성된 종합 게임 디자인 아카이브입니다.

**기존 게임**은 HTML5 Canvas, TypeScript, Godot 등 다양한 기술 스택으로 구현된 **프로토타입, 플랫폼, 생성기, 블록체인 게임**을 포함합니다.

**신규 기획**은 **Tower Defense, Roguelike, Match-3, Deck Building, City Builder** 등 시장 공백을 메우기 위한 10가지 메카닉 기획 문서입니다.

### 폴더 구조

```
game-docs/
├── README.md                          (이 파일)
├── [기존 게임 폴더들]
│   ├── game-flip-gravity/
│   ├── horse-racing-prototype/
│   ├── horse-racing/
│   ├── game-gen/
│   ├── ball-sort-puzzle/
│   ├── mahjong-zen/
│   ├── rhythm-pulse-prototype/
│   ├── idle-hero/
│   ├── game-v6/
│   ├── game-v9/
│   ├── game-v10/
│   ├── game-proposals/
│   ├── game-hub/
│   ├── games/
│   └── p0-colosseum-w2/
└── new-concepts/                      (신규 기획 10개)
    ├── tower-defense-voidwatch/
    ├── roguelike-echo-depths/
    ├── match3-astral-cascade/
    ├── deckbuild-runeforge/
    ├── citybuilder-neon-district/
    ├── battleroyal-nanoswarm/
    ├── autochess-starfield-tactics/
    ├── dungeon-abyssal-gate/
    ├── clicker-cosmic-forge/
    └── survival-last-signal/
```

---

## 🕹️ 섹션 2: 메카닉별 분류 (기존 게임)

### 🎮 Arcade / Endless Runner

- **[Gravity Flip](./game-flip-gravity/)** — 탭 한 번으로 중력 반전, 네온 사이버펑크 원버튼 서바이벌

### 🏇 Racing / Betting Simulation

- **[Derby Dash](./horse-racing-prototype/)** — 9마리 말 + 파리뮤추얼 배팅 HTML5 Canvas 프로토타입
- **[Derby Dash Platform](./horse-racing/)** — TypeScript 기반 경마 데이터 분석·자동화 플랫폼
- **[Derby Dash Gen](./game-gen/)** — Phase 6~7 확장 기획 (10호마, 신규 트랙, 통계)

### 🧩 Puzzle / Sort & Stack

- **[Ball Sort Puzzle](./ball-sort-puzzle/)** — 색깔 공 정렬, 튜브 이동 퍼즐
- **[Mahjong Zen](./mahjong-zen/)** — 마작 솔리테어, 힌트/셔플 시스템

### 🎵 Rhythm / Tap Timing

- **[Rhythm Pulse](./rhythm-pulse-prototype/)** — 3레인 낙하 비트, 피버 모드, 절차적 음악

### ⚔️ Idle / Auto-Battle RPG

- **[Idle Hero](./idle-hero/)** — 영웅 수집 + 공명 진형 + 자동 배틀 (Godot 4)

### 🔧 Game Generator / Multi-genre

- **[Generator v6](./game-v6/)** — FPS모니터링·멀티터치·저장시스템 탑재 10게임 생성기
- **[Generator v9](./game-v9/)** — AI NPC·동적 난이도·점진 공개 10게임 생성기
- **[Generator v10](./game-v10/)** — 크로스플랫폼·반응형·A11y 10게임 생성기

### 📋 Proposal Collection

- **[Game Proposals](./game-proposals/)** — 20개 게임 기획 제안서 풀 (Puzzle 중심)

### 🏢 Platform / Game Hub

- **[Game Hub](./game-hub/)** — 360개 게임 운영 관리 허브
- **[Games Catalog](./games/)** — 600+ 게임 배포 카탈로그 (eastsea.xyz)

### ⛓️ Blockchain / Web3

- **[P0 Colosseum](./p0-colosseum-w2/)** — Rust 기반 EastSea Protocol 블록체인 콜로세움

---

## 🌟 섹션 3: 메카닉별 분류 (신규 기획 — new-concepts/)

### 🏰 Tower Defense

- **[Void Watch](./new-concepts/tower-defense-voidwatch/)** — 역장(力場) 타워 배치로 차원 균열을 방어하는 SF 타워 디펜스

### 🎲 Roguelike / Roguelite

- **[Echo Depths](./new-concepts/roguelike-echo-depths/)** — 절차적 생성 지하 던전, 죽으면 리셋되는 퍼즐-액션 로그라이크

### 💎 Match-3 / Gem Swap

- **[Astral Cascade](./new-concepts/match3-astral-cascade/)** — 별자리 테마 보석 매치-3, 체인 콤보와 스킬 시스템

### 🃏 Deck Building / Card Game

- **[Rune Forge](./new-concepts/deckbuild-runeforge/)** — 룬 카드를 조합해 덱을 진화시키는 로그라이크 덱빌딩

### 🏙️ City Builder / Tycoon

- **[Neon District](./new-concepts/citybuilder-neon-district/)** — 사이버펑크 도시를 설계·운영하는 캐주얼 시티 빌더

### ⚡ Battle Royale / Last Stand

- **[Nano Swarm](./new-concepts/battleroyal-nanoswarm/)** — 100명의 나노봇이 격돌하는 웹 기반 배틀로얄

### ♟️ Auto Chess / Tactical RPG

- **[Starfield Tactics](./new-concepts/autochess-starfield-tactics/)** — 8×8 우주 전장, 자동 전투 오토체스 + 시너지 조합

### 🗺️ Dungeon Crawler / Action RPG

- **[Abyssal Gate](./new-concepts/dungeon-abyssal-gate/)** — 탑 뷰 던전 크롤러, 실시간 액션 + 아이템 빌드

### 🖱️ Clicker / Incremental

- **[Cosmic Forge](./new-concepts/clicker-cosmic-forge/)** — 우주를 창조하는 초월적 스케일 인크리멘탈 게임

### 🌲 Survival / Crafting

- **[Last Signal](./new-concepts/survival-last-signal/)** — 미지 행성 불시착, 자원 수집·제작으로 탈출을 준비하는 생존 게임

---

## 📊 섹션 4: 커버리지 갭 분석표

| 메카닉 카테고리 | 기존 게임 | 신규 기획 | 상태 |
|---|---|---|---|
| Arcade / Runner | Gravity Flip | — | ✅ 커버 |
| Racing / Betting | Derby Dash, Derby Dash Platform, Derby Dash Gen | — | ✅ 커버 |
| Puzzle / Sort | Ball Sort Puzzle, Mahjong Zen | — | ✅ 커버 |
| Rhythm | Rhythm Pulse | — | ✅ 커버 |
| Idle / Auto-Battle RPG | Idle Hero | — | ✅ 커버 |
| **Tower Defense** | ❌ 없음 | Void Watch | 🆕 신규 |
| **Roguelike / Roguelite** | ❌ 없음 | Echo Depths | 🆕 신규 |
| **Match-3 / Gem Swap** | (제안서만) | Astral Cascade | 🆕 신규 |
| **Deck Building** | ❌ 없음 | Rune Forge | 🆕 신규 |
| **City Builder / Tycoon** | ❌ 없음 | Neon District | 🆕 신규 |
| **Battle Royale** | ❌ 없음 | Nano Swarm | 🆕 신규 |
| **Auto Chess** | ❌ 없음 | Starfield Tactics | 🆕 신규 |
| **Dungeon Crawler** | ❌ 없음 | Abyssal Gate | 🆕 신규 |
| **Clicker / Incremental** | (제안서만) | Cosmic Forge | 🆕 신규 |
| **Survival / Crafting** | ❌ 없음 | Last Signal | 🆕 신규 |
| Game Generator | Generator v6, v9, v10 | — | ✅ 커버 |
| Platform / Hub | Game Hub, Games Catalog | — | ✅ 커버 |
| Blockchain / Web3 | P0 Colosseum | — | ✅ 커버 |

---

## 📋 섹션 5: 전체 게임 목록 (가나다 순)

### 기존 게임 (15개)

1. **[Ball Sort Puzzle](./ball-sort-puzzle/)** — 색깔 공 정렬 퍼즐
2. **[Derby Dash](./horse-racing-prototype/)** — HTML5 Canvas 경마 프로토타입
3. **[Derby Dash Gen](./game-gen/)** — 경마 기획 확장 문서
4. **[Derby Dash Platform](./horse-racing/)** — TypeScript 경마 플랫폼
5. **[Game Hub](./game-hub/)** — 360개 게임 관리 허브
6. **[Game Proposals](./game-proposals/)** — 20개 기획안 제안서
7. **[Games Catalog](./games/)** — 600+ 게임 배포 카탈로그
8. **[Generator v6](./game-v6/)** — FPS모니터링 10게임 생성기
9. **[Generator v9](./game-v9/)** — AI NPC 10게임 생성기
10. **[Generator v10](./game-v10/)** — 크로스플랫폼 10게임 생성기
11. **[Gravity Flip](./game-flip-gravity/)** — 원버튼 Arcade 게임
12. **[Idle Hero](./idle-hero/)** — 자동 배틀 RPG (Godot 4)
13. **[Mahjong Zen](./mahjong-zen/)** — 마작 솔리테어
14. **[P0 Colosseum](./p0-colosseum-w2/)** — Rust 블록체인 콜로세움
15. **[Rhythm Pulse](./rhythm-pulse-prototype/)** — 3레인 리듬 게임

### 신규 기획 (10개)

16. **[Abyssal Gate](./new-concepts/dungeon-abyssal-gate/)** — 탑 뷰 던전 크롤러
17. **[Astral Cascade](./new-concepts/match3-astral-cascade/)** — 별자리 매치-3
18. **[Cosmic Forge](./new-concepts/clicker-cosmic-forge/)** — 우주 창조 인크리멘탈
19. **[Echo Depths](./new-concepts/roguelike-echo-depths/)** — 절차적 로그라이크
20. **[Last Signal](./new-concepts/survival-last-signal/)** — 미지 행성 생존 게임
21. **[Nano Swarm](./new-concepts/battleroyal-nanoswarm/)** — 나노봇 배틀로얄
22. **[Neon District](./new-concepts/citybuilder-neon-district/)** — 사이버펑크 시티 빌더
23. **[Rune Forge](./new-concepts/deckbuild-runeforge/)** — 로그라이크 덱빌딩
24. **[Starfield Tactics](./new-concepts/autochess-starfield-tactics/)** — 우주 오토체스
25. **[Void Watch](./new-concepts/tower-defense-voidwatch/)** — SF 타워 디펜스

---

## 🎯 사용 가이드

### 기존 게임 문서 참고
각 게임 폴더 내에는 다음과 같은 문서가 포함됩니다:
- `README.md` — 게임 개요, 메카닉, 기술 스택
- `DESIGN.md` (선택) — 상세 게임 디자인 문서
- `CODE.md` (선택) — 코드 구조 및 아키텍처

### 신규 기획 문서 열람
`new-concepts/` 폴더의 각 게임 기획은 다음을 포함합니다:
- 핵심 컨셉 및 USP (Unique Selling Point)
- 게임플레이 루프 및 메카닉
- 기술 요구사항 및 플랫폼
- 마켓 포지셔닝 및 타겟 오디언스

### 메카닉별 브라우징
위의 **섹션 2, 3**을 통해 관심 있는 메카닉별로 게임을 찾아볼 수 있습니다.

### 커버리지 분석
**섹션 4**의 표를 통해 시장에서 현재 커버하고 있는 메카닉과 신규 기획으로 채우는 공백을 한눈에 확인할 수 있습니다.

---

## 📈 통계

| 항목 | 수량 |
|---|---|
| **기존 게임** | 15개 |
| **신규 기획** | 10개 |
| **총 게임/기획** | 25개 |
| **커버 메카닉** | 18개 카테고리 |
| **기술 스택 다양성** | HTML5 Canvas, TypeScript, Godot 4, Rust, Web3 |

---

## 📞 문의 및 피드백

게임 기획서 풀에 대한 질문, 추가 기획, 또는 피드백은 게임 기획팀과 공유해 주시기 바랍니다.

**마지막 업데이트**: 2026년 4월 21일
