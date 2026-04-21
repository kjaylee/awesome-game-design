# Gravity Flip - 기능 명세서 (Functional Specification)

## 1. 게임 개요

### 1.1 프로젝트 정보
- **게임명**: Gravity Flip
- **프로젝트 코드**: game-flip-gravity
- **장르**: One-button Survival Runner / Arcade
- **플랫폼**: Web (HTML5 Canvas)
- **대상 플레이어**: 캐주얼 게이머, 무료 모바일 게임 사용자
- **ASO 슬로건**: "Gravity Flip — One Tap Survival"

### 1.2 기술 스택
- **구현**: 단일 HTML5 Canvas + Vanilla JavaScript
- **렌더링**: 2D Canvas API
- **데이터 저장**: localStorage (로컬 데이터 퍼시스턴스)
- **의존성**: 없음 (Zero Dependencies)
- **파일 크기**: 단일 .html 파일

### 1.3 핵심 게임플레이
- **입력 메커니즘**: 탭(모바일) / 스페이스바(PC)
- **핵심 액션**: 한 번의 입력 = 중력 180° 반전
- **핵심 루프**: 벽 회피 → 탭으로 중력 반전 → 충돌 또는 통과 → 점수 증가 → 난이도 상승 → 재시작
- **목표**: 최대한 많은 벽을 통과하여 높은 점수 달성

---

## 2. 핵심 시스템 명세

### 2.1 중력 반전 시스템

#### 작동 원리
- 플레이어는 게임 영역 상단 또는 하단에 위치한 정사각형 캐릭터 객체
- 초기 상태: 캐릭터가 화면 하단에 위치, 중력은 아래쪽(양의 Y축)
- 입력 시: 중력 벡터 = 중력 벡터 × -1 (180도 반전)
- 결과: 캐릭터는 반대 방향으로 가속

#### 물리 파라미터
- **초기 중력 값**: 0.6 px/frame²
- **최대 낙하 속도**: 7 px/frame (상향으로도 동일)
- **변속 계수**: 1.0 (일정한 가속도)

#### 상태 전이
```
상태A(하단): 탭 → 상태B(상승)
상태B(상단): 탭 → 상태A(하강)
```

### 2.2 벽 생성 및 이동 시스템

#### 벽의 특성
- **형태**: 수평 직선, 정사각형 간격이 있는 통로
- **벽 너비**: 24px (고정)
- **화면 높이**: 800px
- **생성 위치**: 화면 우측 끝(x = 800px)에서 좌측으로 이동
- **목표 위치**: 화면 좌측 끝을 넘어 사라짐

#### 난이도별 벽 설정
| 점수 범위 | 벽 속도 | 간격 높이 | 생성 간격 | 비고 |
|----------|--------|---------|---------|------|
| 0~10     | 220px/s | 180px  | 1.4초   | 초급 단계 |
| 10~30    | 270px/s | 줄어듦   | 1.2초   | 중급 단계 |
| 30~50    | 370px/s | 줄어듦   | 0.9초   | 상급 단계 |
| 50+      | 440px/s | 100px(최소) | 0.6초   | 극난이도 |

#### 벽 생성 로직
```javascript
- 매 프레임: 생성 간격 타이머 감소
- 타이머 <= 0: 새 벽 객체 생성
- 벽 생성 위치: {x: 800, y: 0}
- 현재 점수에 따라 매개변수 업데이트
- 타이머 리셋: 다음 벽까지의 시간 설정
```

### 2.3 충돌 감지 시스템

#### 충돌 판정
- **판정 대상**: 플레이어 바운딩 박스 vs 벽 바운딩 박스
- **충돌 조건**:
  - 플레이어 좌측 < 벽 우측 AND
  - 플레이어 우측 > 벽 좌측 AND
  - 플레이어 상단 < 벽 하단(또는 우측) AND
  - 플레이어 하단 > 벽 상단(또는 좌측)

#### 안전 영역
- 간격(gap) 내에서는 충돌하지 않음
- 간격의 정중앙에 진입하면 안전

#### 게임 오버 조건
- 벽과의 충돌 감지 1회 = 즉시 게임 오버
- 플레이어는 사망 상태로 전이

### 2.4 점수 시스템

#### 점수 획득 조건
1. **벽 통과**: 벽을 안전하게 통과 → +1점
2. **골드 오브(Gold Orb) 수집**: 간격 중앙에 간헐적 생성 → +5점
   - 생성 확률: 35% (매 벽마다)
   - 위치: 간격의 정중앙
   - 수집: 플레이어와 충돌 시 자동 획득

#### 점수 누적
- 총점 = 벽 통과 수 + (골드 오브 수 × 5)
- 실시간 점수 표시: HUD의 점수 표시 영역

#### 최고점수 저장
- localStorage에 `maxScore` 키로 저장
- 게임 오버 시: 현재 점수 > 최고점수면 업데이트
- 시작 화면에서 최고점수 표시

### 2.5 난이도 곡선

#### 설계 철학
- 초반(0~10점): 플레이어 학습 단계 - 느슨한 난이도
- 중반(10~50점): 점진적 난이도 상승
- 후반(50+점): 극한의 난이도 - 반사 신경 극대화

#### 난이도 상승 메커니즘
```
점수 증가 → 각 파라미터 자동 계산
- 속도 = min(220 + (점수/10) * 30, 440)
- 간격 = max(180 - (점수/20) * 20, 100)
- 생성간격 = max(1.4 - (점수/50) * 0.8, 0.6)
```

---

## 3. UI/UX 명세

### 3.1 화면 구성

#### 게임 플레이 화면
- **배경**: 검은색(#000000) 또는 어두운 네온 배경
- **플레이어**: 네온 시안(#00FFFF) 정사각형, 크기 32x32px
- **벽**: 네온 퍼플(#FF00FF) 라인
- **간격**: 투명(배경색)
- **골드 오브**: 황색(#FFD700) 원형, 반지름 8px

#### 게임 오버 화면
- **반투명 오버레이**: 검은색 배경에 60% 투명도
- **게임오버 텍스트**: 대형 흰색 글자("GAME OVER")
- **점수 표시**: "SCORE: [점수]"
- **최고점수 표시**: "BEST: [최고점수]"
- **재시작 버튼**: 탭 또는 스페이스바로 자동 재시작

### 3.2 HUD (Head-Up Display)

#### 점수 표시
- **위치**: 화면 좌상단
- **폰트 크기**: 24px
- **색상**: 네온 시안(#00FFFF)
- **형식**: "SCORE: [현재점수]"

#### 최고점수 표시 (게임 플레이 중)
- **위치**: 화면 우상단
- **폰트 크기**: 18px
- **색상**: 네온 그린(#00FF00)
- **형식**: "BEST: [최고점수]"

#### FPS 표시 (개발용 - 필요시)
- **위치**: 화면 좌하단
- **폰트 크기**: 12px
- **색상**: 흰색
- **형식**: "FPS: [fps]"

### 3.3 게임오버 화면 상호작용

#### 자동 재시작
- **재시작 딜레이**: 0.7초
- **입력**: 탭(모바일) 또는 스페이스바(PC)로도 즉시 재시작 가능
- **상태 초기화**:
  - 점수 = 0
  - 벽 배열 = []
  - 플레이어 위치 = 초기 위치
  - 중력 = 초기값

---

## 4. 데이터 구조

### 4.1 GameObject 인터페이스

#### 플레이어 객체
```
Player {
  x: number,              // 플레이어 X 좌표
  y: number,              // 플레이어 Y 좌표
  width: number = 32,     // 플레이어 너비
  height: number = 32,    // 플레이어 높이
  velocityY: number,      // Y축 속도
  gravity: number,        // 중력 값 (양수: 하강)
  isAlive: boolean        // 생존 상태
}
```

#### 벽 객체
```
Wall {
  x: number,              // 벽 X 좌표
  y: number = 0,          // 벽 Y 좌표 (항상 0)
  width: number = 24,     // 벽 너비
  height: number = 800,   // 벽 높이 (전체 화면)
  gapY: number,           // 간격 상단 Y좌표
  gapHeight: number,      // 간격 높이
  hasOrb: boolean,        // 골드 오브 포함 여부
  vx: number              // X축 속도 (음수: 좌측 이동)
}
```

#### 골드 오브 객체
```
GoldOrb {
  x: number,              // 골드 오브 X 좌표
  y: number,              // 골드 오브 Y 좌표
  radius: number = 8,     // 반지름
  collected: boolean      // 수집 여부
}
```

#### 파티클 객체
```
Particle {
  x: number,              // 파티클 X 좌표
  y: number,              // 파티클 Y 좌표
  vx: number,             // X축 속도
  vy: number,             // Y축 속도
  lifetime: number,       // 남은 생명 시간 (ms)
  maxLifetime: number,    // 최대 생명 시간
  radius: number,         // 파티클 반지름
  color: string           // 파티클 색상
}
```

### 4.2 localStorage 스키마

#### 저장 데이터
```javascript
localStorage.maxScore   // 최고점수 (정수)
localStorage.totalGamesPlayed  // 총 게임 횟수 (정수)
localStorage.settings   // 게임 설정 (JSON 문자열)
```

#### 설정 객체 구조
```json
{
  "soundEnabled": true,
  "volumeLevel": 0.7,
  "particlesEnabled": true,
  "difficultyMultiplier": 1.0
}
```

#### 초기화 로직
```javascript
if (\!localStorage.maxScore) {
  localStorage.maxScore = 0;
  localStorage.totalGamesPlayed = 0;
  localStorage.settings = JSON.stringify({
    soundEnabled: true,
    volumeLevel: 0.7,
    particlesEnabled: true,
    difficultyMultiplier: 1.0
  });
}
```

---

## 5. 렌더링 파이프라인

### 5.1 프레임 렌더링 순서

#### 매 프레임 실행 순서
1. **게임 상태 업데이트**
   - 플레이어 물리 계산
   - 벽 이동 업데이트
   - 충돌 감지
   - 점수 계산
   - 파티클 애니메이션

2. **렌더링 (Canvas에 그리기)**
   - Canvas 초기화 (검은색 배경으로 채우기)
   - 벽 렌더링
   - 골드 오브 렌더링
   - 플레이어 렌더링
   - 파티클 렌더링
   - HUD 렌더링

3. **프레임 레이트 제어**
   - requestAnimationFrame 사용
   - 목표 FPS: 60 (약 16.67ms 간격)

### 5.2 렌더링 상세

#### 배경 렌더링
```javascript
ctx.fillStyle = '#000000';
ctx.fillRect(0, 0, canvas.width, canvas.height);
```

#### 벽 렌더링
```javascript
// 벽 본체 (퍼플)
ctx.fillStyle = '#FF00FF';
ctx.fillRect(wall.x, 0, wall.width, wall.gapY);
ctx.fillRect(wall.x, wall.gapY + wall.gapHeight, 
             wall.width, 800 - (wall.gapY + wall.gapHeight));

// 간격 강조선 (선택사항)
ctx.strokeStyle = '#00FF00';
ctx.lineWidth = 2;
ctx.strokeRect(wall.x - 2, wall.gapY - 2, 
               wall.width + 4, wall.gapHeight + 4);
```

#### 플레이어 렌더링
```javascript
ctx.fillStyle = '#00FFFF';
ctx.fillRect(player.x, player.y, player.width, player.height);

// 플레이어 테두리 (네온 효과)
ctx.strokeStyle = '#00FFFF';
ctx.lineWidth = 2;
ctx.strokeRect(player.x, player.y, player.width, player.height);
```

#### HUD 텍스트 렌더링
```javascript
ctx.fillStyle = '#00FFFF';
ctx.font = '24px Arial';
ctx.fillText(`SCORE: ${score}`, 20, 40);

ctx.fillStyle = '#00FF00';
ctx.font = '18px Arial';
ctx.fillText(`BEST: ${maxScore}`, canvas.width - 150, 40);
```

### 5.3 Canvas 설정

#### 초기화 코드
```javascript
const canvas = document.getElementById('gameCanvas');
const ctx = canvas.getContext('2d');
canvas.width = 800;
canvas.height = 800;

// 앤티앨리어싱 비활성화 (픽셀 아트 스타일)
ctx.imageSmoothingEnabled = false;
```

---

## 6. 파티클 시스템

### 6.1 파티클 이펙트 종류

#### 중력 반전 이펙트
- **발생 조건**: 플레이어가 탭 입력 시
- **개수**: 8개 파티클 생성
- **색상**: 네온 시안(#00FFFF)
- **생명 시간**: 500ms
- **방사형 확산**: 플레이어 중심에서 360도로 확산

#### 점수 획득 이펙트 (벽 통과)
- **발생 조건**: 벽을 안전하게 통과할 때
- **개수**: 3개 파티클
- **색상**: 네온 그린(#00FF00)
- **생명 시간**: 400ms
- **방향**: 상향 또는 하향 (플레이어 위치에 따라)

#### 골드 오브 수집 이펙트
- **발생 조건**: 골드 오브 수집 시
- **개수**: 10개 파티클
- **색상**: 황색(#FFD700)
- **생명 시간**: 600ms
- **방사형 확산**: 골드 오브 위치에서 360도 확산

#### 충돌/사망 이펙트
- **발생 조건**: 벽과 충돌하여 게임 오버 시
- **개수**: 15개 파티클
- **색상**: 레드(#FF0000)
- **생명 시간**: 700ms
- **방사형 확산**: 충돌 위치에서 360도 확산

### 6.2 파티클 물리

#### 파티클 갱신 로직
```javascript
// 매 프레임
particle.x += particle.vx;
particle.y += particle.vy;
particle.vy += 0.2;  // 중력 영향
particle.lifetime -= deltaTime;

// 투명도 감소 (페이드 아웃)
opacity = particle.lifetime / particle.maxLifetime;
```

#### 파티클 생성 함수
```javascript
function createParticles(x, y, count, color) {
  for (let i = 0; i < count; i++) {
    const angle = (i / count) * Math.PI * 2;
    const speed = 2 + Math.random() * 3;
    particles.push({
      x: x,
      y: y,
      vx: Math.cos(angle) * speed,
      vy: Math.sin(angle) * speed,
      lifetime: 500,
      maxLifetime: 500,
      radius: 3,
      color: color
    });
  }
}
```

### 6.3 파티클 렌더링
```javascript
particles.forEach(particle => {
  const opacity = particle.lifetime / particle.maxLifetime;
  ctx.fillStyle = `${particle.color}${Math.round(opacity * 255).toString(16)}`;
  ctx.beginPath();
  ctx.arc(particle.x, particle.y, particle.radius, 0, Math.PI * 2);
  ctx.fill();
});
```

---

## 7. 입력 시스템

### 7.1 입력 이벤트

#### 터치 입력 (모바일)
```javascript
document.addEventListener('touchstart', (e) => {
  e.preventDefault();
  handleInput();
});
```

#### 키보드 입력 (PC)
```javascript
document.addEventListener('keydown', (e) => {
  if (e.key === ' ' || e.code === 'Space') {
    e.preventDefault();
    handleInput();
  }
});
```

#### 입력 처리 함수
```javascript
function handleInput() {
  if (gameState === 'playing') {
    player.gravity *= -1;
    createParticles(player.x + 16, player.y + 16, 8, '#00FFFF');
  } else if (gameState === 'gameOver') {
    restartGame();
  }
}
```

---

## 8. 게임 상태 관리

### 8.1 게임 상태 머신

#### 상태 정의
- **MENU**: 게임 시작 화면
- **PLAYING**: 게임 진행 중
- **PAUSED**: 일시 정지 (선택사항)
- **GAME_OVER**: 게임 오버 상태

#### 상태 전이
```
MENU → PLAYING (게임 시작 입력)
PLAYING → GAME_OVER (충돌 감지)
GAME_OVER → PLAYING (0.7초 또는 입력)
```

### 8.2 게임 루프

#### 메인 루프 구조
```javascript
let gameState = 'menu';
let score = 0;
let maxScore = localStorage.maxScore || 0;
let gameOverTime = 0;

function gameLoop() {
  switch (gameState) {
    case 'menu':
      renderMenu();
      break;
    case 'playing':
      updateGame();
      renderGame();
      break;
    case 'gameOver':
      renderGameOver();
      if (Date.now() - gameOverTime > 700) {
        // 자동 재시작 준비
      }
      break;
  }
  requestAnimationFrame(gameLoop);
}
```

---

## 9. 성능 최적화

### 9.1 메모리 관리
- **벽 풀링**: 화면 밖의 벽은 배열에서 제거
- **파티클 풀링**: 생명 시간이 0인 파티클은 배열에서 제거
- **최대 벽 수 제한**: 동시에 5~10개의 벽만 유지

### 9.2 렌더링 최적화
- **Canvas 크기 고정**: 800x800px (스케일링 최소화)
- **imgSmoothingEnabled = false**: 픽셀 아트 스타일 유지
- **requestAnimationFrame 사용**: 브라우저 최적화 활용

### 9.3 계산 최적화
- **충돌 감지**: AABB (Axis-Aligned Bounding Box) 사용
- **벽 재사용**: 제거된 벽 객체 재활용

---

## 10. 배포 및 호스팅

### 10.1 빌드 결과물
- **단일 HTML 파일**: index.html
- **파일 크기**: ~50KB (미압축)
- **의존성**: 없음

### 10.2 호스팅 옵션
1. **정적 웹호스팅**: GitHub Pages, Netlify, Vercel
2. **모바일 래퍼**: Cordova, React Native Webview로 앱화
3. **스토어 배포**: Google Play Store, Apple App Store (래퍼 필요)

---

## 11. 테스트 체크리스트

### 11.1 기능 테스트
- [ ] 중력 반전이 정확히 작동하는가
- [ ] 벽이 일정 속도로 움직이는가
- [ ] 충돌 감지가 정확한가
- [ ] 점수가 올바르게 증가하는가
- [ ] 난이도가 점수에 따라 상승하는가
- [ ] 파티클이 올바른 시간에 생성되는가
- [ ] localStorage에 최고점수가 저장되는가

### 11.2 성능 테스트
- [ ] FPS가 60 이상 유지되는가 (모바일 포함)
- [ ] 메모리 누수가 없는가
- [ ] 장시간 플레이 시에도 안정적인가

### 11.3 UI/UX 테스트
- [ ] HUD가 올바르게 표시되는가
- [ ] 게임오버 화면이 명확한가
- [ ] 텍스트가 읽기 쉬운가
- [ ] 색상 대비가 충분한가

---

## 부록: 상수 및 설정값

```javascript
// 화면 설정
const CANVAS_WIDTH = 800;
const CANVAS_HEIGHT = 800;

// 플레이어 설정
const PLAYER_WIDTH = 32;
const PLAYER_HEIGHT = 32;
const PLAYER_START_X = 384;
const PLAYER_START_Y = 750;
const GRAVITY = 0.6;
const MAX_VELOCITY = 7;

// 벽 설정
const WALL_WIDTH = 24;
const BASE_WALL_SPEED = 220;
const BASE_GAP_HEIGHT = 180;
const BASE_SPAWN_INTERVAL = 1.4;

// 게임오버 설정
const GAME_OVER_DELAY = 700;

// 파티클 설정
const PARTICLE_LIFETIME = 500;
```
