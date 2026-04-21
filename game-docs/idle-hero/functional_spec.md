# Idle Hero - Functional Specification

## 1. 게임 개요

**게임명**: Idle Hero
**엔진**: Godot 4.4 (GL Compatibility)
**해상도**: 720×1280 (세로 모드, 모바일 최적화)
**장르**: Idle RPG / 자동 전투 수집형
**배포 목표**: eastsea.monster (HTML5 Web Export)

## 2. 기술 스택

| 항목 | 상세 |
|------|------|
| 게임 엔진 | Godot 4.4 |
| 렌더러 | GL Compatibility |
| 개발 언어 | GDScript |
| 데이터 저장 | localStorage (Web) + FileAccess (Fallback) |
| 싱글턴 (Autoload) | EventBus, GameManager, DataManager, BattleManager, SaveManager |
| UI 프레임워크 | Godot UI System (Control nodes) |

## 3. 핵심 시스템 명세

### 3.1 영웅 수집 시스템 (Hero Collection)

#### 영웅 데이터베이스
- **총 영웅 수**: 14명
- **저장소**: HeroDatabase (스크립트 또는 JSON)
- **영웅 속성**:
  - `id`: 영웅 고유 ID (1-14)
  - `name`: 영웅명
  - `rarity`: 레어도 (Common, Rare, Epic, Legendary)
  - `element`: 속성 (Fire, Water, Wind, Light, Dark)
  - `baseStats`: 기본 스탯 (HP, ATK, DEF, SPD)
  - `skills`: 보유 스킬 배열
  - `resonanceTag`: 공명 태그 (Warrior, Mage, Healer, etc.)
  - `portrait`: 초상화 경로
  - `level`: 현재 레벨 (1-100)
  - `experience`: 현재 경험치

#### 영웅 강화 시스템
- **경험치 획득**: 전투 완료 시 경험치 획득
- **레벨 상한**: Lv.100
- **강화 재료**: 전투 드롭 또는 미션 보상
- **장비 시스템**: 각 영웅마다 슬롯별 장비 장착 가능 (추후 확장)

### 3.2 진형 시스템 (Formation)

#### 파티 구성
- **파티 크기**: 6명 (3(Front) + 3(Back) 배치)
- **Front Line**: 전방 3명 (탱크/딜러 중심)
- **Back Line**: 후방 3명 (마법사/힐러 중심)
- **편성 가능 최소**: 1명 (나머지 슬롯은 선택사항)

#### 진형 배치 규칙
```
Front [0] [1] [2]
Back  [3] [4] [5]
```
- 동일 영웅 중복 배치 불가능
- 언제든 변경 가능

### 3.3 공명 시스템 (Resonance)

#### 공명 활성화
- **조건**: 파티에 특정 공명 태그를 가진 영웅들이 포함될 때
- **공명 유형** (예시):
  - **Warrior Synergy**: Warrior 태그 영웅 3명 → ATK +15%
  - **Mage Synergy**: Mage 태그 영웅 3명 → MAT +20%
  - **Healer Bond**: Healer 태그 영웅 2명 → 회복량 +25%
  - **Multi-Element**: 서로 다른 속성 5명 → 모든 스탯 +10%

#### 공명 보너스
- **스탯 부스트**: ATK, MAT, DEF, MDF, SPD 중 선택적 증가
- **특수 효과**: 특정 공명 조합 시 특수 스킬 언락 (추후 확장)

### 3.4 가챠 시스템 (Summon Gacha)

#### 가챠 메커니즘
- **가챠 타입**: 
  - 일반 소환 (3성 이상 보장)
  - 특급 소환 (5성 이상 보장)
- **확률**:
  - 3성 (Common): 50%
  - 4성 (Rare): 35%
  - 5성 (Epic): 12%
  - 6성 (Legendary): 3%

#### Pity 시스템
- **Pity Counter**: 가챠 횟수 누적 추적
- **보장 조건**:
  - 일반 소환: 50회 이상 시 3성 이상 보장
  - 특급 소환: 30회 이상 시 5성 이상 보장
- **리셋**: Pity 목표 달성 시 카운터 초기화

#### 소환 비용
- **골드**: 게임 내 통화 소비
- **소환권**: 특수 아이템 (미션/이벤트 보상)

### 3.5 턴제 자동 배틀 시스템 (Auto Battle)

#### 배틀 기본 규칙
- **턴 방식**: 속도(SPD) 기반 턴제
- **자동 진행**: 유저 입력 없이 AI가 자동 선택
- **전투 종료**: 한 팀 전멸 시 종료

#### 스킬 시스템
- **스킬 타입**:
  - 물리 스킬 (ATK 스탯 기반)
  - 마법 스킬 (MAT 스탯 기반)
  - 힐 스킬 (MAT 스탯 기반)
  - 상태이상 스킬 (확률 기반)

#### 에너지/궁극기 시스템
- **에너지 게이지**: 각 영웅마다 0-100
- **에너지 축적**:
  - 턴 시작 시 고정 +15
  - 피격 시 +10
  - 공격 시 +5
- **궁극기 발동**: 에너지 100 도달 시 자동 발동
- **궁극기 효과**: 광역 고대미지 또는 특수 버프/디버프

#### 쿨다운 시스템
- **스킬별 쿨다운**: 1~3턴 (스킬마다 상이)
- **쿨다운 계산**: 턴 경과 시 자동 감소
- **쿨타임 스킬 선택**: 사용 불가 시 기본 공격

#### AI 전투 로직
1. 에너지 100이면 궁극기 우선 사용
2. 아군 HP < 30% 시 힐 스킬 우선 (힐러)
3. 적 HP > 70% 시 강력한 스킬 우선 (딜러)
4. 쿨다운 완료된 스킬 우선
5. 사용 불가 시 기본 공격

### 3.6 오프라인 보상 (Idle Rewards)

#### 오프라인 보상 계산
- **시간 추적**: 마지막 플레이 시간 기록
- **보상 공식**:
  ```
  reward = baseReward × (elapsedHours / 2) × goldMultiplier
  (최대 12시간 기준, 이후 일정량으로 상한 고정)
  ```
- **보상 종류**:
  - 골드 (메인 통화)
  - 경험 포션 (영웅 경험치)
  - 소환권 (낮은 확률)

#### 자동 보상 획득
- 게임 실행 시 자동 계산 및 지급
- 팝업 UI로 보상 내역 표시

### 3.7 캠페인 시스템 (Campaign)

#### 챕터 구성
- **Chapter 1**: 1-1 ~ 1-10 스테이지 (총 10개)
- **스테이지 구성**:
  - 스테이지명, 권장 레벨
  - 적 편성 (3명 또는 6명)
  - 획득 보상 (골드, 경험치, 아이템)
  - 클리어 조건 (전투 승리)

#### 진행 시스템
- **잠금 해제**: 직전 스테이지 클리어 시 다음 스테이지 해제
- **재도전**: 언제든 이전 스테이지 재도전 가능
- **보상**: 초회 클리어 및 재도전 시 동일 보상

### 3.8 저장 시스템 (Save System)

#### 저장 데이터 항목
```json
{
  "userId": "uuid",
  "lastPlayTime": "ISO8601",
  "heroes": [
    {
      "id": 1,
      "level": 45,
      "experience": 2500,
      "equipment": [...]
    }
  ],
  "party": [0, 1, 2, 3, -1, -1],
  "campaign": {
    "unlockedStage": 7,
    "clearedStages": [1, 2, 3, 4, 5, 6]
  },
  "currency": {
    "gold": 50000,
    "summonTickets": 3
  },
  "gacha": {
    "normalPity": 25,
    "rarePity": 12
  }
}
```

#### 저장 전략
- **로컬 저장**: localStorage (Web) 우선
- **Fallback**: FileAccess (Desktop 빌드)
- **자동 저장**: 주요 액션 후 즉시 저장 (영웅 레벨업, 진형 변경, 전투 완료)
- **수동 저장**: 메인 메뉴에서 "저장" 버튼 제공

## 4. UI/UX 명세

### 4.1 화면 구성

| 화면명 | 기능 | 전환 |
|--------|------|------|
| **MainScreen** | 메인 메뉴, 게임 입장 | 게임 시작 → HeroList |
| **HeroList** | 영웅 목록 조회, 선택 | 영웅 선택 → HeroDetail |
| **HeroDetail+Upgrade** | 영웅 상세정보, 강화 | 강화 버튼 → 경험치 소비 |
| **Formation** | 파티 편성 화면 | 영웅 선택 → 슬롯 배치 |
| **CampaignSelect** | 챕터 선택, 스테이지 선택 | 스테이지 선택 → Battle |
| **Battle** | 자동 전투 진행 | 전투 중 → BattleResult |
| **BattleResult** | 전투 결과, 보상 표시 | 확인 → CampaignSelect |
| **SummonScreen** | 가챠 소환, 결과 표시 | 소환 → 결과 애니메이션 |

### 4.2 UI 요소

#### MainScreen
- 게임 타이틀 + 슬로건 배너
- "게임 시작" 버튼
- "영웅" 버튼 → HeroList
- "진형 편성" 버튼 → Formation
- "캠페인" 버튼 → CampaignSelect
- "소환" 버튼 → SummonScreen
- 오프라인 보상 팝업 (게임 시작 시)
- 현재 골드/소환권 표시

#### HeroList
- 영웅 목록 (그리드 또는 리스트)
- 각 영웅: 초상화, 이름, 레벨, 레어도 뱃지
- 선택 시 HeroDetail로 전환
- "뒤로가기" 버튼

#### HeroDetail+Upgrade
- 영웅 초상화 (대형)
- 영웅 정보: 이름, 레어도, 속성, 공명 태그
- 현재 스탯 표시 (HP, ATK, DEF, SPD, MAT, MDF)
- 스킬 목록 (이름, 설명, 쿨다운)
- 경험치 바 + 다음 레벨까지 필요 경험치
- "강화" 버튼 (경험 포션 소비) → 레벨업 애니메이션
- "뒤로가기" 버튼

#### Formation
- Front/Back 라인 시각화 (6개 슬롯)
- 각 슬롯: 선택된 영웅 또는 "빈 슬롯"
- 슬롯 클릭 → 영웅 선택 팝업
- 공명 효과 표시 (활성화된 보너스 리스트)
- "확인" 버튼 → 편성 저장
- "뒤로가기" 버튼

#### CampaignSelect
- 챕터 타이틀 ("Chapter 1")
- 스테이지 목록 (1-1 ~ 1-10)
- 각 스테이지: 이름, 권장 레벨, 클리어 여부 표시
- 스테이지 선택 → Battle 진입
- "뒤로가기" 버튼

#### Battle
- 아군 진형 (상단, Front 3 + Back 3)
- 적군 진형 (하단, 미러링)
- 각 영웅: HP 바, 에너지 게이지, 상태이상 아이콘
- 현재 턴 수 표시
- 전투 로그 (또는 스킵 옵션)
- 자동 진행 중 (유저 조작 불가)

#### BattleResult
- "승리" / "패배" 결과 표시
- 획득 경험치 + 골드 표시
- 각 영웅 경험 분배 정보
- 드롭 아이템 목록
- "다음" 버튼 → CampaignSelect

#### SummonScreen
- 가챠 풀 정보 (확률 표시)
- 소환 타입 선택 (일반, 특급)
- "1회 소환" / "10회 소환" 버튼
- 소환 비용 표시 (골드 또는 소환권)
- Pity 진행상황 표시
- 소환 결과 애니메이션 (카드 오픈 효과)
- "뒤로가기" 버튼

### 4.3 팝업 및 다이얼로그

| 팝업명 | 용도 |
|--------|------|
| **오프라인 보상** | 게임 실행 시 오프라인 보상 표시 |
| **영웅 선택** | Formation 화면에서 슬롯별 영웅 선택 |
| **강화 확인** | HeroDetail에서 경험 포션 소비 확인 |
| **소환 결과** | SummonScreen에서 소환 결과 표시 |
| **에러 알림** | 불가능한 액션 시 알림 (예: 골드 부족) |

## 5. 데이터 구조

### 5.1 Hero 데이터 스키마
```gdscript
class_name Hero
var id: int
var name: String
var rarity: String  # "Common", "Rare", "Epic", "Legendary"
var element: String  # "Fire", "Water", "Wind", "Light", "Dark"
var level: int = 1
var experience: int = 0
var baseStats: Dictionary = {
  "hp": 0,
  "atk": 0,
  "def": 0,
  "spd": 0,
  "mat": 0,
  "mdf": 0
}
var skills: Array[Skill]
var resonanceTag: String
var portrait: String
var equipment: Dictionary = {}  # slot -> Item
```

### 5.2 Party 데이터 스키마
```gdscript
class_name Party
var slots: Array[int] = [-1, -1, -1, -1, -1, -1]  # Hero IDs
var resonances: Array[String] = []  # 활성화된 공명 태그

func add_hero(slot: int, hero_id: int) -> bool:
  if slots[slot] == -1 and hero_id not in slots:
    slots[slot] = hero_id
    return true
  return false

func remove_hero(slot: int) -> void:
  slots[slot] = -1

func get_resonance_bonus() -> Dictionary:
  # 현재 파티의 공명 보너스 반환
  pass
```

### 5.3 Battle State 데이터 스키마
```gdscript
class_name BattleState
var allies: Array[BattleCharacter]
var enemies: Array[BattleCharacter]
var currentTurn: int = 0
var battleLog: Array[String]

class_name BattleCharacter
var hero: Hero
var currentHP: int
var energy: int = 0
var skills_cooldown: Dictionary  # skill_id -> remaining_turns
var buffs: Array[Buff]
var debuffs: Array[Debuff]
```

### 5.4 Gacha State 데이터 스키마
```gdscript
class_name GachaState
var normalPity: int = 0
var rarePity: int = 0
var lastSummonTime: String = ""

func pull(type: String) -> Hero:
  # 가챠 로직 실행
  # Pity 증가/초기화
  pass
```

## 6. 렌더링 및 애니메이션 명세

### 6.1 시각 효과

| 효과명 | 타이밍 | 지속시간 |
|--------|--------|----------|
| **레벨업 애니메이션** | 영웅 강화 완료 시 | 1.0초 |
| **스킬 발동 이펙트** | 스킬 사용 시 | 0.8초 |
| **히트 플래시** | 피격 시 | 0.2초 |
| **궁극기 연출** | 궁극기 발동 | 1.5초 |
| **전투 승리 연출** | 전투 종료 (승리) | 2.0초 |
| **카드 오픈 이펙트** | 소환 결과 | 1.2초 |

### 6.2 애니메이션 구현

#### 영웅 이동 애니메이션 (전투)
```gdscript
var tween = create_tween()
tween.tween_property(hero_node, "position", target_pos, 0.3)
```

#### 스킬 발동 연출
- 스킬 사용 영웅 강조 (스케일 업 1.1배)
- 대상 영웅 강조 (색상 오버레이)
- 데미지 수치 플로팅 (상단 이동 + 페이드아웃, 0.5초)

#### 레벨업 이펙트
- 배경 플래시 (흰색, 0.2초)
- 영웅 스케일 업/다운 (1.0 → 1.15 → 1.0, 0.8초)
- 파티클 이펙트 (별 모양, 상단 분출)

### 6.3 UI 전환 애니메이션

#### 화면 이동
- Fade In/Out: 0.3초
- Slide (좌우): 0.4초

#### 버튼 상호작용
- Press: 스케일 축소 (1.0 → 0.95)
- Release: 스케일 복원 (0.95 → 1.0)
- Hover: 색상 변경 (밝기 +10%)

### 6.4 파티클 시스템

#### 전투 이펙트
- **근거리 공격**: 먼지 파티클 (황색, 3-5개)
- **원거리 공격**: 궤적 파티클 (파란색, 경로 따라)
- **마법 공격**: 마법진 파티클 (보라색, 원형 확산)
- **힐 효과**: 별 파티클 (초록색, 상향 분출)

#### 소환 이펙트
- **일반 영웅**: 흰색 별빛 (3개)
- **레어 영웅**: 노란색 별빛 (5개)
- **레전더리 영웅**: 황금색 별빛 + 신비로운 음향 (7개)

## 7. 배포 사양

- **배포 대상**: HTML5 Web Export
- **배포 URL**: eastsea.monster
- **브라우저 호환성**: Chrome, Firefox, Safari (모바일 최적화)
- **최소 해상도**: 720×1280
- **성능 목표**: 60 FPS (중간 사양 기기 기준)
