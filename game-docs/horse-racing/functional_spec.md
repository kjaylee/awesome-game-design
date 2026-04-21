## Derby Dash 데이터 분석 및 자동화 플랫폼 - 기능 명세서

## 개요

Derby Dash 데이터 분석 및 자동화 플랫폼은 TypeScript 기반의 게임 운영 시스템이자 리서치 파이프라인입니다. 경마 게임의 데이터를 수집, 분석, 시각화하며, 자동 수집 및 정보지 초안 생성 기능을 제공합니다. GitHub Pages를 통해 배포되는 웹 기반 플랫폼입니다.

## 핵심 기능

### 1. 검색 인덱스 관리
- 경마 레이스 데이터에 대한 검색 인덱스 생성 및 유지보수
- `npm run index` 명령으로 인덱스 초기화/갱신
- 빠른 데이터 검색 및 필터링 지원

### 2. 데이터 분석
- `npm run analyze` 명령을 통한 통계 분석 수행
- 말의 성적, 승률, 트렌드 분석
- 레이스 히스토리 분석 및 패턴 인식

### 3. 자동 검색
- `npm run search` 명령으로 특정 조건의 레이스 자동 검색
- 데이터베이스에서 원하는 조건의 말/레이스 찾기
- 필터링 및 정렬 기능

### 4. 자동 수집
- `npm run research` 명령을 통한 자동 데이터 수집
- 외부 소스에서 경마 정보 크롤링
- 데이터 정제 및 저장

### 5. 통합 자동화
- `npm run full-auto` 명령으로 모든 프로세스 순차 실행
- 인덱싱 → 수집 → 분석 → 초안 생성 자동화
- 운영 효율성 극대화

### 6. 정보지 초안 생성
- 수집된 데이터 기반 자동 보고서 생성
- 마크다운 형식의 분석 결과 문서화
- 게시 준비 상태의 콘텐츠 산출

## 시스템 아키텍처

### 계층 구조
```
┌─────────────────────────────────────┐
│     GitHub Pages 배포 (프론트엔드)    │
├─────────────────────────────────────┤
│         TypeScript 코드베이스         │
├─────────────────────────────────────┤
│   CLI 명령어 인터페이스 (npm scripts) │
├─────────────────────────────────────┤
│   데이터 처리 및 분석 엔진            │
├─────────────────────────────────────┤
│  검색 인덱스 / 수집 / 저장소         │
└─────────────────────────────────────┘
```

### 주요 모듈
- **Indexing Module**: 검색 인덱스 생성 및 관리
- **Analysis Module**: 통계 및 데이터 분석
- **Search Module**: 쿼리 기반 검색 기능
- **Research Module**: 자동 데이터 수집 및 크롤링
- **Report Generator**: 정보지 초안 자동 생성

## UI/UX 명세

### 배포 인터페이스
- GitHub Pages 정적 사이트 호스팅
- 브라우저 기반 대시보드 (선택사항)
- 분석 결과 시각화 (차트, 표)

### 상호작용 방식
- 명령어 라인 인터페이스 (CLI) 기반
- npm scripts를 통한 작업 트리거
- 실시간 진행 상황 피드백

## 데이터 구조

### 레이스 데이터
```
{
  raceId: string
  date: Date
  horses: Horse[]
  results: RaceResult[]
  metadata: {
    track: string
    distance: number
    conditions: string
  }
}
```

### 말(Horse) 데이터
```
{
  horseName: string
  age: number
  recordWins: number
  recordRaces: number
  recentFormTrend: number[]
  stats: {
    avgSpeed: number
    winRate: number
    placeRate: number
  }
}
```

### 분석 결과
```
{
  analysisDate: Date
  statisticalSummary: {
    topPerformers: Horse[]
    trends: Trend[]
    predictions: Prediction[]
  }
  reportContent: string
}
```

## 배포 및 구성

### 배포 프로세스
- `npm run production` 명령으로 GitHub Pages 배포
- 정적 사이트 생성 및 호스팅
- 자동 빌드 및 배포

### 의존성
- TypeScript: 타입 안전성
- 데이터 처리 라이브러리
- 마크다운 생성 도구

## 성능 고려사항

- 대규모 데이터셋 처리 최적화
- 검색 인덱스 성능
- 자동 수집 스로틀링
- 정적 사이트 생성 속도
