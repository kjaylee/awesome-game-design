## game-v10 기능 명세서

### 개요
Python 기반 HTML5 Canvas + Vanilla JavaScript 게임 생성기 v10입니다. 크로스 플랫폼 입력 지원, 반응형 디자인, 완전한 접근성(A11y) 기능을 통합하여 10개의 포괄적인 게임을 생성합니다.

### 기술 스택
- **백엔드**: Python 3.x (gen_v10.py)
- **프론트엔드**: HTML5 Canvas, Vanilla JavaScript (ES6+)
- **입력 처리**: Keyboard API, Touch Events API, Gamepad API
- **반응형 설계**: CSS Container Queries, clamp() 함수
- **접근성**: ARIA Live Regions, Screen Reader 지원, 고대비 모드, 포커스 표시

### 핵심 기능

#### 1. Cross-Platform 입력 (Keyboard + Touch + Gamepad)
- **키보드**: 방향키, WASD, 엔터, 스페이스
- **터치**: 멀티터치 제스처, 스와이프, 탭, 롱프레스
- **게임패드**: Xbox/PlayStation 컨트롤러 지원
- **입력 통합**: 동일 게임에서 세 가지 입력 방식 동시 지원

#### 2. 반응형 디자인 (Responsive Design)
- **CSS Container Queries**: 부모 컨테이너 크기 기반 스타일링
- **유동형 레이아웃**: clamp()로 조정 가능한 폰트/공간
- **화면 크기 최적화**: 모바일(320px) ~ 데스크톱(1920px) 대응
- **DPI 인식**: 고해상도 디스플레이 지원

#### 3. 완전한 접근성 (A11y)
- **ARIA Live Regions**: 게임 상태 변화 실시간 알림
- **스크린 리더 지원**: 완전한 내레이션 및 탐색
- **고대비 모드**: WCAG AAA 표준 준수
- **포커스 표시**: 명확한 포커스 인디케이터
- **움직임 감소**: prefers-reduced-motion 미디어 쿼리 지원
- **키보드 네비게이션**: 마우스 없이 전체 게임 플레이

#### 4. 멀티장르 게임 생성
- Puzzle: Gridlock Puzzle, Word Cascade
- Arcade: Stellar Breach
- Strategy: Mirror Match
- Idle: Pixel Factory
- 추가 5개 게임

### 시스템 아키텍처

#### 입력 통합 레이어
```
InputManager
  ├─ KeyboardHandler
  ├─ TouchHandler
  ├─ GamepadHandler (Gamepad API)
  └─ UnifiedInputBus (모든 입력 정규화)
```

#### 반응형 렌더링 엔진
```
ResponsiveRenderer
  ├─ ViewportManager (화면 크기 추적)
  ├─ LayoutCalculator (동적 레이아웃)
  ├─ DPIScaler (고해상도 지원)
  └─ CanvasResizer (Canvas 해상도 조정)
```

#### 접근성 시스템
```
AccessibilityEngine
  ├─ ARIAManager (Live Regions, 레이블)
  ├─ ScreenReaderBridge (내레이션)
  ├─ ContrastDetector (고대비 모드)
  ├─ FocusManager (포커스 추적)
  └─ MotionDetector (prefers-reduced-motion)
```

### UI/UX 명세

#### 입력 표시
- 현재 활성 입력 방식 표시 (키보드/터치/게임패드)
- 입력 방식 변경 시 프롬프트
- 컨트롤 설정 페이지 (리매핑 지원)

#### 반응형 UI
- 모바일: 세로/가로 모드 자동 전환
- 태블릿: 터치 최적화 버튼 (큰 터치 영역)
- 데스크톱: 정밀한 마우스 및 게임패드 컨트롤

#### 접근성 UI
- 고대비 모드 토글
- 애니메이션 감소 옵션
- 폰트 크기 조정
- 음성 안내 활성화/비활성화

### 데이터 구조

#### 입력 이벤트 (정규화)
```javascript
{
  type: "move",
  direction: "up",
  magnitude: 1.0,
  source: "keyboard|touch|gamepad",
  timestamp: 1234567890,
  metadata: {
    key: "ArrowUp",
    touchId: 0,
    gamepadIndex: 0
  }
}
```

#### 반응형 브레이크포인트
```javascript
{
  mobile: { min: 320, max: 767 },
  tablet: { min: 768, max: 1024 },
  desktop: { min: 1025, max: Infinity }
}
```

#### 접근성 설정
```javascript
{
  contrastMode: "normal|high",
  reduceMotion: false,
  fontSize: 16,
  voiceGuide: true,
  screenReaderMode: true,
  focusIndicatorSize: "normal|large"
}
```

### 성능 최적화
- 터치 지연 제거 (touch-action CSS)
- 게임패드 폴링 최적화 (requestAnimationFrame 연동)
- 반응형 레이아웃 재계산 최소화
- 접근성 기능 성능 영향 <5%

### 호환성
- 브라우저: Chrome, Firefox, Safari, Edge (모던 버전)
- 모바일: iOS 13+, Android 8+
- 게임패드: Xbox, PlayStation, Nintendo Pro
- 보조기술: NVDA, JAWS, VoiceOver, TalkBack
