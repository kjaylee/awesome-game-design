## game-v6 기능 명세서

### 개요
Python 기반 HTML5 Canvas + Vanilla JavaScript 게임 생성기 v6입니다. 자동으로 10개의 멀티장르 게임을 생성하며, FPS 모니터링, 멀티터치 지원, 표준화된 저장/로드 기능을 포함합니다.

### 기술 스택
- **백엔드**: Python 3.x (gen_v6.py)
- **프론트엔드**: HTML5 Canvas, Vanilla JavaScript (ES6+)
- **저장소**: Browser localStorage, JSON export/import
- **입력**: 키보드, 마우스, 멀티터치 (Touch Events API)
- **출력**: `/workspace/games/` 에 게임별 폴더 생성

### 핵심 기능

#### 1. FPS 모니터링 오버레이
- 실시간 FPS 카운터 렌더링
- 프레임 타이밍 추적
- 성능 최적화 인사이트 제공

#### 2. 멀티터치 & 비주얼 피드백
- 터치 이벤트 감지 및 처리
- 터치 포인트 시각화
- 클릭/터치 피드백 애니메이션

#### 3. 저장/로드 시스템 (표준화)
- localStorage 기반 자동 저장
- 게임 상태 JSON 시리얼화
- 파일 export/import 기능
- 여러 세이브 슬롯 지원

#### 4. 멀티장르 게임 생성
- Puzzle: Echo Navigator, Mirror Maze
- Strategy: Root Network
- Arcade: Kite Messenger, Thermal Drift
- 추가 5개 게임

### 시스템 아키텍처

#### 생성 파이프라인
```
gen_v6.py
  ├─ 게임 템플릿 로드
  ├─ 게임별 설정 (메카닉, 난이도)
  ├─ HTML/CSS/JS 생성
  ├─ 자산(이미지, 사운드) 복사
  └─ /workspace/games/[game-name]/ 배포
```

#### 게임 런타임 구조
```
index.html
  ├─ Canvas element
  ├─ UI 오버레이 (FPS, 메뉴)
  └─ game.js
      ├─ GameEngine (메인 루프)
      ├─ InputManager (키보드/터치)
      ├─ RenderManager (Canvas 렌더링)
      ├─ SaveManager (localStorage)
      └─ GameState (게임 상태)
```

### UI/UX 명세

#### 메인 메뉴
- 게임 시작 버튼
- 계속하기 (저장된 진행 상황)
- 설정 (음량, 난이도)
- 크레딧

#### 게임 인 게임 UI
- FPS 모니터 (우상단)
- 점수/진행 표시기
- 일시정지 버튼
- 터치/클릭 피드백 시각화

#### 저장/로드 UI
- 저장 슬롯 표시
- 게임 스크린샷 미리보기
- 플레이 시간 표시
- export/import 버튼

### 데이터 구조

#### GameState 객체
```javascript
{
  gameId: "echo-navigator",
  version: "1.0.0",
  timestamp: 1234567890,
  progress: {
    level: 5,
    score: 12500,
    bestScore: 25000,
    completedLevels: [1,2,3,4,5]
  },
  settings: {
    volume: 0.8,
    difficulty: "medium",
    language: "ko"
  },
  playerStats: {
    totalPlayTime: 3600,
    sessionsPlayed: 25,
    achievements: ["first-clear", "speed-run"]
  }
}
```

#### SaveFile 구조
```javascript
{
  meta: {
    gameId: string,
    version: string,
    saveDate: ISO8601,
    thumbnail: base64_image
  },
  state: GameState
}
```

### 성능 최적화
- Canvas 렌더링 최적화 (requestAnimationFrame)
- 이미지 스프라이트 시트 사용
- 음성 큐 관리
- 메모리 누수 방지 (이벤트 리스너 정리)

### 호환성
- 모던 브라우저 (Chrome, Firefox, Safari, Edge)
- iOS/Android 모바일 브라우저
- 데스크톱 터치 디바이스 지원
