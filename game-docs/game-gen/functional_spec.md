## Derby Dash 확장 기획 (Phase 6~7) - 기능 명세서

## 개요

Derby Dash 확장 기획 문서는 게임의 Phase 6~7에서 추가될 주요 기능과 콘텐츠를 상세히 설명합니다. Phase 6에서는 새로운 경주마를 추가하고, Phase 7에서는 새로운 트랙과 고급 통계 시스템을 도입합니다.

## Phase 6: 말 추가 확장

### 신규 경주마: Phantom Runner 👻

**타입**: 은신형 마무리꾼

**능력 분포**:
- 기본 속도: 중간 (6/10)
- 지구력: 높음 (9/10)
- 가속력: 매우 높음 (9/10)
- 후반 가속 부스트: 고유 능력

**게임플레이 특성**:
- 레이스 초반: 평범한 성능 (중간 순위 유지)
- 레이스 중반: 점진적 속도 증가
- 레이스 후반 (마지막 25%): 급속한 속도 향상으로 역전 승리 가능
- 높은 배당률: 확률 낮음 (약 8~15%)

**시각 표현**:
- 픽셀아트 유령 테마 말
- 후반부에 빛나는 이펙트
- 속도 증가 시 흐릿한 잔상 (motion blur)

**음향 효과**:
- 유령 같은 신비로운 울음소리
- 후반 가속 시 특수 음향 신호
- 승리 시 신비한 팡파르

### 전체 말 구성

1. Thunderbolt (번개 속성): 빠른 출발
2. Midnight Swift (밤 속성): 야간 경기 강함
3. Silver Storm (폭풍 속성): 날씨 영향 적음
4. Goldenhoof (황금 속성): 기본 배팅 인기
5. Emerald Dream (에메랄드 속성): 중간 속도
6. Coal Shadow (검은색 속성): 어두운 환경 강함
7. Ruby Flash (루비 속성): 짧은 거리 강함
8. Blaze (불 속성): 뜨거운 환경 강함
9. Brightstar (별 속성): 밝은 환경 강함
10. Phantom Runner 👻 (유령 속성): 후반 가속 특화 **[NEW]**

## Phase 7: 트랙 및 통계 시스템 확장

### 새로운 트랙 환경

#### 1. Classic Track (클래식 트랙)
- 기본 설정, 변수 없음
- 길이: 1,000m
- 지면: 표준 흙

#### 2. Mountain Trail (산악 트랙)
- 고도 변화 (오르막/내림막)
- 길이: 1,200m
- 영향: 지구력 중요도 증가
- 특성: 은신형 말 유리

#### 3. Desert Stretch (사막 트랙)
- 모래 지면, 마찰 증가
- 길이: 1,500m
- 영향: 기본 속도 감소
- 특성: 인내력 높은 말 유리

#### 4. Forest Path (숲 속 트랙)
- 나뭇가지 장애물
- 길이: 950m
- 영향: 민첩성 테스트
- 특성: 빠른 말 유리

#### 5. Night Circuit (야간 서킷)
- 야간 환경
- 길이: 1,100m
- 영향: 특정 말에 보너스 적용
- 특성: Midnight Swift 유리

#### 6. Storm Track (폭풍 트랙)
- 악천후 조건
- 길이: 1,050m
- 영향: 날씨 내성 필요
- 특성: Silver Storm 유리

### 레이스 히스토리 시스템

#### 기능:
- 모든 경주 결과 자동 저장
- 말별 통계 추적
- 스타일 선택형 필터링
- 날짜 범위 검색

#### 데이터 항목:
```
{
  raceId: string
  timestamp: Date
  trackType: string
  weather: string
  winner: Horse
  positions: Horse[]
  totalPool: number
  odds: number
  payouts: Map<Horse, number>
}
```

#### 시각화:
- 시간대별 승률 그래프
- 말별 성적 비교 표
- 트랙별 성능 분석
- 배팅액 vs 이익률 산점도

### 레이스 팁 시스템

#### 분석 기반 팁:
- 과거 3경주: 승률이 높은 말 강조
- 현재 배팅 풀: 배당률 분석 제시
- 특정 말의 형태: 최근 3경주 추세

#### 팁 유형:

**약자 추천**: 배당률 높은 말의 숨은 강점 분석

**인기마 회피**: 과도한 배팅이 수익을 압박할 때 경고

**조합 추천**: 2개 말 동시 베팅 (Double) 제안

**트랙 분석**: 현재 트랙에서 강한 말 강조

### 통계 시스템

#### 개인 기록 (Player Stats):
```
{
  totalWagers: number        // 누적 베팅액
  totalPayouts: number       // 누적 수익
  netProfit: number          // 순이익
  winRate: number            // 전체 승률
  roi: number                // 투자 수익률 (%)
  favoriteHorse: Horse       // 가장 자주 베팅한 말
  luckyTrack: string         // 가장 많이 이기는 트랙
  longestWinStreak: number   // 최대 연승
  largestPayout: number      // 최대 배당금
}
```

#### 말 기록 (Horse Stats):
```
{
  horseName: string
  totalRaces: number
  wins: number
  places: number             // 2위
  shows: number              // 3위
  winRate: number
  avgSpeed: number
  avgPayout: number
  favoriteTrack: string      // 최고 성적 트랙
  preference: {
    weatherPreference: string
    distancePreference: string
    trackTypePreference: string
  }
}
```

## 스프라이트 에셋 구조

### 경로: `sprites/derby-dash/`

```
sprites/derby-dash/
├── horses/
│   ├── thunderbolt.png
│   ├── midnight-swift.png
│   ├── silver-storm.png
│   ├── goldenhoof.png
│   ├── emerald-dream.png
│   ├── coal-shadow.png
│   ├── ruby-flash.png
│   ├── blaze.png
│   ├── brightstar.png
│   └── phantom-runner.png (NEW)
├── tracks/
│   ├── classic-track.png
│   ├── mountain-trail.png
│   ├── desert-stretch.png
│   ├── forest-path.png
│   ├── night-circuit.png
│   └── storm-track.png
├── effects/
│   ├── dust-particle.png
│   ├── speed-burst.png
│   ├── phantom-glow.png (NEW)
│   └── weather-effects.png
└── ui/
    ├── stats-panel.png
    ├── tips-indicator.png
    └── history-chart.png
```

## 시스템 아키텍처 업그레이드

### Phase 6 추가 모듈
- **Horse Manager**: 10마리 말 관리
- **Special Ability System**: 고유 능력 처리 (Phantom Runner)

### Phase 7 추가 모듈
- **Track System**: 여러 트랙 선택 및 속성 적용
- **Stats Engine**: 통계 계산 및 저장
- **Tips Engine**: 분석 기반 조언 생성
- **History Manager**: 경주 히스토리 DB

## 성능 목표

- 히스토리 데이터: 최대 1,000경주 저장 (로컬 스토리지)
- 통계 계산: 100ms 이내
- 팁 생성: 50ms 이내
- 그래프 렌더: 60 FPS 유지
