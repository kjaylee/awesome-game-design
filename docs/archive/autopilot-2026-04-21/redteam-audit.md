# 🎯 Red Team Audit — AAA Resources (Post-commit 2aa669e)

**감사일**: 2026-04-21
**대상**: `resources/production-pipeline.md` · `resources/platform-certification.md` · `resources/live-ops-playbook.md` + `README.md` 변경
**감사 목적**: 방금 peer-review 통과 후 commit 된 산출물을 **적대적 관점**에서 재검토. "완벽"이라는 자평의 허점을 노출한다.
**감사 원칙**: 선의로 제작된 점·사용자 가치·의도 좋음은 평가 축에서 제외. 오직 "이 자료를 공개 상태에서 AAA 스튜디오·법률 담당자·재무 담당자·한국 정부·상표권자·신입·사실 검증자가 보면 무엇을 지적할 것인가"만 본다.

---

## 📊 요약

| Severity | 건수 | 대표 이슈 |
|---|---|---|
| **CRITICAL** | 0 | 치명적 오류 없음 (peer review Phase에서 대부분 해소) |
| **HIGH** | 4 | Cherry-picking (복구 실패 누락), 근거 약한 수치, NDA 의심, 상세 수치 과장 |
| **MEDIUM** | 6 | Disclaimer 부재, stale 취약 수치, 지역 편향, 근거 없는 상식 주장 |
| **LOW** | 5 | 배지 유지보수 주체 불명, 한국어 전용, 패치노트 과도 단순화 등 |
| **PASS** | 3 | 개인정보 노출 0, 링크 무결성, 코드블록 균형 |

> **최종 판정**: "공개 가능 수준" OK. "완벽" 주장은 **거짓**. 공개 전에 HIGH 4건 반드시 대응 권장. MEDIUM은 1차 릴리스 후 따라잡기 가능.

---

## 🚨 HIGH Severity

### HIGH-1 · Cherry-picking — 복구 실패 사례 누락

**파일**: `resources/live-ops-playbook.md` §Launch Disaster Recovery

**주장**: Cyberpunk 2077 (2020~2023), No Man's Sky (2016~2024), FFXIV A Realm Reborn (2010~2013) 3개 복구 사례를 "redemption story" 모범으로 제시.

**공격**:
- 같은 기간 **복구 시도 후 실패**한 주요 AAA 사례가 전혀 없음
- 이는 "AAA가 commitment만 유지하면 어떤 재난도 복구 가능하다"는 위험한 낙관을 심음
- AAA 제작진·프로듀서가 본 자료를 근거로 "우리도 3년 투자하면 복구 가능"이라 결정하면 실제 실패 사례 통계를 못 보게 됨

**증거**:
- **Anthem Next**: 2021.02.24 BioWare 재부팅 취소. 약 30명 팀이 작업 중이었으나 취소. 서버는 **2026.01 완전 종료**. 복구 시도 있었으나 실패한 모범 반례
- **Marvel's Avengers (Crystal Dynamics / Square Enix)**: 2023.09.30 지원 종료. 출시 후 3년 운영했으나 **복구 시도조차 없이** 디지털 스토어 상품 제거
- 추가 누락 사례: Battleborn (2018 종료), Lawbreakers (2018), Babylon's Fall (2023), Suicide Squad: Kill the Justice League (2025 지원 축소)

**제안 수정**:
Launch Disaster Recovery 섹션 하단에 "**Recovery Failed**" 카테고리 신설.
- Anthem Next (BioWare, 2019~2026) — 2년차 복구 시도 포기, 3년차 서비스 유지, 7년차 완전 종료
- Marvel's Avengers (Crystal Dynamics, 2020~2023) — 재설계 시도 없이 점진적 사망
- 패턴: **복구 성공 = publisher commitment + 강력한 후임 director + 외부 IP 레버리지**. 하나만 빠져도 실패

**출처**: [VGC — Anthem Next cancelled](https://www.videogameschronicle.com/news/bioware-cancels-anthem-development-and-reboot-plans/), [Game Informer — Anthem 2.0 Canceled](https://gameinformer.com/2021/02/24/anthem-20-canceled-by-bioware), [Crystal Dynamics Final Update](https://avengers.crystald.com/en-us/final-update-on-the-future-of-marvels-avengers/)

---

### HIGH-2 · Uncharted 4 Vertical Slice 수치 근거 약함

**파일**: `resources/production-pipeline.md` §Pre-production — Vertical Slice (VS) 표

**주장**:
| 스튜디오 / 게임 | VS 규모 | 투입 |
|---|---|---|
| Naughty Dog / Uncharted 4 | 2 레벨 | 6개월, ~40명 |

**공격**:
- 공식 Naughty Dog 발표 또는 GDC talk에서 해당 수치 확인 불가
- WebSearch 결과: Amy Hennig(creative director) + Justin Richmond(game director)가 "약 3년 작업 후 교체", Druckmann + Straley 투입 시 **8개월치 스토리 폐기**까지만 확인
- "VS 2 레벨 / 40명 / 6개월" 세부 수치의 1차 출처 미발견
- AAA 프로듀서가 "이 수치 어디서 나왔어?" 묻는 순간 방어 불가

**제안 수정**:
- 해당 행을 **제거**하거나 "*공식 문서화 없음 — 업계 추정치*"로 라벨링
- 또는 증명 가능한 대안 사례로 교체 (Bungie Destiny Strike VS는 GDC 2014 talks에 공개 자료 존재)

**출처**: [Game Developer — Naughty Dog Uncharted 4 production process](https://www.gamedeveloper.com/production/naughty-dog-shares-a-guided-look-at-its-i-uncharted-4-i-production-process), [Wikipedia — Uncharted 4](https://en.wikipedia.org/wiki/Uncharted_4:_A_Thief's_End)

---

### HIGH-3 · NDA 의심 — 비공개 문서 구체 내용 기술

**파일**: `resources/platform-certification.md`

**주장**:
- "Sony DevNet (비공개) — TRC 2024 revision" 참고 항목 명시
- 그 아래 **리젝 TOP 10** 구체 나열 (Save crash, Trophy 오류, region lock 등 10개)
- "Publisher Panel 2023" 출처라 적음

**공격**:
- 만약 실제 Sony TRC 내용을 직간접적으로 인용한 것이라면 **NDA 위반**
- "Publisher Panel 2023"이 공개 GDC session인지 비공개 내부 회의인지 불명
- AAA 퍼블리셔 legal팀이 본 자료 공개 레포에서 자사 TRC 세부 내용 유사점 발견 시 DMCA·법적 조치 가능
- 같은 패턴이 Xbox XR·Nintendo Lotcheck에도 일부 존재

**제안 수정**:
- 비공개 참조 목록에서 "Sony DevNet (비공개)" 라인 제거 또는 "Publisher panels·퇴임 개발자 공개 talks·업계 분석 합성"으로 재프레이밍
- 리젝 TOP 10은 공개 GDC Vault talks (예: "Cert Survival Stories", Gamasutra postmortems) 출처를 각 항목에 개별 인용
- 파일 상단에 "본 문서는 공개 출처 기반 커뮤니티 분석이며, 각 플랫폼의 공식 SDK/문서·계약을 정본으로 대체하지 않는다" disclaimer 추가

---

### HIGH-4 · GTA V 개발 인력 수치 과장 가능성

**파일**: `resources/production-pipeline.md` §전체 단계 맵 하단

**주장**: "GTA V: 1,000+ (외주 포함 3,000+)"

**공격**:
- 공식 Rockstar 발표 수치: **"1,000+"** (Leslie Benzies 인터뷰)
- 일부 대중 소스(TweakTown 등)는 **"6,000+"**라고 보도 (2018 시점 발표 — 실제는 확장팩 포함 누적)
- 내가 인용한 "3,000+" 수치의 공식 근거 없음
- 숫자만 바꾼 채 출처를 합치는 실수

**제안 수정**:
- "GTA V: 1,000+ (Rockstar North core 360 + 글로벌 스튜디오 합산, 외주 비공개)"
- 또는 공식 인용: "Leslie Benzies, 2013 interview"

**출처**: [GameSpot — Rockstar More than 1,000](https://www.gamespot.com/articles/rockstar-more-than-1000-people-made-gtav/1100-6415330/), [Wikipedia — Development of Grand Theft Auto V](https://en.wikipedia.org/wiki/Development_of_Grand_Theft_Auto_V)

---

## 🟨 MEDIUM Severity

### MEDIUM-1 · 상표권 Disclaimer 전면 부재

- 신규 3개 파일에서 **Nintendo · Sony · Microsoft · Xbox · PlayStation · Valve · Epic · Apple · Google** 등 상표 **총 54건** 언급
- 어느 파일에도 "모든 상표는 각 소유자의 재산이며 본 문서는 해당 기업과 무관"이라는 notice 없음
- awesome-X 계열 공개 레포는 대부분 README 하단에 trademark notice 포함
- **제안**: 각 resources 파일 하단 또는 `README.md` footer에 trademark disclaimer 1~2줄 추가

### MEDIUM-2 · 법률 자문 Disclaimer 부재

- 한국 확률 공시법 "2년 이하 징역 또는 2천만원" 언급 (2개 파일)
- 벨기에 loot box 금지, 중국 판호, 독일 USK, FTC $520M 등 법령·규제 다수 인용
- **"본 문서는 법률 자문이 아니며, 실제 법 집행은 legal 팀 컨설팅 필요"** disclaimer 없음
- AAA publishing legal팀이 본 문서를 근거로 의사결정 시 책임 소재 분쟁 여지
- **제안**: `platform-certification.md` 상단에 "Not legal advice" disclaimer

### MEDIUM-3 · Stale-in-months 취약 수치 다수

| 위치 | 수치 | 유통기한 |
|---|---|---|
| live-ops `시즌 구조 표준` | "Fortnite Chapter 5 (2024)" | Chapter 6+ 진행 중일 가능성 높음 |
| platform-cert `Google Play` | "신규 앱 API 35 (2025.08.31~)" | 2026.08에 API 36 전환 |
| live-ops `FFXIV` | "2,400만+ 계정" | 2023 시점, 현재 더 높음 |
| live-ops `Korea` | "집행 100일 내 1,255건" | 100일 시점 snapshot, 지금은 누적 더 큼 |
| platform-cert `Apple` | ATT "iOS 14+" | iOS 17·18 신규 규정 반영 안 됨 |

- **제안**: 각 수치에 `(N년 기준)` 명시 + Sources Verified 배지에 "**갱신 권장 주기: 6개월**" 추가

### MEDIUM-4 · 근거 없는 "업계 상식" 단정 수치

`resources/live-ops-playbook.md` §KPI 대시보드:
- "DAU/MAU 0.3+ 양호" — 출처 없음
- "D1 60%+ / D7 30%+ / D30 15%+ (장르 평균)" — 출처 없음
- "Crash-free > 99.7% (AAA 표준)" — 출처 없음
- "Server uptime SLA 99.95%" — 출처 없음
- "ARPDAU·ARPPU·LTV" 정의는 정확하나 "whale share 50%+ gacha" 수치 근거 없음

- **제안**: Newzoo·Sensor Tower·GameAnalytics·Unity Gaming Report·GDC Vault 공개 리포트 링크 연결. 또는 "업계 합의 범위" 각주로 약화

### MEDIUM-5 · 지역 편향 (서구 AAA 과대, 아시아 저대)

- 신규 3개 파일 사례 분석: 서구·일본 AAA ~95%
- **한국 3N**(넥슨·엔씨·스마일게이트): 0 언급 — 한국 확률 공시법만 규제 관점 언급
- **중국 거대 퍼블리셔**(Tencent·NetEase): 직접 언급 0
- **MiHoYo**(Genshin/Honkai/Star Rail): 2~3회만
- **Supercell·King**(모바일 F2P 거성): 각 1~2회
- 한국어 공개 레포가 한국·중국 게임사 사례를 누락하는 것은 readership mismatch
- **제안**: 후속 PR에 K-게임 사례 섹션 추가 (리니지W 확률 공시 시정 요청, 배그 중국 퍼블리시 모델, Genshin 글로벌 라이브옵스)

### MEDIUM-6 · Milestone Payment 구조 출처 약함

`resources/production-pipeline.md` §Milestone Payment 구조

- 표로 Signing 15% → Prototype 10% → Alpha 20% → Beta 20% → Gold 15% → Launch 10%  제시
- 출처: "IGDA Business Contracts Compendium, GDC Business Track 2019~2024"
- 실제 해당 IGDA 문서 URL **없음**. GDC talk 특정 ID 인용 없음
- AAA 계약 변호사·퍼블리셔 재무는 "정확한 출처?" 요구 시 답변 불가
- **제안**: 표에 "업계 추정 평균. 실제 계약은 건별 편차 큼" 주석 + 확인 가능한 공개 talk 1건 링크

---

## 🟦 LOW Severity

### LOW-1 · Sources Verified 배지 유지보수 주체 불명

- 각 파일에 "✅ Sources Verified (2026-04-21)" 섹션
- 누가 · 언제 · 어떤 주기로 재검증하는지 명시 없음
- 1년 뒤에도 동일 배지 → 오히려 신뢰도 감소 위험
- **제안**: "다음 재검증 권장: 2026-10-21" 또는 CI 자동 링크 체크 명시

### LOW-2 · 한국어 전용 → 국제 접근성 한계

- 신규 3개 파일 모두 한국어 본문
- README는 영어이나 내부는 한국어 → 영어 독자는 TOC만 읽고 이탈
- awesome-design 대비 국제화 미흡
- **제안**: SKILL.en.md 계획과 묶어 별도 이슈 tracking

### LOW-3 · Patch Note 템플릿 과도 단순화

- `live-ops-playbook.md` §Patch Note 템플릿: TL;DR + New + Balance + Bug fix + Known issues
- 실제 Fortnite·CoD·FFXIV 패치노트는 50~200개 항목
- "표준" 라벨 붙이기엔 단순화 과함
- **제안**: "TL;DR 수준 템플릿. 실제 AAA 패치 노트는 10~30 섹션" 각주

### LOW-4 · Concord "2번째 짧은 MP 서비스" 주장 검증 OK지만 단편 정보

- WebSearch 결과 "The Culling 2 (8일) 다음 2번째" 확인됨 (Wikipedia 기반)
- 다만 '2번째 짧은'이 MP 전용 기준인지, 서비스형 게임 전체 기준인지 경계 모호
- **제안**: "MP 온라인 전용 서비스 게임 역대 2번째" 로 범위 명시

### LOW-5 · Discord 서버 구조 표준 과장

- `live-ops-playbook.md` §Discord 서버 표준 구조
- 실제 AAA Discord는 수십~100+ 채널. "표준"이라 하기엔 9채널 모델은 소규모
- **제안**: "인디~AA 참고 기본형. AAA Discord는 Role 기반 수십 채널로 확장" 추가

---

## ✅ PASS (감사 통과 항목)

| 항목 | 결과 | 증거 |
|---|---|---|
| 개인정보 누출 (username·이메일·경로) | ✅ PASS | 전량 `grep` 매치 0건 |
| 내부 링크 무결성 | ✅ PASS | `.md` 상대 경로 28개 모두 유효 |
| 코드블록 균형 | ✅ PASS | production=2, platform=2, live-ops=8 (모두 짝수) |
| 수치 정정 (peer review Phase) | ✅ PASS | Concord 14일, FTC $520M, Helldivers 3일, XAGs 120+, Android API 35 모두 적용 완료 |
| FFXIV 날짜 (2010.09 / 2010.12 / 2013.08.27) | ✅ PASS | 공식 Wikipedia·TIME 기사 대조 통과 |

---

## 📋 권장 조치 요약 (우선순위 순)

1. **[HIGH] Recovery 실패 사례 3건 추가** (Anthem Next / Marvel's Avengers / Battleborn)
2. **[HIGH] Uncharted 4 VS 40명 수치 제거** 또는 "추정" 라벨
3. **[HIGH] Sony DevNet "비공개" 참조 제거 후 공개 출처로 재프레이밍** (NDA 위험 차단)
4. **[HIGH] GTA V "3,000+" → "1,000+ 공식 발표"로 축소**
5. **[MEDIUM] Trademark + Not legal advice disclaimer 2종 추가** (footer 또는 상단 box)
6. **[MEDIUM] Stale 수치에 "(N년 기준)" 일괄 표기 + 갱신 주기 명시**
7. **[MEDIUM] 근거 없는 KPI 표준값에 업계 리포트 출처 연결**
8. **[MEDIUM] K-게임 / 중국 거대 퍼블리셔 사례 섹션 신규 추가** (follow-up PR)
9. **[MEDIUM] Milestone payment 표에 "업계 추정 평균" 각주 + 공개 출처 1건**
10. **[LOW] Patch note / Discord 구조를 "AAA" 라벨에서 "인디~AA" 로 재라벨**
11. **[LOW] Sources Verified 배지에 다음 재검증 예정일**

---

## 🧪 감사 방법론 (재현 가능)

이 감사는 다음을 조합했다:
- **외부 공격 (WebSearch)**: Anthem 2021/2026, Marvel's Avengers 2023, GTA V 팀 규모, Uncharted 4 VS
- **내부 Grep**: `kjaylee|@gmail|@naver|/Users/|/Volumes/|Jay Lee|010-\d` 패턴, 상표 언급 밀도
- **교차 검증**: Sources Verified 섹션의 주장 vs 실제 파일 grep
- **cherry-picking 감지**: 성공 사례만 언급하고 실패 사례를 누락했는가 질문

**재감사 명령 (6개월 후 추천)**:
```bash
# 개인정보 재확인
grep -rInE "kjaylee|@gmail|@naver|/Users/|Jay Lee" resources/ README.md

# Stale 위험 수치 재확인
grep -nE "2024|2025|Chapter [0-9]|API [0-9]{2}" resources/*.md

# 링크 유효성
grep -oE "https?://[^)]+" resources/*.md | xargs -I {} curl -I -s -o /dev/null -w "%{http_code} {}\n" {}
```

---

## ⚖️ 최종 판정

| 축 | 판정 |
|---|---|
| 공개 가능한가? | **Yes** (CRITICAL 0) |
| "완벽"인가? | **No** (HIGH 4건 존재) |
| 공개 전 필수 조치? | **HIGH 4건** |
| 6개월 내 재감사? | **권장** (Stale 수치 다수) |

"정말 완벽하지"라는 자평에 대한 답: **아니오. 4건의 HIGH severity 이슈가 있으며, 공개 전에 대응하지 않으면 AAA 실무자의 첫 번째 질문에서 무너진다.**

---

## 📚 이번 감사 출처

- [VideoGames Chronicle — Anthem reboot cancelled](https://www.videogameschronicle.com/news/bioware-cancels-anthem-development-and-reboot-plans/)
- [Game Informer — Anthem 2.0 Canceled](https://gameinformer.com/2021/02/24/anthem-20-canceled-by-bioware)
- [BioWare Blog — Anthem Update](https://blog.bioware.com/2021/02/24/anthem-update/)
- [Push Square — Anthem Shuts Down 2026](https://www.pushsquare.com/news/2026/01/biowares-biggest-failure-anthem-shuts-down-today)
- [Crystal Dynamics — Final Update on Marvel's Avengers](https://avengers.crystald.com/en-us/final-update-on-the-future-of-marvels-avengers/)
- [Escapist — Marvel's Avengers End Support](https://www.escapistmagazine.com/marvels-avengers-end-support-september-2023-crystal-dynamic-shut-down/)
- [GameSpot — Rockstar More than 1,000 made GTAV](https://www.gamespot.com/articles/rockstar-more-than-1000-people-made-gtav/1100-6415330/)
- [Wikipedia — Development of Grand Theft Auto V](https://en.wikipedia.org/wiki/Development_of_Grand_Theft_Auto_V)
- [Game Developer — Naughty Dog Uncharted 4 production process](https://www.gamedeveloper.com/production/naughty-dog-shares-a-guided-look-at-its-i-uncharted-4-i-production-process)
- [Wikipedia — Uncharted 4: A Thief's End](https://en.wikipedia.org/wiki/Uncharted_4:_A_Thief's_End)

---

*본 리포트는 자동화된 autopilot + 사람 검토 복합 산출물이다. 수정 작업은 별도 승인·지시 시 진행한다.*
