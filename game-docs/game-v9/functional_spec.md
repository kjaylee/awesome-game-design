## game-v9 기능 명세서

### 개요
Python 기반 HTML5 Canvas + Vanilla JavaScript 게임 생성기 v9입니다. AI 동반자/NPC 시스템, 동적 난이도 조정, 점진적 공개 메카닉을 통합하여 10개의 AI 강화형 게임을 생성합니다.

### 기술 스택
- **백엔드**: Python 3.x (gen_v9.py)
- **프론트엔드**: HTML5 Canvas, Vanilla JavaScript (ES6+)
- **AI 엔진**: 상태 머신 기반 NPC AI
- **난이도 조정**: 플레이어 성능 메트릭 분석
- **저장소**: localStorage + 클라우드 동기화

### 핵심 기능

#### 1. AI Companion/NPC 시스템
- **독립적 NPC 제어**: 자체 목표, 행동 패턴
- **동적 상호작용**: 플레이어 행동에 반응
- **프로시저럴 대화**: 상황별 텍스트 생성
- **성격 시스템**: 각 NPC의 고유한 성격 특성

#### 2. Dynamic Difficulty Adjustment (DDA)
- **성능 분석**: 클리어 타임, 시도 횟수, 실패율 추적
- **자동 난이도 변경**: 플레이어 기술 수준에 맞춤
- **쿨다운 시스템**: 급격한 난이도 변화 방지
- **투명성 UI**: 현재 난이도 단계 표시

#### 3. Progressive Disclosure
- **단계적 튜토리얼**: 처음 3 레벨에서 메카닉 점진 공개
- **팁 시스템**: 플레이어 행동 분석 후 맞춤형 팁 제공
- **잠금 해제 메카닉**: 레벨 진행에 따라 기능 언락
- **온보딩 플로우**: 신규 플레이어를 위한 부드러운 시작

### 시스템 아키텍처

#### NPC AI 엔진
```
NPCController
  ├─ StateManager (Idle, Wander, Attack, Interact)
  ├─ BehaviorTree (의사결정 로직)
  ├─ MemorySystem (플레이어 행동 기억)
  ├─ DialogueSystem (대화 생성)
  └─ GoalManager (장기/단기 목표)
```

#### DDA 엔진
```
DifficultyManager
  ├─ PerformanceTracker (메트릭 수집)
  ├─ EvaluationEngine (성능 분석)
  ├─ AdjustmentCalculator (난이도 계산)
  └─ ConfigurationUpdater (게임 설정 변경)
```

#### Progressive Disclosure 시스템
```
TutorialManager
  ├─ LevelMilestones (레벨별 목표)
  ├─ MechanicUnlocker (기능 해금)
  ├─ TipGenerator (맞춤형 팁)
  └─ OnboardingController (신규 플레이어 가이드)
```

### UI/UX 명세

#### NPC 상호작용 UI
- 대화 박스 (우측 하단)
- NPC 감정 표현 (얼굴 아이콘)
- 선택지 버튼 (대화 옵션)
- 상호작용 프롬프트 (E 키)

#### 난이도 표시
- 현재 난이도 배지 (상단 중앙)
- 난이도 히스토리 (세션 내 변화)
- DDA 활성화 토글

#### 튜토리얼 UI
- 하이라이트 오버레이 (현재 목표 강조)
- 팝업 팁 (우상단)
- 체크리스트 (완료된 메카닉)
- 다음 목표 표시

### 데이터 구조

#### NPC 객체
```javascript
{
  id: "companion-drone-01",
  name: "Drift",
  personality: {
    friendliness: 0.8,
    helpfulness: 0.9,
    humor: 0.6
  },
  state: "FOLLOW",
  memory: {
    playerInteractions: [],
    learnedPatterns: {},
    preferences: {}
  },
  stats: {
    health: 100,
    energy: 75,
    skillLevel: 5
  }
}
```

#### DDA 메트릭
```javascript
{
  sessionId: "session-12345",
  clearTime: 450,
  attemptCount: 3,
  failureRate: 0.33,
  playerSkillScore: 7.2,
  recommendedDifficulty: "HARD",
  adjustmentHistory: []
}
```

#### 튜토리얼 체크포인트
```javascript
{
  level: 1,
  mechanics: [
    { name: "movement", unlocked: true },
    { name: "interaction", unlocked: false },
    { name: "combat", unlocked: false }
  ],
  completedTips: ["tip-001", "tip-003"],
  nextObjective: "reach-npc-companion"
}
```

### 성능 및 확장성
- NPC AI 업데이트 주기: 100ms (비동기)
- DDA 분석 주기: 레벨 완료 시점
- 최대 5개 NPC 동시 제어 (성능 최적화)
- AI 계산 오버헤드: 게임 프레임 레이트의 <10%

### 호환성
- 모던 브라우저 (Chrome 70+, Firefox 65+, Safari 12+)
- 모바일 최적화 (iOS 12+, Android 8+)
