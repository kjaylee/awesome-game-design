# 🔁 Live Ops Playbook — 라이브 서비스 운영

> "출시는 끝이 아니라 1일차다. Destiny 2는 8년째, FF14는 14년째다."
> AAA 라이브 운영은 **제작보다 긴 시간·큰 인력·엄격한 KPI**로 움직인다.

---

## 📊 라이브 서비스 모델 분류

| 모델 | 대표작 | 업데이트 주기 | 주 수익 구조 |
|---|---|---|---|
| Season-based | Fortnite, Apex, Call of Duty | 8~12주 시즌 | 배틀패스 (~$10) |
| Expansion-based | FF14, WoW, Destiny 2 | 12~24개월 | 박스 ($30~60) + 구독·패스 |
| Episodic | Hitman, Life is Strange | 3~6개월 | 에피소드 단위 |
| Event-driven (gacha) | Genshin, Honkai Star Rail, Arknights | 5~6주 | 가챠 (10연차 $15~30) |
| Hybrid BP + Gacha | Call of Duty Warzone, PUBG | 6~10주 | BP + 번들 |
| Freemium Box | League of Legends, Dota 2 | 2주 patch | Cosmetic-only |

---

## 📆 시즌 구조 표준 (8~12주 기준)

```
Week 0   | Season launch — trailer, patch notes, new content drop
Week 1-2 | Peak engagement: 신규 오브젝트·이벤트 1
Week 3-5 | Mid-season balance patch (metadata 조정, 경제 튜닝)
Week 6-7 | Event 2: crossover / 한정 / holiday-tie
Week 8-10| End-season push: XP 이벤트, BP 마감 drive
Week 11-12| Finale event, next-season teaser
```

### Fortnite Chapter 5 시즌 구성 (2024)
- Battle Pass 100 tiers, 10주 진행
- Mid-season live event (Big Bang concert, The Device)
- Collaboration: Marvel, Star Wars, 애니 IP
- 신규 메카닉 (Vehicles, Medallions, Mythic weapons)
- 평균 season revenue: $300M+ (추정)

### Destiny 2 Episode 구조 (2024~)
- 이전 "Season" (3개월) → "Episode" (4개월) 전환
- 각 Episode는 3 "Act" × 6주
- 서사 독립성 강화, 재진입 장벽 낮춤

### FF14 패치 주기 (Patch Cadence)
- Major expansion: 2년
- 중간 패치: **.0 → .1 → .2 → .3 → .4 → .5 → 신 확장**
- 각 패치 14주 간격. 디렉터 Yoshi-P의 "리듬" 강조

---

## 🏭 Live 콘텐츠 Pipeline

### Sprint → Content Gate → Live

```
Sprint Plan (2주)
  └→ Content Design & Prototype (1~2주)
     └→ Implementation (3~6주)
        └→ Internal QA + Balance sim (1주)
           └→ Closed beta / Private playtest (1주)
              └→ Content Gate (go / no-go 판정)
                 └→ Staging build + SRE 리허설
                    └→ Live patch (maintenance window)
```

### Content Gate 체크리스트

- [ ] Crash-free session rate **> 99.7%**
- [ ] Load time 회귀 없음 (< 5s)
- [ ] 메모리 budget 준수 (platform별)
- [ ] Accessibility 요구 통과
- [ ] 지역별 locale fall-through 없음
- [ ] 경제 시뮬: 10k~100k bot session 통과
- [ ] A/B 실험 승자 확정 (유저 노출 전 내부 결정)
- [ ] 서비스 rollback plan 준비 (5분 내)
- [ ] 지원팀 (CS) 브리핑 완료
- [ ] 커뮤니티팀 patch note 준비

---

## 📈 KPI 대시보드

### Engagement

| 지표 | 정의 | 주의 |
|---|---|---|
| **DAU / MAU** | 일일/월간 활성 | sticky = DAU/MAU, **0.3+ 양호** |
| **Session length (median, p95)** | 세션당 플레이 시간 | median만 보면 long-tail whales 누락 |
| **Retention D1/D7/D30** | 코호트 유지율 | D1 60%+, D7 30%+, D30 15%+ (장르 평균) |
| **Time-to-next-session** | 재접속 간격 | FTUE 직후가 critical |
| **Sessions per DAU** | 하루에 몇 번 들어오는가 | 1.5+ = 높은 habit |

### Monetization

| 지표 | 정의 |
|---|---|
| **ARPDAU** | Daily revenue / DAU |
| **ARPPU** | Daily revenue / Payers only |
| **Conversion rate** | 무료 → 유료 전환 (전체 2~5% 표준) |
| **LTV (D60/D90/D360)** | 코호트별 누적 매출 |
| **Whale share** | Top 0.1% 지출이 전체 수익의 N% (gacha: 50%+) |
| **Refund rate** | 전체 매출 대비 |

### Economy

- **Currency inflation index**: 주차별 가격 지수 (특정 아이템의 마켓 가격 추적)
- **Source / Sink ratio**: 현재 ≈ 1.0. 0.8 이하 = 디플레, 1.2 이상 = 인플레
- **Rarity drift**: 희귀 아이템 출몰 빈도 모니터링
- **Flash price alert**: 경제 붕괴 조기 경보 (5% 이상 급락/급등 즉시 알림)

### Quality / Operational

- **Crash-free session rate**: > 99.7% (AAA 표준)
- **Server uptime SLA**: 99.95% (월 21.9분 다운 허용)
- **Patch rollback rate**: < 2%
- **Support ticket volume**: 일·카테고리별 분해, 자동 카테고리화 (NLP)
- **MTTR** (Mean Time to Recovery): incident → fix 평균 시간

### Community / Sentiment

- **Steam review score**: 최근 30일 기준, 85%+ 양호
- **Reddit sentiment** (scraped): 주간 긍정/부정 비율
- **Discord member growth**: DAU와 상관관계
- **Streamer concurrent**: Twitch·YouTube 평균 viewer

---

## 💰 경제 모니터링 상세

### 인플레이션 대응 도구

| 도구 | 설명 | 사례 |
|---|---|---|
| Cosmetic sink | 영구 아이템에 cosmetic 통화 싱크 | WoW transmog |
| Currency cap | 주간·월간 최대 보유량 | Destiny 2 Glimmer cap |
| Drop rate 조정 | 메인 소스 10~20% 감소 | FF14 tomestone weekly cap |
| 새 티어 추가 | 상위 보상으로 인플레 흡수 | Diablo 3 Primal Ancient |

### 희귀도 Drift 방지

- 히든 카운터로 월간 최대 드랍량 설정
- Pity system (Genshin: 90 pull hard pity, 75~80 soft pity)
- Server-side rarity adjuster (이상 시 튜닝)

### 실패 사례

- **Diablo Immortal (2022)**: $110k 개인 소비자 등장 → 커뮤니티 반발, 리텐션 급락
- **Star Wars Battlefront II (2017)**: Loot box progression → 출시 직전 시스템 disable, 이후 MTX 전면 재설계
- **FIFA Ultimate Team (2017~)**: 패킹 확률 소송, 유럽 여러 국가 규제 대응

---

## 🛡️ Anti-cheat 전략

### 솔루션 비교

| 제품 | 커널 수준 | 대표 도입 | 특징 |
|---|---|---|---|
| Easy Anti-Cheat | kernel | Apex, Fortnite, Elden Ring | Epic 인수 후 크로스플랫폼 |
| BattlEye | kernel | PUBG, Rainbow Six Siege, DayZ | 일부 Linux 지원 |
| Vanguard | kernel (상시 구동) | Valorant | 부팅부터 구동, 논란 많음 |
| Denuvo Anti-Cheat | user-mode | Doom Eternal (철회) | 유저 반발로 철회 선례 |
| VAC (Valve) | server-side | CS, TF2 | 소프트, 지연 ban |
| Warden | server-side | WoW | 심층 행동 분석 |
| PunkBuster (legacy) | mixed | BF 시리즈 | 현재는 거의 퇴출 |

### Helldivers 2 사태 (2024 May)

- 2024.05.03: Arrowhead/Sony가 PSN 강제 연동 발표 (신규 유저 5.30~, 기존 유저 6.04까지 연동)
- 2024.05.03~06: 주말 이틀 + 월요일 포함 약 3일간 **Steam review "매우 긍정적" → "복합적"**, 170+ 국가 스토어 판매 중단 여파 (PSN 미지원 지역)
- 2024.05.06: Sony 공식 철회 발표
- 교훈: live ops 정책 결정 시 **커뮤니티 백래시 시뮬레이션** 필수. 특히 지역별 계정 생성 가능 여부 (PSN은 약 69개국만 지원) — Steam 2.6B 잠재 시장 중 0.6B+ 배제 이슈

### Valorant Vanguard 논란

- 부팅 시 kernel-level driver 상시 구동
- 시스템 자원·보안 관심 사용자 이탈
- 교훈: anti-cheat vs 사용자 프라이버시 trade-off는 경쟁 게임에서만 정당화 가능

---

## 🌅 Sunset Playbook — 서비스 종료 체크리스트

### 180일 ~ Launch day 기준

- [ ] **D-180**: 공지. 플레이어 6개월 반응 시간 제공
- [ ] **D-150**: Refund policy 공지 (미사용 가상재화 처리 방침)
- [ ] **D-120**: IAP disable (결제 중단)
- [ ] **D-90**: Final content patch (마지막 이벤트 발표)
- [ ] **D-60**: Offline 모드 빌드 제공 검토 (기술적 가능 시)
- [ ] **D-45**: 플레이어 감사 이벤트 (무료 스킨, 특별 대사)
- [ ] **D-30**: 추억 이벤트 시작, 감사 영상 공개
- [ ] **D-14**: 최종 리더보드 fix
- [ ] **D-7**: 커뮤니티 tribute (아트북 PDF, soundtrack 공개)
- [ ] **D-0**: 서버 종료, 마지막 메시지
- [ ] **D+30**: 아카이브 페이지, 정식 postmortem, 기록 포트폴리오

### 실제 사례

- **Concord (Firewalk/Sony, 2024)**:
  - 2024.08.23 출시 → 2024.09.06 서버 종료 (**14일 서비스**). 전액 환불. 2024.10.29 Firewalk Studios 스튜디오 자체 폐쇄
  - 8년·~$100M 추정 프로젝트 실패. MP 게임 역대 2번째로 짧은 서비스 기간 (1위: The Culling 2 — 8일)
  - 교훈: Live service는 런치 후 **1주 retention < 목표의 20%** = 즉시 복구 불가 신호
- **WildStar (Carbine, 2014~2018)**: 4년 서비스 후 종료. 오프라인 모드 없음 → 팬덤 상실감 극대
- **P.T. (Kojima/Konami, 2014~2015)**: 디지털 배포 중단이 얼마나 고통스러운지의 상징 케이스
- **City of Heroes (NCsoft, 2004~2012 → 2019 사설 서버)**: 커뮤니티 복구 성공. 코드 leak이 "unofficial preservation"의 사례
- **Titanfall 1 (Respawn/EA, 2014~2022 사실상 방치)**: 서버 봇 공격으로 운영 포기. 교훈: **sunset 플랜 없이 방치 금지**

---

## 🚑 Launch Disaster Recovery 사례

### Cyberpunk 2077 (2020 → 2023)

- **Y+0 (2020 12월)**: PS4/XB1 스토어 디리스트 (Sony 사상 초유)
- **Y+1 (2021)**: Hotfix 6+, Next-gen 무료 업데이트 약속
- **Y+2 (2022)**: Edgerunners (Netflix) 애니 공개 → 신규 유저 300만+ 유입
- **Y+3 (2023)**: Phantom Liberty 확장 + 2.0 패치 → Steam 리뷰 83% "매우 긍정적"
- **레버리지**: 지속 commitment + 외부 IP (애니) + 기술 성숙
- **교훈**: 3년 commitment가 회복 최소 단위

### No Man's Sky (2016 → 2024)

- 출시: 소비자 기만 논란, 환불 대란
- 2016~2024: **18개 무료 대형 업데이트**, 8년
- 현재: Steam 리뷰 "매우 긍정적", 상징적 "redemption arc"
- **교훈**: 작은 팀(Hello Games ~30명)도 장기 commitment로 복구 가능

### FFXIV "A Realm Reborn" (2010~2013)

- **2010.09.30**: 1.0 출시 → 품질 미달, 거의 파산 직전. 공식 사과문 발행
- **2010.12**: Naoki Yoshida (Yoshi-P)가 producer/director로 임명, 전면 재개발 지시
- **2013.08.27**: 2.0 "A Realm Reborn"으로 재출시 (PS3 + Windows)
- 현재: MMO 시장 수위권, 2,400만+ 계정
- **교훈**: 경영진의 "전면 reboot" 결단 + 후임 디렉터 임명은 재개발 공개 **3년 전**

### Recovery Failed — 복구 실패 사례 (균형을 위해)

> 위 세 사례만 보면 "commitment만 지속하면 어떤 재난도 복구 가능"이라 오독할 수 있다. 실제 live-service 복구 시도의 다수는 실패한다. 대표 실패 사례:

#### Anthem / Anthem Next (BioWare / EA, 2019~2026)
- 2019.02: Anthem 출시. 혹평·유저 이탈
- 2019~2021: 재부팅 "Anthem Next" 내부 계획. ~30명 팀 투입
- **2021.02.24**: BioWare 공식 취소 발표 (팬데믹·생산성 이유)
- 2021~2026.01: 서비스 유지하되 **신규 콘텐츠 없음**
- **2026.01**: 서버 완전 종료
- **교훈**: 복구 commitment 선언 ≠ 성공. 팀 자원·회사 우선순위가 바뀌면 중단된다

#### Marvel's Avengers (Crystal Dynamics / Square Enix, 2020~2023)
- 2020.09: 출시, 혹평
- 캐릭터 DLC 몇 개 추가 외 **재설계·확장 시도 없음**
- **2023.09.30**: 공식 지원 종료, 디지털 스토어 상품 제거
- **교훈**: Publisher가 복구 투자 의사 없으면 점진적 사망

#### 기타 복구 미시도 종료 사례
- **Battleborn** (Gearbox / 2K, 2016~2021)
- **Lawbreakers** (Boss Key, 2017~2018, Boss Key 해산)
- **Babylon's Fall** (Platinum / Square Enix, 2022~2023)
- **Suicide Squad: Kill the Justice League** (Rocksteady, 2024~2025 지원 축소)

#### 패턴 분석
복구 성공 = **(publisher 장기 투자) × (강력한 후임 director) × (외부 IP·애니메이션 등 레버리지)**. 3요소 중 하나만 빠져도 실패. Cyberpunk는 3개 모두, No Man's Sky는 1·2, FFXIV는 1·2 확보. Anthem Next는 1·2·3 모두 부재 → 취소 필연.

---

## 💵 Monetization Compliance — 지역별 규제

| 국가 | 규제 핵심 | 시행 | 실무 조치 |
|---|---|---|---|
| UK | UKGC loot box 가이드 | 2022 자율 | 확률 공시 + 부모 알림 |
| Belgium | **전면 금지** | 2018 | BE region 완전 제외 (FIFA, CoD 등) |
| Netherlands | KSA 규제 | 2018 | FIFA 패킹 금지 (2020) |
| Germany | USK 연령 병기 | 2021 | "simulated gambling" 18+ 강제 |
| China | 판호 + 확률 공시 | 2017, 2019 | 모든 콘텐츠 정부 승인 + 확률 100% 공시 |
| Korea | 확률 공시 법제화 (GIPA 시행령) | **2024.03.22** | IAP 구매 UI에 확률 명시 필수. GRAC 시정 요청 → MCST 시정명령 → **미준수 시 2년 이하 징역 또는 2천만원 이하 벌금**. 집행 100일 내 1,255건 모니터링 |
| Japan | JOGA 자율 규제 | 2012~ | complete gacha 금지 (2012 이후) |
| USA | FTC 조사·합의 | 2022.12 | Epic Games 총 **$520M** (dark patterns refund $245M + COPPA privacy $275M, FTC 역대 최대) |

> 한국 확률 공시 의무화는 AAA 글로벌 출시 시 **한국 서비스 전용 UI 대응** 필요. 전체 구매 가능한 IAP는 확률 명시 및 CSV export 기능 권장.

---

## 👥 Community Operations

### Discord 서버 표준 구조

```
📢 Announcements
📰 Patch Notes
💬 General
🎮 LFG (Looking for Group)
🐛 Bug Reports
💡 Feedback & Suggestions
🎨 Fan Art
🆘 Tech Support
🌍 Regional (JP, KR, EU 등)
🎙️ Voice Channels
```

### Mod 체제

- 3 타임존 커버 (APAC, EU, Americas)
- Mod 핸드북, 벤 기준, 24h SLA
- 유저 mod는 "Community Council" 방식 (Bungie BSL 사례)

### Patch Note 템플릿

```
# Patch 1.4.2 — 2026-06-15

## TL;DR
- 신규 보스 "Oblivion Titan" 공개
- 딜러 클래스 전면 버프
- 파티 매칭 알고리즘 개선

## New Content
- ...

## Balance Changes
- **Warrior**: 기본 공격력 120 → 135
- **Mage**: ...

## Bug Fixes
- ...

## Known Issues
- 특정 지역에서 로딩 시간 지연
```

---

## 🧪 A/B 실험 운영

### AAA 라이브 서비스 실험 표준

- **트래픽 세그먼트**: 유저 ID 해시 기반 5~20% 할당
- **실험 기간**: 최소 2주 (주말 효과 포함)
- **평가 지표**: 1차 (conversion), 2차 (D7 retention), negative guard (churn)
- **의사결정 문서**: PR 템플릿화, 모든 실험 공개 보관

### 실제 사례

- Riot Games: 하루 수십 개 A/B (Valorant 스킨 가격·노출)
- Supercell: 신규 Brawler 공개 전 5개국 소프트 런치
- Epic: Fortnite 아이템숍 아이템 노출 순서 상시 실험

---

## 📚 참고

- GDC Vault — "Live Ops" track (2020~2024)
- [Superjoost blog](https://superjoost.substack.com/) — Laasonen의 live ops 분석
- GameIndustry.biz postmortems — 최신 업계 실패/성공
- Naavik — mobile·live game analytics newsletter
- Bungie, Respawn, Digital Extremes, Larian GDC talks
- [Play Ventures](https://www.playventures.vc/) 보고서 — live ops vertical

---

*Live ops는 제작보다 길다. AAA는 3~10년 commitment를 전제로 팀·예산·KPI를 설계한다. 인디·AA도 이 playbook을 축소 적용할 수 있다.*

---

## ✅ Sources Verified (2026-04-21)

- **Concord 타임라인**: [Wikipedia — Concord](https://en.wikipedia.org/wiki/Concord_(video_game)), [PlayStation.Blog 공식 업데이트](https://blog.playstation.com/2024/09/03/an-important-update-on-concord/), [Variety — Firewalk 폐쇄 2024.10.29](https://variety.com/2024/digital/news/playstation-closes-firewalk-studios-concord-canceled-1236193942/)
- **Helldivers 2 PSN 사태**: [Game Developer — Sony reverses](https://www.gamedeveloper.com/business/sony-reverses-helldivers-2-s-account-linking-requirement), [Game Informer — PSN 철회](https://gameinformer.com/news/2024/05/06/playstation-walks-back-helldivers-2-changes-psn-account-linking-no-longer-required), [Kotaku — community backlash](https://kotaku.com/helldivers-2-psn-steam-account-linking-explained-sony-1851455071)
- **FTC Epic Games 합의**: [FTC 공식 — $520M 합의](https://www.ftc.gov/news-events/news/press-releases/2022/12/fortnite-video-game-maker-epic-games-pay-more-half-billion-dollars-over-ftc-allegations), [FTC 2023.03 최종 order — $245M refund](https://www.ftc.gov/news-events/news/press-releases/2023/03/ftc-finalizes-order-requiring-fortnite-maker-epic-games-pay-245-million-tricking-users-making)
- **FFXIV A Realm Reborn & Yoshi-P**: [Wikipedia — Naoki Yoshida](https://en.wikipedia.org/wiki/Naoki_Yoshida), [TIME — How Yoshida Saved FFXIV](https://time.com/3817373/final-fantasy-14-naoki-yoshida/)
- **한국 확률 공시법**: [PMC 논문](https://pmc.ncbi.nlm.nih.gov/articles/PMC12583229/), [Kim & Chang](https://www.kimchang.com/en/insights/detail.kc?sch_section=4&idx=29487)
