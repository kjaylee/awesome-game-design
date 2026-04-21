## Derby Dash 프로토타입 - 기능 명세서

## 개요

Derby Dash 프로토타입은 순수 HTML5 Canvas 기반의 단일 파일 경마 게임입니다. 9마리의 경주마가 참여하는 실시간 레이스 시뮬레이션과 파리뮤추얼 배팅 시스템을 제공합니다. 절차적 사운드와 픽셀아트 그래픽으로 풍부한 게임 경험을 구현합니다.

## 핵심 기능

### 1. 경주마 시스템
- **9마리 경주마**: Thunderbolt, Midnight Swift, Silver Storm, Goldenhoof, Emerald Dream, Coal Shadow, Ruby Flash, Blaze, Brightstar
- 각 말의 고유 능력치 (속도, 지구력, 가속력)
- 절차적 다리 애니메이션
- 동적 움직임 및 상태 관리

### 2. 실시간 경주 엔진
- 레이스 시뮬레이션 (거리: 트랙 길이)
- 말의 동적 상태 변화
- 충돌 감지 및 처리
- 승자 판정 및 기록

### 3. 파리뮤추얼 배팅 시스템
- 총 배당금을 승자가 분배받음 (하우스 30% 컷)
- 실시간 배당률 변동
- 베팅 풀에 따른 동적 배당률 계산
- 투명한 수수료 구조

### 4. HUD (헤드 업 디스플레이)
- 과거 승률 차트 (각 말별)
- 현재 뱅크롤 표시
- 베팅 상태 표시
- 실시간 경주 정보

### 5. 뱅크롤 관리
- 초기 자본 할당
- 베팅 후 잔액 계산
- $0일 시 자동 리셋 (재시작)
- 수익/손실 추적

### 6. 절차적 사운드 (Web Audio API)
- 출발 신호음
- 갤럽 리듬 (발굽 소리)
- 승리 팡파르
- 패배 음향 효과
- 배팅 확인음

### 7. 비주얼 시스템
- 픽셀아트 말 스프라이트
- 절차적 다리 애니메이션
- 먼지 파티클 이펙트
- 트랙 및 배경 그래픽

## 시스템 아키텍처

### 렌더링 파이프라인
```
Canvas Context
    ↓
배경 렌더 (트랙, 거리 마커)
    ↓
말 렌더 (위치, 각도, 다리 애니메이션)
    ↓
파티클 렌더 (먼지, 이펙트)
    ↓
HUD 렌더 (차트, 정보)
    ↓
화면 출력
```

### 게임 루프 구조
```
초기화 (Initialize)
    ↓
메뉴 상태 (Menu State)
    ↓
베팅 상태 (Betting State)
    ↓
경주 진행 (Racing State)
    ↓
결과 표시 (Result State)
    ↓
반복 또는 종료
```

### 주요 모듈
- **Horse Module**: 말 데이터 및 물리 시뮬레이션
- **Race Engine**: 경주 로직 및 진행 상황 관리
- **Betting System**: 배팅 계산 및 배당률 관리
- **Audio System**: Web Audio API 기반 사운드 생성
- **Particle System**: 파티클 이펙트 생성 및 렌더
- **UI System**: HUD 및 차트 렌더링

## UI/UX 명세

### 게임 화면 구성
```
┌────────────────────────────────────────┐
│        Derby Dash - 경주 화면          │
├────────────────────────────────────────┤
│                                        │
│  트랙 (말들의 경주 공간)               │
│                                        │
│  [말1] [말2] [말3] ... [말9]          │
│                                        │
├────────────────────────────────────────┤
│  뱅크롤: $1,000  |  승률 차트         │
└────────────────────────────────────────┘
```

### 베팅 UI
- 칩 버튼: $10, $25, $50, $100, $250, $500
- 클릭으로 베팅액 누적
- 총 베팅액 표시
- 배당률 실시간 계산 표시

### 경주 중 정보
- 각 말의 현재 위치
- 진행 상황 바
- 실시간 배당률
- 예상 수익 계산

### 결과 화면
- 우승마 강조 표시
- 배당금 계산 결과
- 최종 뱅크롤
- 다음 경주 버튼

## 데이터 구조

### 말(Horse) 구조
```typescript
{
  name: string
  speed: number          // 기본 속도
  endurance: number      // 지구력
  acceleration: number   // 가속력
  position: number       // 현재 위치
  velocity: number       // 현재 속도
  winRate: number        // 역사적 승률
  wins: number           // 총 승리 수
  races: number          // 참여 레이스 수
  isActive: boolean      // 현재 레이스 참여 여부
}
```

### 베팅 데이터
```typescript
{
  horseName: string
  amount: number         // 베팅액
  odds: number          // 배당률
  payout: number        // 가능한 배당금
}
```

### 레이스 결과
```typescript
{
  winner: Horse
  positions: Horse[]    // 순위 순서
  totalPool: number     // 총 베팅액
  oddsAtWin: number     // 우승 시 배당률
  payout: number        // 최종 배당금
  houseCommission: number // 하우스 수수료
}
```

## 성능 고려사항

- Canvas 최적화 (60 FPS 유지)
- 음향 합성 효율성 (CPU 부하 최소화)
- 파티클 풀링 (메모리 효율)
- 프레임 스킵 처리 (저사양 기기 대응)

## 브라우저 호환성

- Chrome/Edge: 전체 지원
- Firefox: 전체 지원
- Safari: Web Audio API 지원 필수
- 모바일 브라우저: Canvas 지원 필수

## 파일 구조

- 단일 HTML 파일 (game.html)
- 내장 CSS (스타일링)
- 내장 JavaScript (모든 로직 포함)
- 외부 라이브러리 없음 (순수 Canvas API 사용)
