# 📖 Narrative Design 심화

> 게임에서 스토리를 "쓰는 것"이 아니라 "플레이하게 만드는 것". 내러티브 디자이너는 작가이자 시스템 디자이너다.

---

## 🛠️ 도구 (Tools)

### Twine
**링크**: [twinery.org](https://twinery.org/)  
**라이선스**: 오픈소스 (무료)  
**사용 목적**: 비선형 인터랙티브 픽션, 프로토타이핑

Twine은 HTML 기반 인터랙티브 스토리 도구로, 코딩 없이 분기 내러티브를 만들 수 있다.

**적합한 사용 사례**:
- 대화 시스템 프로토타이핑
- 스토리 구조 검증 (실제 엔진 구현 전)
- 텍스트 기반 인디 게임 (80 Days, Depression Quest 스타일)

**핵심 기능**:
```
Passage (노드) → 링크로 연결 → 변수로 상태 관리
[[링크 텍스트->목적 노드]]
(if: $has_key)[[열쇠로 문을 열다->door_open]]
(else:)[[자물쇠를 확인하다->locked_door]]
```

**팁**: Twine으로 먼저 전체 스토리 구조를 시각화한 후 실제 엔진에 구현하면 구조적 문제를 조기에 발견할 수 있다.

---

### Ink / Inky
**링크**: [inklestudios.com/ink](https://www.inklestudios.com/ink/)  
**제작**: Inkle Studios (80 Days, Heaven's Vault 개발사)  
**라이선스**: MIT (오픈소스)  
**Unity 통합**: 공식 지원

Ink는 내러티브 게임을 위한 스크립트 언어. Inkle Studios가 자사 게임 개발을 위해 만들었으며, 현재 업계 표준 도구 중 하나.

**문법 예시**:
```ink
=== 첫_만남 ===
낯선 사람이 다가온다.
* [손을 내밀다]
    그가 악수를 한다. -> 친근한_대화
* [고개만 끄덕이다]
    어색한 침묵. -> 짧은_대화
* [무시하다]
    그가 등을 돌린다. -> 적대적_관계

=== 친근한_대화 ===
"오래 기다리셨나요?" 그가 웃으며 말한다.
~ trust += 1
-> 대화_계속

=== 짧은_대화 ===
"바쁘신가요?" 짧은 인사. -> 대화_계속
```

**주요 기능**:
- `~` 변수 선언 및 조작
- `->` 분기 이동
- `(조건)` 분기 조건
- `CHOICE` 선택지
- 가중치 랜덤 대화 (`+ [3]일반 대화`)

**실제 사용 게임**: Heaven's Vault, 80 Days, Sable, Disco Elysium (초기 프로토타입)

---

### Yarn Spinner
**링크**: [yarnspinner.dev](https://yarnspinner.dev/)  
**엔진 통합**: Unity, Godot, Unreal
**라이선스**: MIT (오픈소스)

Unity 생태계에서 가장 널리 쓰이는 대화 시스템. Night in the Woods, A Short Hike의 대화 시스템.

**문법 예시**:
```yarn
title: MeetingNPC
---
NPC: 안녕하세요. 처음 뵙는 것 같은데요.
-> 네, 처음 왔어요.
    NPC: 환영합니다!
    <<set $visited_town = true>>
-> 아는 척하다
    NPC: ...어, 기억이 안 나는데요.
===
```

**Ink vs Yarn Spinner 비교**:

| 항목 | Ink | Yarn Spinner |
|------|-----|--------------|
| 학습 곡선 | 중간 | 낮음 |
| Unity 통합 | 공식 | 공식 |
| Godot 지원 | 서드파티 | 공식 |
| 복잡한 분기 | 강점 | 보통 |
| 커뮤니티 | 중간 | 활발 |

---

### articy:draft
**링크**: [articy.com](https://www.articy.com/)  
**가격**: 유료 (팀 규모별 구독)  
**엔진 통합**: Unity, Unreal (공식)

전문 게임 스튜디오를 위한 내러티브 설계 통합 도구. 대화 트리, 세계관 문서, 캐릭터 DB, 플로우차트를 하나의 도구에서.

**주요 기능**:
- 비주얼 플로우차트 대화 편집기
- 엔티티 DB (캐릭터, 장소, 아이템)
- 버전 관리
- Unity/Unreal 실시간 동기화

**적합한 사용**: AA/AAA 규모 팀, 복잡한 분기가 있는 RPG

---

### Obsidian (게임 작가용)
**링크**: [obsidian.md](https://obsidian.md/)  
**라이선스**: 개인 무료, 팀 유료

노트 앱이지만 게임 세계관 구축에 최적화됨. 양방향 링크로 설정 문서 간 관계를 시각화.

**게임 작가 활용법**:
- 각 NPC를 노트로 관리 (관계, 역사, 대화 어조)
- 세계관 역사를 타임라인으로 구성
- Graph View로 설정 간 연결 관계 시각화
- 플레이어 선택에 따른 세계 상태 변화 추적

**폴더 구조 예시**:
```
World/
├── Characters/
│   ├── Protagonist.md
│   ├── Antagonist.md
│   └── NPCs/
├── Lore/
│   ├── History.md
│   └── Factions.md
├── Quests/
│   ├── Main Story/
│   └── Side Quests/
└── Dialogue/
    └── Draft Scripts/
```

---

## 📐 이론 (Theory)

### Save the Cat 비트 시트 — Blake Snyder

영화 시나리오 방법론을 게임 내러티브에 적용한 구조. 15개의 "비트"가 감정 여정을 설계.

**게임 적용 시 핵심 조정**:
- 영화: 수동적 관람 → 게임: 능동적 참여
- 플레이어가 주인공 = 주인공의 실패가 플레이어의 실패
- 각 비트가 "게임플레이 사건"과 일치해야 함

```
게임 비트 시트 예시 (15비트):

[1] 오프닝 이미지 (0~1%)
    → 오프닝 시네마틱 or 첫 화면
    → "이 세계는 이런 곳이다"

[2] 테마 스테이트먼트 (5%)
    → 첫 NPC 대화에 숨겨진 주제 힌트
    → "이 게임이 말하고 싶은 것"

[3] 셋업 (1~10%)
    → 플레이어 캐릭터의 결핍 상태
    → 튜토리얼 구간과 겹침

[4] 촉매 (10%)
    → 첫 번째 주요 사건
    → 메인 퀘스트 시작 트리거

[5] 논쟁 (10~25%)
    → "해야 할까, 말아야 할까"
    → 도전/동기를 확립하는 구간

[6] 2막 진입 (25%)
    → 첫 번째 주요 지역 이동
    → 새 메카닉 언락

[7] B-스토리 (30%)
    → 로맨스 라인 or 동료 캐릭터 등장
    → 감정적 서포트 서브플롯

[8] 재미와 게임 (30~55%)
    → 핵심 콘텐츠 구간
    → 가장 "게임다운" 구간

[9] 중간점 (50%)
    → 거짓 승리(False Victory): 보스 처치, 아이템 획득
    → 또는 거짓 패배(False Defeat): 빌런에게 패배
    → 중간 반전이 긴장감 유지

[10] 나쁜 놈의 역습 (55~75%)
    → 적이 반격, 상황 악화
    → 난이도 스파이크 구간

[11] 모두 잃음 (75%)
    → 동료 사망, 기지 파괴, 핵심 아이템 분실
    → 감정적 저점

[12] 영혼의 어두운 밤 (75~80%)
    → 비대화적 순간: 느린 걷기, 회상 시퀀스
    → 플레이어와 캐릭터의 내성 공간

[13] 3막 진입 (80%)
    → 새로운 해결책 발견
    → 마지막 힘을 내는 동기

[14] 피날레 (80~99%)
    → 최종 던전, 최종 보스
    → 모든 서브플롯 해결

[15] 최종 이미지 (99~100%)
    → 변화를 상징하는 마지막 장면
    → 오프닝 이미지와 대조
```

---

### 히어로의 여정 (The Hero's Journey)

Joseph Campbell의 원형에서 Christopher Vogler가 정리한 12단계 구조.

**12단계 + 게임 구현**:

```
1. 일상 세계 (Ordinary World)
   → 홈 마을, 기본 튜토리얼 존
   → 플레이어가 잃을 것이 있는 상태 확립

2. 모험의 부름 (Call to Adventure)
   → 메인 퀘스트 NPC 등장
   → 세계가 위험에 처했다는 신호

3. 부름의 거부 (Refusal of the Call)
   → 옵션: 플레이어가 선택 가능한 망설임
   → "아직 준비가 안 됐다"는 내적 갈등

4. 멘토와의 만남 (Meeting with the Mentor)
   → 튜토리얼 가이드 NPC
   → 핵심 무기/스킬 부여

5. 1차 관문 통과 (Crossing the Threshold)
   → 홈 마을을 떠나는 포인트
   → 귀환이 불가능하거나 어려워짐

6. 시련/동료/적 (Tests, Allies, Enemies)
   → 중반 던전, 동료 캐릭터 합류
   → 세계의 규칙을 배우는 구간

7. 가장 깊은 동굴 (Approach to the Inmost Cave)
   → 최종 보스 성이나 적의 본거지 진입 전
   → 긴장감 최고조

8. 시련 (The Ordeal)
   → 중간 클라이맥스, 주요 적 격파
   → 캐릭터 변화의 계기

9. 보상 (Reward/Seizing the Sword)
    → 맥거핀 아이템 획득, 진실 발견
    → 짧은 승리의 시간

10. 귀환의 길 (The Road Back)
    → 최종 보스를 향한 진군
    → 빌런의 마지막 방해

11. 부활 (Resurrection)
    → 최종 보스전, 최고의 위기
    → 주인공의 진정한 변화 순간

12. 영약 귀환 (Return with the Elixir)
    → 엔딩, 세계가 구원됨
    → 주인공이 가져온 것 (교훈, 평화, 물건)
```

---

### 비선형 스토리텔링 원칙

비선형 스토리는 단순히 "선택지가 있는 것"이 아니다.

**레벨 1 — 코스메틱 선택 (표면적 분기)**
```
다른 대화 → 같은 결과
플레이어는 선택감을 느끼지만 실제 분기 없음
예: 대부분의 JRPGs "예/아니오" 대화
장점: 제작 비용 낮음
단점: 장기적 플레이어 불신
```

**레벨 2 — 짧은 분기 (Short-term Branching)**
```
선택 → 다른 장면 → 같은 중심 스토리로 수렴
예: The Walking Dead (Telltale)
장점: 의미있는 선택감, 합리적 제작 비용
단점: 엔딩이 거의 같다는 것을 알게 될 때 실망
```

**레벨 3 — 누적 세계 상태 (World State Accumulation)**
```
선택들이 누적되어 세계의 현재 상태를 만듦
예: Dragon Age: Origins, The Witcher 3
장점: 진짜 플레이어 자율성
단점: 테스트 비용 기하급수적 증가
```

**레벨 4 — 시스템적 내러티브 (Systemic Narrative)**
```
플레이어가 메카닉으로 고유한 스토리를 만들어냄
예: Dwarf Fortress, RimWorld, Crusader Kings
장점: 무한 재플레이, 유저 생성 스토리
단점: 단일 강력 스토리 불가능
```

---

## 🎭 대화 시스템 설계 패턴

### 패턴 1: 감정 스펙트럼 선택지

단순한 "예/아니오" 대신 감정 상태로 분류:
```
[동정적으로] "당신의 상황을 이해해요."
[중립적으로] "그래서 어쩌라고요."  
[냉소적으로] "그게 내 문제인가요?"
[공격적으로] "그 거짓말 집어치워요."
```

**장점**: 캐릭터 개성 투사, 도덕적 딜레마 생성  
**사용 사례**: Disco Elysium, Mass Effect

### 패턴 2: 정보/스킬 기반 잠금

특정 스킬이나 정보 보유 시 새 선택지 등장:
```
[일반] "뭔가 이상하네요."
[지식:의학] "저 상처는 칼이 아니라 독에 의한 것이에요." (조사 10+)
[관찰] "손이 떨리고 있군요. 거짓말하고 있네요." (지각 8+)
```

**장점**: 스킬 투자에 의미 부여, 탐험 욕구 자극  
**사용 사례**: Fallout (1, 2), Baldur's Gate, Disco Elysium

### 패턴 3: 시간 제한 선택지

선택하지 않으면 기본값이 적용되는 타이머:
```
[3초] [신뢰한다] → 3초 후 자동: [침묵을 유지한다]
```

**장점**: 긴장감 상승, "즉각적 판단" 감정  
**사용 사례**: Mass Effect, 대부분의 텔테일 게임

### 패턴 4: 관계 상태 반영 대화

NPC가 이전 상호작용을 기억하고 반영:
```
// 이전에 도움을 줬다면
NPC: "당신이 뭘 하든 믿어요. 전에 증명해줬잖아요."

// 이전에 거절했다면  
NPC: "...또 당신이군요. 뭘 원하는 건지 모르겠어요."
```

**구현**: 플래그 변수 + 대화 조건 분기

---

## 🌍 세계관 구축 방법론

### 1세계관 바이블 (World Bible) 구조

```
Chapter 1: 핵심 컨셉 (Core Concept)
- "이 세계는 한 마디로 ___이다"
- 무엇이 일반 세계와 다른가?
- 중심 갈등/긴장

Chapter 2: 역사 (History)
- 세계의 기원
- 주요 시대 구분
- 현재 상태를 만든 사건

Chapter 3: 지리 (Geography)
- 지도 (또는 지도 묘사)
- 각 지역의 특성
- 이동 방법/비용

Chapter 4: 세력 (Factions)
- 각 세력의 목표, 방법, 약점
- 세력 간 관계 (동맹/적대)
- 플레이어와의 관계

Chapter 5: 문화 (Culture)
- 종교/신화
- 기술 수준
- 사회 구조 (계급, 성별 역할)
- 언어/문자

Chapter 6: 경제 (Economy)
- 화폐 시스템
- 희소 자원
- 무역 루트

Chapter 7: 규칙 (Rules)
- 마법/기술의 한계
- 무엇이 가능하고 불가능한가
- 이 세계의 "물리 법칙"
```

### 환경 스토리텔링 기법

텍스트 없이 스토리를 전달하는 레벨 디자인 기법:

**Dead Space 방식 — 피의 흔적**
- 발자국, 혈흔, 긁힌 자국이 사건을 암시
- 플레이어가 추론하게 만드는 증거 배치

**Dark Souls 방식 — 아이템 설명**
- 아이템 하나에 역사의 조각이 담김
- 플레이어가 조각들을 모아 전체 그림을 구성

**Firewatch 방식 — 물리적 흔적**
- 누군가가 살았던 흔적 (빈 캔, 낙서, 노트)
- 부재하는 인물을 현존하게 만드는 기법

---

## 📚 참고 자료

| 자료 | 유형 | 추천 이유 |
|------|------|-----------|
| [Narrative Design (Edwin McRae)](https://narrativedesign.org/) | 웹사이트 | 업계 전문가 블로그 |
| [The Anatomy of Story (John Truby)](https://www.amazon.com/Anatomy-Story-Storytelling-Principles-Screenwriter/dp/0865479518) | 책 | 스토리 구조 바이블 |
| [Story (Robert McKee)](https://www.amazon.com/Story-Substance-Structure-Principles-Screenwriting/dp/0060391685) | 책 | 시나리오 작법 고전 |
| [Hamlet on the Holodeck (Janet Murray)](https://www.amazon.com/Hamlet-Holodeck-Updated-Future-Narrative/dp/0262534541) | 책 | 인터랙티브 내러티브 이론 |
| [GDC Narrative Summit](https://gdcvault.com/search.php#&category=free&firstfocus=&keyword=narrative+summit) | 강연 | 최신 업계 트렌드 |
| [Inkle Studios Blog](https://www.inklestudios.com/blog/) | 블로그 | Ink 도구 개발사 |
| [Emily Short's Interactive Storytelling](https://emshort.blog/) | 블로그 | 인터랙티브 픽션 비평/이론 |
