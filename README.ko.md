# Awesome Game Design 🎮

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)
[![Last Updated](https://img.shields.io/badge/Updated-April%202026-orange.svg)]()

> 🌐 **언어**: [English (README.md)](./README.md) · **한국어 (this file)**

> 게임 기획자를 위한 세계 최고 수준의 큐레이션 자료 — GDD 레퍼런스, 디자인 이론, 밸런싱 프레임워크, 내러티브 도구, 아트 디렉션, 마케팅, AAA 제작, 플랫폼 인증, 라이브 오퍼레이션을 망라합니다. [awesome-design](https://github.com/gztchan/awesome-design) 의 큐레이션 철학에서 영감을 받았습니다.

---

## 📌 이 저장소는 무엇인가?

**게임 기획자를 위한 종합 지식 베이스**입니다 — 인디 솔로 개발자부터 AAA 스튜디오 리드까지. 프로 기획자가 실제로 의존하는 이론·도구·역사적 GDD·실무 프레임워크를 모았습니다.

**공개 큐레이션 자료**로서, GitHub에서 가장 유용한 게임 디자인 레퍼런스가 되도록 유지됩니다. 모든 항목은 다음 한 가지 질문에 답합니다: *"제목만 구글링해서는 얻을 수 없는, 기획자가 이 자료에서 배울 핵심은 무엇인가?"*

---

## 📚 목차

- [SKILL — 게임 디자인 전문가 시스템 프롬프트](#skill)
- [Resources](#resources)
  - [유명 GDD](#-유명-game-design-documents)
  - [Postmortems](#-postmortems)
  - [Narrative Design](#-narrative-design)
  - [Game Balancing](#%EF%B8%8F-game-balancing)
  - [Art Direction](#-art-direction)
  - [Marketing & QA](#-marketing--qa)
  - [Production Pipeline (AAA)](#-production-pipeline-aaa)
  - [Platform Certification](#-platform-certification)
  - [Live Ops Playbook](#-live-ops-playbook)
- [활용 가이드](#%ED%99%9C%EC%9A%A9-%EA%B0%80%EC%9D%B4%EB%93%9C)
- [기여하기](#%EA%B8%B0%EC%97%AC%ED%95%98%EA%B8%B0)
- [상표 및 법적 고지](#%EC%83%81%ED%91%9C-%EB%B0%8F-%EB%B2%95%EC%A0%81-%EA%B3%A0%EC%A7%80)

---

## SKILL

**[→ SKILL.md (한국어)](./SKILL.md)** · **[→ SKILL.en.md (English)](./SKILL.en.md)** — Claude를 세계 최고 수준의 게임 기획자로 만드는 풀 시스템 프롬프트. 다음을 포함합니다:

- 역할 정의 (System Designer, Narrative Designer, UX Designer, PM, Visual Director)
- Awesome Design에서 추출한 게임 디자인 원칙 (색상 이론, 타이포그래피, UX 패턴, 애니메이션)
- GDD 작성 표준과 10섹션 템플릿
- 게임 메카닉 분류 체계
- 수익화 전략 프레임워크
- MVP 범위 정의 방법론 (RICE 스코어링)
- **Claude Design System Prompt 철학** — HTML 아티팩트 게임 UI 프로토타이핑
- **내러티브 디자인 방법론** — Save the Cat, Hero's Journey, 분기 내러티브 패턴
- **밸런싱 이론** — Machinations, 경제 루프, PvP ELO/MMR, 가챠 윤리

---

## Resources

### 📄 유명 Game Design Documents

**[→ resources/famous-gdds.md](./resources/famous-gdds.md)**

랜드마크 게임의 역사적 GDD와 디자인 문서, 그리고 각 문서에서 추출한 핵심 교훈:

| 게임 | 스튜디오 | 핵심 교훈 |
|---|---|---|
| **Doom Bible** | id Software (1992) | 내러티브 vs 순수 게임플레이 — 단순함을 선택하는 시점 |
| **Diablo** | Blizzard North (1994) | 문서보다 프로토타입 — 플레이테스트 중 턴제가 실시간으로 바뀐 사례 |
| **BioShock** | Irrational Games (2006) | 컷씬이 아닌 메카닉에 철학을 새기는 법 |
| **Deus Ex** | Ion Storm (1998) | 스크립트 분기가 아닌 열린 시스템을 통한 진정한 플레이어 자율성 |
| **Monaco** | Pocketwatch Games (2013) | 솔로 개발자의 인내심과 코옵 디자인의 역할 분화 |
| **The Sims** | Maxis (2000) | 의외의 재미를 따라가라 — 집보다 NPC가 더 흥미로웠던 이유 |

GDC Vault 링크, Game Developer Magazine 아카이브, 디자인 철학 분석, GDD 작성에 대한 보편적 교훈을 포함합니다.

---

### 🪦 Postmortems

**[→ resources/postmortems.md](./resources/postmortems.md)**

무엇이 통했고 무엇이 통하지 않았는가 — 인디 히트작부터 AAA 대작까지:

**인디:**
- **Stardew Valley** — 1인 4년 개발; 번아웃 리스크; 마케팅보다 폴리싱
- **Hollow Knight** — 스코프 확장 결정; 분위기 우선 설계; 무료 DLC를 통한 충성도
- **Celeste** — 접근성 표준이 된 Assist Mode; 메카닉이 곧 메타포; 개인적 진실
- **Undertale** — 장르 전복; 세이브 데이터를 내러티브로; 매체 특유의 스토리텔링
- **Hades** — 얼리 액세스를 공동 개발 도구로; 죽음을 스토리 구조에 통합

**AAA:**
- **The Last of Us** — 감정 우선 메카닉 설계; 동반자 AI 진화
- **God of War (2018)** — 원샷 카메라를 창의적 제약이자 정체성으로
- **Elden Ring** — 소울라이크 + 오픈 월드의 결합; PC 최적화 함정

GDC Vault 링크와 여러 postmortem에서 반복적으로 등장하는 패턴을 정리.

---

### 📖 Narrative Design

**[→ resources/narrative-design.md](./resources/narrative-design.md)**

도구, 이론, 대화 시스템 패턴:

**도구:** Twine, Ink/Inky (MIT), Yarn Spinner (Unity/Godot), articy:draft, Obsidian (월드 바이블)

**이론:**
- Save the Cat 15비트 시트의 인터랙티브 미디어 적용
- Hero's Journey 12단계와 게임 구현 노트
- 비선형 스토리텔링 단계: 코스메틱 선택 → 짧은 분기 → 월드 상태 → 시스템 내러티브

**대화 패턴:** 감정 스펙트럼 (Disco Elysium 스타일), 스킬 게이트 선택 (Fallout 스타일), 시간 제한 응답 (Mass Effect 스타일), 관계 상태 대화

**세계관 구축:** 빙산 이론, World Bible 챕터 템플릿, 환경 스토리텔링 기법 (Dead Space, Dark Souls, Firewatch)

---

### ⚖️ Game Balancing

**[→ resources/game-balancing.md](./resources/game-balancing.md)**

이론에서 실전 공식까지:

**Machinations 프레임워크:** 6가지 노드 유형, 피드백 루프 설계 (포지티브/네거티브), RPG·전략 장르의 경제 루프 다이어그램

**수치 밸런싱:**
- 선형 / 지수 / 로그 / S-커브 스탯 스케일링과 예시
- DPS·TTK 계산 표준과 인카운터 유형별 목표값
- 가위바위보 삼각 밸런싱

**PvP:** K값 최적화를 포함한 ELO 공식; MMR 티어 분포 설계; 승률 밸런싱 원칙; 매칭 속도 vs 품질 트레이드오프

**Idle/Casual:** 업그레이드 비용 곡선 (`BASE × MULTIPLIER^n`); 세션 길이 설계; 오프라인 진행 공식

**가챠 윤리:** 천장 시스템 수학 (소프트/하드 ceiling), 드랍 테이블 설계, 글로벌 규제 비교 (한국·중국·벨기에·EU), 윤리적 디자인 체크리스트

**5단계 프로세스:** 이론 → 봇 시뮬레이션 → 내부 플레이테스트 → 외부 플레이테스트 → 라이브 데이터

---

### 🎨 Art Direction

**[→ resources/art-direction.md](./resources/art-direction.md)**

픽셀에서 사운드까지의 비주얼 크래프트:

**픽셀 아트:** 7가지 핵심 원칙; Aseprite vs Pyxel Edit vs LibreSprite 비교; 애니메이션 프레임 카운트; 학습 자료 (Lospec, Pedro Medeiros, Pixel Joint)

**UI/UX:** 정보 위계; HUD 영역 배치 (Fitts's Law); 색맹 접근성 (WCAG 2.1); 인벤토리 시스템 유형; 온보딩 패턴 카탈로그

**색상 이론:** 5계층 팔레트 구조; 명도 우선 디자인; 도구 라운드업 (Coolors, Lospec, Adobe Color, Paletton)

**사운드 디자인:** FMOD vs Wwise (인디 가격 포함); 무료 소스 (Freesound, BFXR, OpenGameArt); 레이어링·피치 랜덤화·다이내믹 레인지 원칙

**애니메이션:** Spine vs DragonBones vs 프레임 애니메이션 결정 트리; 게임에 적용한 디즈니 12원칙

---

### 📣 Marketing & QA

**[→ resources/marketing-qa.md](./resources/marketing-qa.md)**

첫 커밋부터 출시 주간과 그 이후까지:

**런치 체크리스트:** 6개월 → 3개월 → 1개월 → 출시 주간 단계별 구체 액션

**Steam 최적화:** 타이틀 네이밍, 짧은 설명 공식, 태그 선택 전략, 캡슐 아트 원칙, 위시리스트→판매 전환 추정치

**트레일러 제작:** 4가지 트레일러 유형; "처음 5초" 원칙; 음악 라이선스 옵션; 6단계 게임플레이 트레일러 구조

**커뮤니티:** Discord 구조; Twitter/TikTok/Reddit 플랫폼별 전략; 인플루언서/스트리머 아웃리치 흐름

**QA:** 기능/리그레션/플레이테스트 유형; 버그 리포트 표준 템플릿 (severity + priority); 닐슨의 법칙 (5–8 테스터 = 95% 이슈 발견)

**런치 전략:** 소프트 런치 vs 하드 런치; Steam Early Access 결정 기준; 출시 후 1주차 대응; 장기 업데이트 로드맵; 세일 참여 전략

---

### 🏭 Production Pipeline (AAA)

**[→ resources/production-pipeline.md](./resources/production-pipeline.md)**

AAA 스튜디오가 실제로 사용하는 제작 파이프라인 — 인디·AA가 "왜 AAA는 2~5년이 걸리나"를 이해할 때도 유용:

- **단계**: Concept → Pre-production → Production (Alpha / Beta / Code Lock) → Certification → Launch → Live
- **Gate criteria**: 단계별 통과 조건 명문화 (블로커 수, 크래시 율, Cert 통과율, Localization lock)
- **Vertical Slice**: Uncharted 4·Destiny·Spider-Man·AC Valhalla의 실제 VS 규모와 체크리스트
- **Greenlight**: 10장 피치덱 표준 구조 + 퍼블리셔 측 판정 rubric (7개 가중 항목)
- **마일스톤 페이먼트**: Signing 15% → Prototype 10% → Alpha 20% → Beta 20% → Gold 15% → Launch 10% + 로열티 (업계 추정 평균)
- **RACI / DRI**: 디자인 필러 변경·스코프 컷·플랫폼 추가·딜레이·크런치 결정의 책임 매트릭스
- **심화 사례**: Uncharted 4 감독 교체 reboot, Cyberpunk 2077 cert/launch 실패, Baldur's Gate 3의 EA-as-production, Starfield 엔진 동시 개발

---

### 🎮 Platform Certification

**[→ resources/platform-certification.md](./resources/platform-certification.md)**

플랫폼 인증은 AAA 출시 일정의 1순위 리스크 — 이 문서 하나로 커버:

- **플랫폼별 상세**: PS TRC ~200 / Xbox XR ~150 / Switch Lotcheck / Steam Partner / Apple App Review / Google Play / EGS
- **PS5 리젝 TOP 10**: Save crash, trophy 오류, region lock 미적용, accessibility 누락 등
- **XAGs (Xbox Accessibility Guidelines) — 120+ 가이드라인**: Input · Audio · Visual · Cognitive · Motor 카테고리별 대표 XAG 번호
- **Nintendo Lotcheck 특별 요구**: Docked vs Handheld 이중 성능, JoyCon 전 조합, 페런털 컨트롤 준수
- **Rating 기관 비교**: ESRB / PEGI / CERO / USK / GRAC (한국 게임위) / ACB / 중국 판호 — 비용·기간·제출 방식
- **지역 규제**: 한국 확률 공시 의무화 (GIPA 시행령, 2024.03.22 발효), 중국 판호 제도, 벨기에 loot box 금지
- **공통 Fail Top 20**: 크로스 플랫폼에서 반복 발생하는 리젝 사유
- **Cert 타임라인**: Gold-master 4주 전 제출, 3개 리전 병렬 제출, Day-1 patch 별도 제출 기준

---

### 🔁 Live Ops Playbook

**[→ resources/live-ops-playbook.md](./resources/live-ops-playbook.md)**

출시는 1일차 — 3~10년 라이브 서비스 운영 매뉴얼:

- **서비스 모델 분류**: Season-based (Fortnite / Apex), Expansion (FF14 / WoW), Episodic, Gacha, Hybrid
- **8~12주 시즌 표준 구조**: 주차별 이벤트 배치 (Fortnite, Destiny 2 Episode, FFXIV cadence)
- **풀 KPI 대시보드**:
  - Engagement: DAU/MAU, sticky ratio, D1/D7/D30 retention
  - Monetization: ARPDAU, ARPPU, conversion, LTV, whale share
  - Economy: inflation index, source/sink ratio, rarity drift
  - Operational: crash-free rate, SLA, MTTR
- **Anti-cheat 비교**: Easy Anti-Cheat / BattlEye / Vanguard / Denuvo / VAC — 커널 레벨 트레이드오프
- **Launch Disaster Recovery**: Cyberpunk 3년·No Man's Sky 8년·FFXIV "A Realm Reborn" 전면 reboot 사례
- **Recovery Failed**: Anthem Next (2021 취소, 2026.01 서버 종료), Marvel's Avengers (복구 시도 없이 2023.09 EOL), Battleborn / Lawbreakers / Babylon's Fall — 3요소 성공 패턴 분석
- **Sunset Playbook**: D-180부터 D+30까지 서비스 종료 체크리스트 (Concord 14일 종료, WildStar, P.T. 사례)
- **수익화 컴플라이언스**: 한국 확률 공시 2024.03, 중국 판호, 벨기에 전면 금지, FTC Epic Games $520M 합의 (2022.12)
- **Asia Live Service 사례**: 한국 MMO (리니지·메이플스토리 ₩116억 2024 공정위·로스트아크·우마무스메 KR 시위)와 중국 가챠/SLG (HoYoverse cadence·PUBG Mobile vs Peacekeeper Elite·Honor of Kings·SLG 서버 전쟁)
- **A/B 실험 운영**: Riot·Supercell·Epic의 트래픽 분배·평가 지표·의사결정 표준

---

## 활용 가이드

### Claude 시스템 프롬프트로 사용

[SKILL.md](./SKILL.md) (한국어) 또는 [SKILL.en.md](./SKILL.en.md) (영어)을 메시지 앞에 붙여 Claude를 풀 게임 기획자 모드로 활성화. Claude가 다음을 수행할 수 있게 됩니다:

- 완전한 10섹션 GDD 작성
- HTML 아티팩트 게임 UI 프로토타입 즉석 생성
- 밸런스 시뮬레이션 실행 및 곡선 조정 제안
- 확립된 프레임워크 기준으로 내러티브 구조 비평
- Ink / Yarn Spinner 대화 스크립트 작성

### 솔로 인디 개발자

1. **SKILL.md** → 모든 기획 작업의 시스템 프롬프트
2. **resources/narrative-design.md** → 대화 도구·스크립트 포맷 선택
3. **resources/game-balancing.md** → 진행 곡선 공식을 스프레드시트에 복사
4. **resources/marketing-qa.md** → 출시 3개월 전 런치 체크리스트 가동

### 팀 리드

1. **resources/famous-gdds.md** → 신규 팀원 필독서
2. **resources/postmortems.md** → 회고 레퍼런스 ("이전에 어떤 일들이 잘못되었나?")
3. SKILL의 GDD 템플릿 → 모든 신규 프로젝트 문서의 표준 포맷

### AAA / 대형 스튜디오

1. **resources/production-pipeline.md** — 내부 pre-prod / production / cert 일정 템플릿의 대체 또는 교차 검증용. Greenlight 판정 rubric을 내부 greenlight review에 직접 적용 가능
2. **resources/platform-certification.md** — QA 리드·프로듀서를 위한 사전 체크리스트. 1차 submission 전 self-audit 기준. 지역 규제 항목 (한국 확률 공시, 중국 판호)은 publishing·legal 팀과 공유
3. **resources/live-ops-playbook.md** — 라이브 옵스 디렉터·PM을 위한 KPI·sunset·A/B 프레임워크. Launch disaster 사례는 신규 프로젝트의 리스크 리뷰에 활용
4. **resources/game-balancing.md** — PvP ELO·MMR, 가챠 천장, idle 비용 곡선을 기존 AAA 밸런스팀 공식과 교차 확인

### 학생

1. 모든 postmortem을 읽기 — 정직한 게임 디자인 교육
2. 유명 GDD 학습 — 계획과 현실 사이의 간극 이해
3. 수치를 추측하기 전에 밸런싱 공식을 학교 프로젝트에 적용
4. Production pipeline → 업계 진입 준비생을 위한 "AAA가 실제로 일하는 방식" 입문서

---

## 기여하기

기여를 환영합니다. 이 저장소는 폭이 아닌 깊이로 성장합니다.

**받는 항목:**
- 설명 + 핵심 교훈이 포함된 신규 항목 (단순 링크 제외)
- 다루지 않은 주제의 신규 리소스 파일
- 오래된 정보·깨진 링크 정정

**받지 않는 항목:**
- 개인 게임 포트폴리오
- 홍보성 콘텐츠
- 맥락·분석 없는 링크 dump
- 플랫폼 NDA 위반 자료 (Sony DevNet, Xbox XR, Nintendo Lotcheck 등)

**기준:** 모든 항목은 다음 질문에 답해야 합니다: *"제목만 구글링해서는 얻을 수 없는, 기획자가 이 자료에서 배울 핵심은 무엇인가?"*

기여 방법: Fork → Branch (`resource/your-topic`) → 콘텐츠 추가 → 설명을 포함한 Pull Request. 전체 표준은 [CONTRIBUTING.md](./CONTRIBUTING.md)에서, 커뮤니티 행동 강령은 [CODE_OF_CONDUCT.md](./CODE_OF_CONDUCT.md)에서 확인하세요.

---

## 라이선스

MIT License — 상세는 [LICENSE](./LICENSE) 참조.

## 상표 및 법적 고지

본 저장소에서 언급되는 모든 제품명·게임 타이틀·스튜디오명·로고 (PlayStation, Xbox, Nintendo Switch, Steam, Epic Games, Unity, Unreal 및 특정 게임 타이틀 등을 포함하되 이에 국한되지 않음)는 **각 소유자의 상표**입니다. 본 저장소는 해당 기업과 무관하며, 그 어느 곳의 후원·승인·제휴를 받지 않았습니다. 모든 참조는 교육 및 분석 목적입니다.

본 저장소는 **법률·규제·계약 자문이 아닙니다**. 플랫폼 인증 요구사항, 지역 규제 (loot-box 법규, 등급 심사, 확률 공시 규정), 퍼블리싱 계약은 자주 바뀌며 관할권에 따라 다릅니다. 본 자료를 바탕으로 행동하기 전에 반드시 공식 플랫폼 문서, 자격 있는 법률 자문, 최신 규제 원문을 확인하세요.

---

*[awesome-design](https://github.com/gztchan/awesome-design) (★15k+) 의 영감을 받아 게임 기획의 영역에 적용했습니다.*
