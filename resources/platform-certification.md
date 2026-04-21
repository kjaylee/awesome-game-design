# 🎮 Platform Certification — 플랫폼 인증 전수 가이드

> "우리는 2번 리젝당했다. 각각 2주 지연됐고, 총 손실은 $4M이었다."
> — Cert는 AAA 출시 일정에서 **제어 불가 리스크 1위**다.

---

## 📊 플랫폼별 비교

| 플랫폼 | 제출→승인 평균 | 체크 카테고리 | 공식 포털 | 주요 language |
|---|---|---|---|---|
| Sony PlayStation | 3~5주 | TRC 200+ | DevNet / Partner | EN, JP |
| Xbox | 2~4주 | XR 150+ | Partner Center | EN |
| Nintendo Switch | 4~8주 | Lotcheck TRC | NDI | EN, JP |
| Steam | 1~3일 | Partner checklist ~40 | partner.steamgames.com | EN |
| Apple iOS | 1~7일 | App Review | App Store Connect | EN |
| Google Play | 1~3일 | Policy + target API | Play Console | EN |
| Epic Games Store | 1~3주 | EGS checklist | dev.epicgames.com | EN |

> "제출→승인"은 **1차 통과 기준**. 리젝 시 수정·재제출로 2~3배 시간 소요 가능.

---

## 🟦 Sony PlayStation TRC (Technical Requirement Checklist)

PS5 기준 ~200개 항목. 비공개 문서(Sony DevNet 로그인 필요). 아래는 공개된 카테고리 구조와 업계 공유 지식 기반.

### 주요 카테고리

#### 1. Save & Load
- 저장 중 전원 차단 시 **데이터 손상 금지** (auto-recovery or rollback)
- Cloud save 동기화 지원
- Multiple user profile 분리 저장
- Upload/download 크기 제한 준수 (PS+ cloud storage)

#### 2. Trophy
- **Platinum 필수** (PS5, PS4 full product)
- 티어 분포 권장: Bronze 多 > Silver > Gold > Platinum 1개
- 치트·exploit 통한 unlock 방지
- 오프라인 획득 가능해야 함 (예외: 시즌 이벤트)

#### 3. PS5 DualSense
- Haptic feedback 또는 Adaptive trigger **최소 1회 활용**
- 유저가 햅틱·트리거 강도 설정에서 조정 가능
- 마이크·스피커 기능은 opt-out 가능

#### 4. Accessibility (PS5는 2023년부터 강화)
- Subtitle on/off 및 크기 조정
- Controller full remap
- High-contrast mode 권장
- Ping screen reader 호환 (메뉴)

#### 5. Regional & Legal
- Region lock 정확 적용 (가격, 언어)
- EULA·Privacy Policy 인앱 노출
- GDPR, COPPA, LGPD 대응 (지역별)

### 리젝 TOP 10 (Publisher Panel 공유, 2023)

1. Save 중 전원 cut 시 크래시 또는 손상
2. Trophy 카운팅 오류 (서버 동기화 실패)
3. Region lock 미적용 (일본 전용 DLC가 글로벌 표시)
4. Accessibility subtitle 미제공 또는 지연
5. Pause menu / 메뉴 30fps 이하 드랍
6. Platinum 획득 경로 불명확 (가이드 부재)
7. Controller disconnect → reconnect 시 입력 drop
8. Photo mode UI glitch (UI 레이어 어긋남)
9. Cross-save 문서화 부재 (동작은 하나 설명 없음)
10. End-user license 초기 실행 시 미표시

### 제출 주기 권장

- **Gold 후 4주 전 제출** (리젝 버퍼 2주 포함)
- 글로벌 출시라면 Sony Japan / America / Europe 3개 region 병렬 제출
- Day-1 patch는 cert 통과 build 별도 제출 필수

---

## 🟩 Xbox XR (Xbox Requirements)

### 주요 카테고리

#### 1. Gamerscore / Achievement
- 최소 **1000G, 30개 이상**
- 이벤트 기반 unlock (진행도, 성취, 탐험)
- 멀티플레이 achievement는 상시 달성 가능해야 (서버 종료 후 대체 경로)

#### 2. Xbox Live 연동
- Profile sync (Gamertag, avatar)
- Friend list access (LFG, invite)
- Game DVR / Share 호환 (민감 스크린 blur 허용)

#### 3. Play Anywhere (선택이지만 권장)
- Xbox + Windows 10/11 양쪽 build 제공
- 저장 데이터, achievement cross-platform

#### 4. Accessibility — XAGs (Xbox Accessibility Guidelines)

XAGs는 **120+ 가이드라인** (Microsoft Learn 2026-04 기준, XAG 101~123+ 연속 번호 체계). Xbox 플랫폼은 AAA 게임에 "Full XAG compliance"를 강하게 요구.

대표 XAG 번호:
- XAG 101: 컬러·대비
- XAG 105: 오디오 접근성
- XAG 112: 입력·컨트롤러
- XAG 117: 시각 자극·모션
- XAG 120: 컨트롤러 재매핑
- XAG 122: 인지 부하
- XAG 123: 정신건강 best practices

카테고리:
- **Input**: 전체 remap, 단일 핸드 플레이, 긴 누름 → 토글
- **Audio**: 자막, 화자 식별, 보이지 않는 소리 아이콘, 사운드 시각화
- **Visual**: 색약 모드 3종 (protanopia, deuteranopia, tritanopia), 대비 모드, HUD scale, font 크기
- **Cognitive**: 튜토리얼 재시청, 난이도 조절, 자동 전투 옵션, quest marker 토글
- **Motor**: QTE 대체, 타이밍 어시스트, aim assist

공식: [Xbox Accessibility Guidelines](https://learn.microsoft.com/en-us/gaming/accessibility/guidelines)

### Xbox 리젝 주요 사유

- Achievement 카운팅 오류
- Gamerscore 불일치 (설명 vs 실제)
- Share 기능에서 cutscene 저장 차단 누락
- XAG 핵심 항목 누락 (subtitle size, remap)

---

## 🟥 Nintendo Switch Lotcheck

Nintendo의 Lotcheck는 **가장 엄격**하기로 업계 정평.

### 특별히 엄격한 요소

#### 1. 성능 기준 이중화
- **Docked 모드** (1080p 타깃): 60fps 안정
- **Handheld 모드** (720p): 프레임 유지 또는 명시적 낮은 타깃

#### 2. JoyCon 조합
- 단일 JoyCon (가로) / 페어링 / Pro Controller / 무선 키보드 등 전 조합 지원
- JoyCon disconnect → reconnect 매끄러운 처리

#### 3. Parental Control
- Nintendo parental control 앱과 완전 연동
- 연령·시간·구매 제한 실시간 적용

#### 4. Cartridge vs eShop
- **Cart 용량**: 32GB까지. Mario Kart 8 Deluxe는 14GB로 카트 사용. AAA 대부분 eShop 추가 다운로드 함께 배포
- eShop 업로드는 **SHA 해시 검증** 엄격

### 제출 및 리젝 주기

- 첫 리젝 후 **4주 대기** 권장 (Nintendo 내부 재검토 주기)
- 글로벌 출시 시 **일본어 번역 품질** 별도 검증 (native reviewer)

---

## ⬛ Steam Partner Checklist

### Store Page 요구사항

- **Capsule 4종**: Small (231×87), Main (616×353), Wide (1920×620), Vertical (374×448)
- **Screenshot 5+** (실제 게임플레이 권장, 3:2 또는 16:9)
- **Trailer 1~3개** (Welcome, Feature, Launch)
- **Tag 20개 이하** (과도한 스팸 tag → Steam 자체 penalty)
- **Short description** 300자 이하
- **About This Game** 본문 — 8~15개 섹션 표준

### SteamPipe (빌드 업로드)

- Content build **≤ 100GB 권장** (이상 시 BitTorrent 분산 부하)
- **Depot 분할**:
  - Game (메인)
  - Language packs (각 언어)
  - DLC
  - Demo (별도 App ID)
- Build 롤백: 최대 10개 버전 보관, hotfix 시 롤백 가능
- Beta branch 활용 (`public_beta`, `prerelease` 등)

### 추가 기능 (선택)

- **Trading Cards**: Level 5+ 계정 대상 드랍 (badge craft)
- **Workshop**: UGC, Mod 지원
- **Steam Input**: 컨트롤러 universal remap
- **Remote Play Together**: 1개 계정으로 소셜 멀티플레이

### Steam 자체 심사 (Checklist)

- 유해성·저작권·성인 콘텐츠 심사 (1~3일)
- Spam / 저품질 게임 방어 (Steam Direct $100 per title)

---

## 🍎 Apple App Review (iOS · macOS · tvOS · visionOS)

### 주요 리젝 사유 (App Store Review Guidelines 2024)

- **3.1.1**: IAP 우회 (외부 웹 결제 유도)
  - Fortnite vs Apple 소송 (2020~): $1B+ 비용
  - 2024 EU DMA로 sideloading 일부 허용, 그러나 iOS 기본은 여전히 IAP 강제
- **4.3**: Spam (복제 게임, 아트 reskin)
- **5.1.1**: Privacy policy 미비
- **5.1.2**: 데이터 수집 목적 불명확
- **AppTrackingTransparency (ATT)**: iOS 14+ 의무 구현
- **Age rating**: 4+, 9+, 12+, 17+ 정확 표기

### 게임 특화 주의

- **GameCenter 권장** (필수 아님이지만 Apple 노출 우선순위 ↑)
- **CloudKit save** 지원
- **Metal 엔진 호환성** (Apple Silicon 대응)
- **iPadOS 최적화** (mouse/trackpad, Apple Pencil, Stage Manager)

### 제출 주기

- 평균 24~48시간 (간혹 7일)
- 리젝 후 Resolution Center 통해 어필 가능

---

## 🤖 Google Play

### 정책 집중 이슈 (2024~2025 기준)

- **Target API level**:
  - **신규 앱 & 업데이트**: Android 15 (API 35) 이상 (2025.08.31~)
  - **기존 앱 (mobile·Android Auto)**: Android 14 (API 34) 이상 (2024.08.31~)
  - Wear OS·Android TV: API 33, Android Automotive OS: API 32 (플랫폼별 별도 스케줄)
  - 연장 신청: 2025.11.01까지 가능 (Play Console 양식)
- **Family Policy**: 13세 미만 타깃 시 COPPA + GDPR-K 강화
- **Data Safety form**: 데이터 수집·공유 항목 자기 선언
- **Google Play Integrity API**: 서버 검증 의무 (cheat 방지)

### 주요 리젝 사유

- Policy 위반 (과도한 ad, misleading description)
- Intellectual property 침해
- Target API 미달
- Privacy policy URL 작동 불가

---

## 🟪 Epic Games Store (EGS)

### 요구사항 (2024)

- **EGS SDK**: Launcher / Online Services 통합
- **Achievements** (선택): XP + Trophy 레벨 시스템
- **Cross-progression** (선택)
- **Exclusive or multi-platform**: EGS는 exclusive 딜 시 수익 배분 12% (Steam 30% 대비)
- **Post-launch review 정책**: 매 업데이트마다 재심사 없음 (Steam과 유사)

---

## 📜 Rating / 규제 기관

| 기관 | 지역 | 비용 | 제출 방식 | 비고 |
|---|---|---|---|---|
| ESRB | 북미 | $3k~10k | Online form | Self-rating + audit |
| PEGI | EU | €1k~5k | Online | IARC 통합 |
| CERO | 일본 | ¥100k~300k | 직접 | 오프라인 심사 |
| USK | 독일 | €1.5k~5k | 직접 심사 | 폭력 게임 엄격 |
| 게임위 (GRAC) | 한국 | ₩20만~200만 | Online | **필수**. 또한 확률 공시 시정명령 미준수 시 2년 이하 징역 또는 2천만원 이하 벌금 (GIPA 시행령 2024.03.22 개정) |
| ACB | 호주 | AUD $500~2000 | Online | R18+ 존재 |
| GSRR | 대만 | NT$ 5k~20k | Online | |
| SRRC / 판호 | 중국 | 중국 퍼블리셔 필수 | 정부 승인 | **외국 직접 판매 불가** |
| IARC | 글로벌 통합 | 무료 | Online 자가 | PEGI / ESRB 자동 매핑 |

> 한국 게임위 등록: 미등록 유통 시 **형사 처벌** 가능. 글로벌 스토어라도 한국 IP 접속 차단 또는 등록 필수.
> **확률 공시법 강화 (2024.03.22~)**: GRAC가 미공시 업체에 시정 요청 → MCST 시정명령 → 미준수 시 **2년 이하 징역 또는 2천만원 이하 벌금**. 집행 시작 100일 내 1,255건 모니터링, 266건 시정 요청 실제 발동 (논문 출처: Pmc / Kim&Chang).
> 중국 판호: 2021~2022 전면 중단 → 2023 재개, 외국 게임은 여전히 제한적. **중국 퍼블리셔 (Tencent, NetEase) 없이 직접 출시 불가**.

---

## 📋 공통 Fail 사유 Top 20 (cross-platform)

1. Crash on save
2. Crash on controller disconnect
3. Memory leak (장시간 플레이 후 성능 저하)
4. Localization missing (한 언어라도 텍스트 누락)
5. Subtitle 크기 고정 (조절 불가)
6. Colorblind mode 누락
7. Remap 불가능한 버튼 존재
8. Pause menu에서 cert 요구사항 누락 (Help, Credits, Legal)
9. Platform 고유 UI 용어 위반 (PS "버튼 선택" vs Xbox "버튼 누름")
10. Online 기능이 서버 다운 시 크래시
11. Achievement 획득 후 "다시 로드"하면 재 unlock 시도
12. Cutscene skip 불가
13. Save slot 개수 부족
14. 저작권 (음악, 캐릭터, 폰트 라이선스 미클리어)
15. Legal notice 초기 누락 (Unreal, Unity "made with" 로고)
16. Rating 표기 불일치 (스토어는 T, 실 콘텐츠는 M)
17. Voice chat moderation 미구현 (Xbox, PS 필수)
18. Cross-play toggle 불가
19. Share feature에서 cutscene 저장 차단 누락 (spoiler)
20. 홈 버튼 눌러 복귀 시 오디오 지속 재생

---

## 🗓️ Cert 타임라인 표준 (AAA 출시 12주 전 기준)

```
D-84  | Beta 내부 완료, 외부 베타 종료
D-70  | Cert build #1 준비, 내부 QA full pass
D-56  | First cert submission (PS + Xbox + Switch + Steam)
D-42  | 1차 결과 수신. 리젝 시 fix sprint
D-35  | Cert build #2 submission (필요 시)
D-21  | Gold Master 확정, disc press 시작
D-14  | Digital storefront 업로드, pre-download 설정
D-7   | Day-1 patch 최종 제출
D-3   | Review 엠바고 공개
D-0   | Launch
```

---

## 📚 참고 자료

- Sony DevNet (비공개) — TRC 2024 revision
- [Xbox Requirements (XR)](https://learn.microsoft.com/en-us/gaming/xbox-live/test-release/xbox-requirements.md) (부분 공개)
- Nintendo Developer Portal (비공개)
- [App Store Review Guidelines (Apple)](https://developer.apple.com/app-store/review/guidelines/)
- [Google Play Developer Policy Center](https://support.google.com/googleplay/android-developer/topic/9858052)
- [Steamworks Partner Documentation](https://partner.steamgames.com/doc)
- GDC Vault: "Cert Survival Stories" talks (2021~2024)
- IGDA Quality of Life Committee — cert stress 이슈

---

*Cert는 품질 보증이 아닌 **최소 요건 검증**이다. AAA 스튜디오는 내부 pre-cert QA 팀을 cert 기관보다 엄격하게 운영하는 것이 표준이다.*

---

## ✅ Sources Verified (2026-04-21)

- 한국 확률 공시법 시행일 & 처벌: [PMC 연구논문](https://pmc.ncbi.nlm.nih.gov/articles/PMC12583229/), [Kim & Chang Insights](https://www.kimchang.com/en/insights/detail.kc?sch_section=4&idx=29487), [Chambers Gaming Law 2025 — South Korea](https://practiceguides.chambers.com/practice-guides/gaming-law-2025/south-korea)
- XAGs 가이드라인 번호 체계: [Microsoft Learn — Xbox Accessibility Guidelines](https://learn.microsoft.com/en-us/gaming/accessibility/guidelines), [XAG Version History](https://learn.microsoft.com/en-us/gaming/accessibility/xag-version-history)
- Google Play target API: [Play Console Help — Target API level](https://support.google.com/googleplay/android-developer/answer/11926878?hl=en), [Android Developers — Target SDK requirement](https://developer.android.com/google/play/requirements/target-sdk)
