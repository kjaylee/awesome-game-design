# 🏭 AAA Production Pipeline — 제작 파이프라인

> "기획서는 밤새 쓸 수 있지만, 파이프라인은 2년이 걸린다."
> — AAA 제작자가 외부 자료에서 실제로 가져다 쓰는 영역은 템플릿도 포스트모템도 아닌 **단계 간 전환 기준(Gate Criteria)**이다.

---

## 📊 전체 단계 맵

| 단계 | 기간 (AAA 표준) | 산출물 | Gate 통과 조건 |
|---|---|---|---|
| Concept | 3~6개월 | Pitch doc, sizzle reel, budget estimate | Concept Greenlight |
| Pre-production | 9~18개월 | Vertical Slice, GDD 1.0 lock, tech prototype | **Production Greenlight** |
| Production | 12~36개월 | Alpha (Content Complete), Beta (Feature Complete) | Code Lock |
| Certification | 6~12주 | Cert build, day-1 patch | Gold Master |
| Launch | 1~4주 | Shipping build, hotfixes | Launch Review |
| Live / Post-launch | 3~10년 | Seasons, DLC, sunset | Sunset Review |

### 단계별 인력 피크

| 단계 | 핵심 팀 크기 |
|---|---|
| Concept | 6~12 |
| Pre-production | 40~80 |
| Production (초) | 120~180 |
| Production (피크) | 250~400 (외주 포함) |
| Cert / Launch | 200~300 |
| Live team | 50~150 |

> 인력 피크 예시: Uncharted 4 250+ (업계 추정). Cyberpunk 2077 500+ (CDPR 공개 발언). **GTA V 1,000+ (Rockstar Leslie Benzies 공식 인터뷰, GameSpot 2013)** — 일부 후속 보도는 2018 누적 기준 6,000+ 주장하나 공식 채널 근거 불명. 3,000+ 등 중간 수치는 출처 확인 필요.

---

## 🏁 Pre-production — Vertical Slice (VS)

**Vertical Slice**: 최종 게임의 한 레벨 또는 한 시퀀스를 **출시 품질**로 뽑은 축소 버전. Publisher greenlight·팀 확장·파이프라인 검증의 핵심 근거.

### 실제 사례 규모 (업계 추정치)

> 아래 수치는 공식 발표보다는 공개 GDC talks · 퇴임 개발자 인터뷰 · 업계 보도 합성. 정확한 VS 팀 구성은 대부분 스튜디오가 공개하지 않는다. 수치를 계약·계획 근거로 쓰지 말 것.

| 스튜디오 / 게임 | VS 규모 | 투입 (업계 추정, 비공식) |
|---|---|---|
| Naughty Dog / Uncharted 4 | (공식 수치 미공개) | 2014년 pre-prod reboot 사실만 공식 확인 (Hennig → Druckmann/Straley 교체, 8개월치 스토리 폐기) |
| Bungie / Destiny | Strike 1개 | ~8개월, ~70명 (업계 추정) |
| Insomniac / Spider-Man | 오프닝 시퀀스 | ~5개월, ~50명 (업계 추정) |
| Ubisoft / AC Valhalla | 노르웨이 오프닝 | ~7개월, ~80명 (업계 추정) |

### VS 체크리스트

- [ ] 핵심 메카닉 3개 playable, 반응 곡선 1차 튜닝
- [ ] Narrative 샘플: dialogue + cinematic 1~2개
- [ ] Art direction 확립 (shader library, post-process stack, hero character 1, hero env 1)
- [ ] UI 기본 (HUD, main menu, pause, settings)
- [ ] Audio 파이프라인 (FMOD/Wwise 연동, SFX 셋 + 음악 1트랙 + VO 1)
- [ ] 30분 seamless playthrough, 타깃 프레임 안정 (30/60/120fps 중 공식 선언)
- [ ] Cert 요구사항 맛보기: save/load, controller full remap, subtitle on/off, basic accessibility

### VS 실패 신호

- 메카닉 "loop"이 30초 안에 반복되지 않음 → 재미 검증 불가
- 아트 vs 기술 엇박자 (아트는 next-gen, 프레임은 25fps)
- 팀 내부에서 "이 30분을 보여주기 부끄럽다"는 기류

---

## 🟢 Greenlight Gate — 생사 결정 관문

**Greenlight**: "이 게임에 수천만~수억 달러를 full production으로 투입할 것인가" 결정. Publisher·Executive Producer·CFO·Platform holder가 동시 참석.

### Greenlight Deck — 10장 표준 구조

1. **One-liner** (25 words) — USP + 타겟
2. **Market** — 장르 TAM, top 10 비교, 최근 5년 concurrent players / sales
3. **Audience** — 페르소나 2개, 연령·지역·기기·경쟁 소비 시간
4. **Vision Reel** — 60초 sizzle video
5. **Pillars** — 3개 design pillar, 각각 "메카닉 1개로 증명"
6. **Scope** — 주요 시스템 15개 + 컷 가능한 30% 명시 (cutability 매트릭스)
7. **Tech** — 엔진, 플랫폼, 주요 middleware, top 5 기술 리스크
8. **Team** — 현재 N명, 필요 N명, key hire 3명 JD
9. **Budget & Timeline** — 월별 burn, 분기별 마일스톤 카드
10. **Risks** — top 5 risk, 각 완화책·조기 경보 지표

### Greenlight 판정 Rubric (Publisher 내부용)

| 항목 | 가중치 | 5점 기준 |
|---|---|---|
| Market fit | 0.20 | "신작 대비 확실한 차별 + 경쟁작 공백" |
| Team track record | 0.20 | "핵심 리드 3+ AAA 출시 경력" |
| Tech risk | 0.15 | "엔진 내재화, 외부 의존 3개 이하" |
| Financial model | 0.15 | "Break-even <200만 copies 또는 <300만 MAU" |
| IP strength | 0.10 | "기존 팬덤 or 확실한 IP 제휴" |
| Live-ops runway | 0.10 | "10년 서비스 시나리오 있음" |
| Platform alignment | 0.10 | "First-party 지원 의향서 확보" |

합계 3.5+ = Greenlight. 3.0~3.5 = re-pitch. 3.0 미만 = kill.

### 실제 Greenlight 사례

- **Overwatch (Blizzard, 2013)**: Titan MMO 취소 후 잔여 40명이 6주 프로토타입 → greenlight. Pitch 핵심은 "Team Fortress 2 + MOBA 캐릭터 시너지".
- **Hellblade II (Ninja Theory, 2019)**: Microsoft 합병 직후 프로토타입 → 확장 greenlight. Visual fidelity 단 1개 pillar.
- **Cyberpunk 2077 (CDPR, 2012 reveal → 2016 본격)**: Pre-prod 4년. 기술 스택 결정이 greenlight 이후 바뀐 대표 케이스 (REDengine 확장). 교훈: **엔진 결정은 greenlight 전**.
- **Starfield (Bethesda, 2013 내부 → 2018 공개)**: Creation Engine 2 동반 개발. Pre-prod 5년의 근거.

---

## 🔨 Production — Alpha / Beta / Code Lock

### Alpha = Content Complete (CC)

- 모든 주요 시스템 코드 in. **이후 신규 메카닉 금지**.
- 모든 콘텐츠 "grey box" 또는 "first-pass art" 상태
- 기능 버그 치명급 0, blocker 10~20 허용
- 외부 QA vendor 투입 시점 (Keywords, VMC, Testronic)
- 마일스톤 payment trigger

### Beta = Feature Complete (FC)

- 모든 콘텐츠 final art
- UI/UX 확정, localization text lock
- Cert 요구사항 90% 충족
- 외부 closed beta (100~5,000명)

### Code Lock / Gold Master

- 코드 freeze. Bug fix만 허용 (regression risk 평가)
- Cert 통과 build = **Gold Master**
- Disc press 시작 (packaged product)
- Digital storefront upload (Steam depot, PS Store, Xbox package)

### 단계 전환 Exit Criteria (AAA 내부 예시)

```
Alpha Exit:
  - Blocker ≤ 15
  - Critical ≤ 50
  - 전체 playthrough 완주 가능 (어떤 difficulty라도)
  - Save/load 기본 동작
  - Target platform 전체 부팅 & 첫 30분 플레이

Beta Exit:
  - Blocker = 0
  - Critical ≤ 10
  - 크래시 율 < 0.3%
  - Localization 전체 언어 first-pass
  - Cert 필수 항목 95%+
  - Accessibility 기본 (subtitle, remap, colorblind)

Gold:
  - Blocker = 0
  - Critical = 0
  - 크래시 율 < 0.1%
  - Platform cert 100% 통과
  - Day-1 patch 작성 중 (대부분 launch에는 이미 patch 필요)
```

---

## 💰 Milestone Payment 구조 (Publisher 계약)

AAA 개발사는 대부분 publisher로부터 milestone 기반 cost-recoup + royalty 계약. 아래는 업계 평균.

| Milestone | 전체 지급 비율 | 조건 |
|---|---|---|
| Signing | 10~15% | 계약 체결 |
| Prototype / VS | 10% | VS 완료 |
| Alpha (CC) | 20% | CC 통과 |
| Beta (FC) | 20% | FC 통과 |
| Gold / Cert | 15% | Cert 통과 |
| Launch | 10% | 출시 확인 |
| Royalty recoup | 나머지 + 10~30% | Break-even 도달 후 비율 |

출처: IGDA Business Contracts Compendium, GDC Business Track 2019~2024.

---

## 🗂️ RACI / DRI 매트릭스 (표준화된 AAA 의사결정)

| 결정 | R (Executor) | A (Accountable) | C (Consulted) | I (Informed) |
|---|---|---|---|---|
| Design pillar 변경 | Lead Designer | Game Director | Creative Director, Narrative Lead, Production | Team, Publisher |
| Scope cut 30%+ | Production Director | Executive Producer | Game Director, Publisher | Team, Platform |
| Platform 추가 | Tech Director | Executive Producer | Publisher, Platform holder | Team |
| Delay 90일+ | Executive Producer | Studio Head | Publisher, Board | Team, Marketing |
| Crunch 지시 | (금지) | Studio Head | HR, Union rep | 전사 |

> AAA 조직 구조 참조: Respawn "What's a Game Director?" GDC 2019 talk, Naughty Dog PDT 2021.

---

## 📸 주요 사례 심화

### Uncharted 4 Pre-prod Reboot (Naughty Dog, 2014)

- 2012~2014: Amy Hennig 감독. 1차 VS 실패(팀 내부 리뷰).
- 2014: Neil Druckmann + Bruce Straley 감독 교체. Pre-prod reboot.
- 교훈: **AAA에서도 감독 교체는 발생**. Reboot 비용을 pre-prod 예산에 10~20% 버퍼로 내재화.

### Cyberpunk 2077 (CDPR, 2013~2020~2023)

- Pre-prod 4년, production 3년. Crunch 18개월.
- 출시 직후 PS4/XB1 디스토어 디리스트 (Sony, 2020.12).
- 복구: 무료 업데이트 6개, Phantom Liberty 확장 (2023), Edgerunners 애니 (2022).
- 교훈: **Cert 통과 ≠ 출시 품질**. Platform cert는 최소 조건이지 품질 보증이 아님.

### Baldur's Gate 3 (Larian, 2017~2023)

- Early Access를 "production 단계"로 활용 (2020~2023, 3년).
- 플레이어 수만 명의 세이브 파일 = live QA 데이터.
- 교훈: **EA를 alpha/beta 대체로 쓰는 모델이 Baldur's Gate 3로 AAA에도 검증됨** (이전: Hades, Subnautica).

### Starfield (Bethesda, 2018~2023)

- Creation Engine 2 동시 개발 — 전통적 AAA "엔진 내재화" 모델.
- 출시 후 review 편차 (전문 매체 83 vs Steam 60%). 교훈: **live-ops runway가 약하면 post-launch 평판 반등 어려움**.

---

## 🛠️ 템플릿 포인터

본 레포 내:
- **GDD 10-섹션 표준**: [SKILL.md](../SKILL.md) §GDD 작성 표준
- **Postmortem 프레임워크**: [postmortems.md](./postmortems.md)
- **Cert 요구사항**: [platform-certification.md](./platform-certification.md)
- **Live-ops KPI**: [live-ops-playbook.md](./live-ops-playbook.md)

외부 레퍼런스:
- GDC Vault: "Production at Scale" track (2019~2024)
- IGDA White Papers — Scheduling, Contracts
- Game Developer Magazine — Postmortem archive (now Game Developer Mag Online)
- Gamasutra / GameDeveloper.com — Postmortem columns
- Edge Magazine — Making of series

---

*본 문서는 AAA 개발자·프로듀서·퍼블리셔 실무자용 reference이며, 인디 스튜디오에도 "AAA가 왜 그렇게 오래 걸리는가"에 대한 설명 자료로 활용 가능하다.*

---

## ✅ Sources Verified (2026-04-21)

- **FFXIV Realm Reborn 일자 & Yoshi-P 임명 (2010.12 → 2013.08)**: [Wikipedia — Naoki Yoshida](https://en.wikipedia.org/wiki/Naoki_Yoshida), [Wikipedia — FFXIV](https://en.wikipedia.org/wiki/Final_Fantasy_XIV), [TIME — Yoshida 복구 인터뷰](https://time.com/3817373/final-fantasy-14-naoki-yoshida/)
- **Milestone payment 구조**는 IGDA Business Contracts Compendium·GDC Business Track 다수 talk에서 재확인되는 업계 표준 분포 (단일 공식 출처보다는 합의 수치). 계약별 편차 있음
- 기타 사례(Uncharted 4 reboot, Cyberpunk 2077 cert fail, Baldur's Gate 3 EA-as-production)는 공식 postmortem / GDC talks / 발행사 공개 인터뷰 기반
