## game-proposals 기능 명세서

### 개요
20개 게임 기획 제안서 모음입니다. 각 제안서는 독립적이고 완전한 게임 디자인 문서로, 구현을 위한 기술 스택, 시스템 설계, 수익화 전략을 포함합니다.

### 프로젝트 구조
```
game-proposals/
├─ 001-block-bounce.md
├─ 002-color-sort-puzzle.md
├─ 003-merge-rush.md
├─ 004-stack-tower.md
├─ 005-brick-breaker-blast.md
├─ 006-hex-drop-puzzle.md
├─ 007-gravity-orbit.md
├─ 008-pipe-connect-puzzle.md
├─ 009-idle-slime-merge.md
├─ 010-rhythm-pulse.md
├─ 011-fruit-merge-drop.md
├─ 012-crystal-match-quest.md
├─ 013-screw-sort-factory.md
├─ 014-laser-reflect-puzzle.md
├─ 015-number-drop-puzzle.md
├─ 016-rope-untangle.md
├─ 017-slide-block-match.md
├─ 018-chain-pop-puzzle.md
├─ 019-ball-sort-puzzle.md
└─ 020-match-3d-zen.md
```

### 핵심 기능

#### 1. 표준화된 제안서 구조
모든 제안서는 다음 섹션 포함:
- 게임 컨셉 및 핵심 메카닉
- 타겟 유저 분석
- 차별화 포인트
- 기술 스택
- 시스템 설계 및 아키텍처
- UI/UX 명세
- 게임플레이 루프
- 수익화 모델
- 개발 로드맵

#### 2. 게임 분류 (멀티장르)
- **Puzzle** (12개): Block Bounce, Color Sort, Hex Drop, Pipe Connect, Laser Reflect, Number Drop, Rope Untangle, Slide Block, Chain Pop, Ball Sort, Match 3D, Word-based
- **Arcade** (4개): Stack Tower, Brick Breaker, Gravity Orbit, Stellar elements
- **Idle** (2개): Idle Slime Merge, Pixel Factory type
- **Rhythm** (1개): Rhythm Pulse
- **Simulation** (1개): Screw Sort Factory

#### 3. 기술 스택 (공통)
- **프론트엔드**: HTML5 Canvas / WebGL, Vanilla JavaScript (ES6+)
- **백엔드**: Node.js / Python (선택적)
- **저장소**: localStorage / Firebase
- **분석**: Firebase Analytics / Mixpanel
- **광고**: AdMob / Facebook Ads
- **IAP**: Stripe / Apple App Store / Google Play

#### 4. 수익화 모델 (표준화)
- **배너 광고**: 게임 하단 배너 ($0.5-1.0 CPM)
- **리워드 광고**: 힌트/보너스 획득 시 ($2-4 eCPM)
- **인앱 구매**:
  - 광고 제거: $4.99/월
  - 힌트 팩: $0.99 (5개), $4.99 (30개)
  - 부스트 아이템: $0.99-$9.99
  - 코스메틱: $0.99-$2.99

### 시스템 아키텍처 (공통)

#### 게임 런타임
```
index.html
  ├─ Canvas/WebGL context
  ├─ UI Layer (HTML/CSS)
  └─ game.js (Core Engine)
      ├─ GameState
      ├─ Physics/Logic
      ├─ InputManager
      ├─ RenderEngine
      ├─ AudioManager
      ├─ SaveManager (localStorage)
      └─ AnalyticsManager
```

#### 백엔드 (선택적)
```
Backend API (Node.js/Python)
  ├─ Player Authentication
  ├─ Leaderboard Service
  ├─ Cloud Saves
  ├─ In-App Purchase Verification
  ├─ Analytics Aggregation
  └─ Push Notifications
```

### UI/UX 기본 구조

#### 메인 메뉴
- 게임 시작 버튼
- 계속하기 (저장된 진행)
- 설정 (음량, 난이도)
- 크레딧

#### 게임플레이 화면
- 점수/진행 표시기
- 일시정지 버튼
- 게임 오버/성공 모달

#### 설정 화면
- 음량 조절
- 난이도 선택
- 광고 설정
- 계정 연동

### 데이터 구조 (공통)

#### 플레이어 프로필
```javascript
{
  playerId: "uuid",
  nickname: "Player123",
  level: 15,
  totalScore: 125000,
  currency: {
    coins: 5000,
    gems: 50
  },
  achievements: ["first-win", "level-10"],
  lastLogin: "2026-04-21T10:30:00Z",
  playtime: 3600
}
```

#### 게임 세션 상태
```javascript
{
  gameId: "block-bounce",
  sessionId: "session-12345",
  currentLevel: 5,
  score: 12500,
  moves: 42,
  startTime: 1234567890,
  lastSaveTime: 1234567950,
  achievements: ["no-moves-wasted"],
  ads: {
    watched: 3,
    rewarded: 1
  }
}
```

### 성능 목표
- 로드 시간: <3초
- 프레임 레이트: 60 FPS (모바일 30 FPS)
- 메모리: <50MB
- 배터리 드레인: <5%/시간

### 호환성
- 브라우저: 모든 모던 브라우저 (Chrome 70+, Firefox 65+, Safari 12+)
- 모바일: iOS 12+, Android 8+
- 네트워크: 온/오프라인 모두 지원 (싱크 시 온라인)

### 마케팅 전략
- 앱 스토어 최적화 (ASO): 키워드 리서치 기반
- 사용자 획득 (UA): 페이스북/Google Ads 캠페인
- 리텐션: 푸시 알림, 일일 로그인 보상
- 수익화: IAP 및 광고 혼합 모델
