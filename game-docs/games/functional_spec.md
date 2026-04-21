## games 기능 명세서

### 개요
games 폴더는 600개 이상의 게임이 배포되는 메인 게임 카탈로그입니다. 모든 게임이 games.eastsea.xyz에서 호스팅되며, 빌드 스크립트와 i18n 도구를 통해 자동으로 관리됩니다.

### 프로젝트 구조

```
games/
├─ [game-folders] × 600+
│  ├─ abyssal-archive-diver/
│  ├─ accordion-vault/
│  ├─ aether-farm-command/
│  ├─ alchemist-tower/
│  ├─ alchemy-merge-defense/
│  ├─ ant-colony-command/
│  ├─ ant-colony-tycoon/
│  ├─ arcade-lobby/
│  ├─ arcane-survivor/
│  └─ ... (600+개 게임)
│
├─ _test_all_games.js        (게임 검증)
├─ apply-i18n.js              (국제화 적용)
├─ package.json               (의존성)
├─ README.md                  (프로젝트 설명)
└─ .github/workflows/         (CI/CD)
```

### 핵심 기능

#### 1. 멀티 게임 호스팅
- **600개 게임**: 다양한 장르와 개발자의 게임
- **독립적 배포**: 각 게임 폴더는 독립 실행 가능
- **공통 자산**: 공유 라이브러리 (Canvas, 물리 엔진 등)

#### 2. 자동 테스트 시스템 (_test_all_games.js)
- **로드 검증**: 모든 게임 index.html 로드 확인
- **성능 테스트**: 프레임 레이트, 메모리 사용량 검증
- **에러 추적**: 콘솔 에러 및 경고 수집
- **배포 전 검사**: 문제 있는 게임 자동 탐지

#### 3. 국제화 (i18n) 시스템 (apply-i18n.js)
- **다국어 지원**: 한국어, 영어, 스페인어, 프랑스어, 일본어, 중국어
- **자동 번역**: i18n JSON 파일 기반 텍스트 치환
- **로컬라이제이션**: 숫자, 날짜, 통화 포맷 변환

#### 4. 빌드 및 배포
- **버전 관리**: package.json 기반 시맨틱 버전 관리
- **깃허브 액션**: CI/CD 자동화 (push → 자동 배포)
- **롤백 지원**: 이전 버전 복구 가능

### 시스템 아키텍처

#### 게임 구조 (표준)
```
[game-name]/
├─ index.html         (진입점)
├─ game.js            (게임 로직)
├─ style.css          (스타일)
├─ assets/            (자산)
│  ├─ images/
│  ├─ sounds/
│  └─ i18n/          (국제화 JSON)
│     ├─ ko.json     (한국어)
│     ├─ en.json     (영어)
│     └─ ...
├─ package.json       (메타데이터)
└─ README.md          (게임 설명)
```

#### 테스트 파이프라인
```
_test_all_games.js
  ├─ 모든 게임 폴더 스캔
  ├─ index.html 존재 확인
  ├─ 헤드리스 브라우저로 로드
  ├─ 5초 동안 실행 (에러 감시)
  ├─ 성능 메트릭 수집
  ├─ 에러 로그 생성
  └─ 배포 적격성 판정
```

#### i18n 처리 파이프라인
```
apply-i18n.js
  ├─ 모든 게임의 i18n/ 폴더 스캔
  ├─ i18n JSON 파일 로드
  ├─ HTML/JS 의 i18n 태그 식별
  ├─ 국가별/언어별 텍스트 치환
  ├─ locale-specific.js 생성
  └─ 자동 로드 스크립트 추가
```

### 데이터 구조

#### 게임 메타데이터 (package.json)
```javascript
{
  "name": "block-bounce",
  "version": "1.2.3",
  "description": "블록 배치 라인 클리어 퍼즐",
  "genre": "puzzle",
  "mechanics": ["match-3", "block-placement"],
  "author": "EastSea Games",
  "rating": 4.2,
  "downloads": 125000,
  "releaseDate": "2025-06-15",
  "status": "active",
  "languages": ["ko", "en", "es", "fr", "ja", "zh"],
  "requirements": {
    "minWidth": 320,
    "minHeight": 480
  }
}
```

#### 테스트 결과 리포트
```javascript
{
  timestamp: "2026-04-21T10:30:00Z",
  totalGames: 600,
  successfulGames: 598,
  failedGames: 2,
  results: {
    "block-bounce": {
      status: "success",
      loadTime: 450,
      fps: 60,
      memoryUsage: 25,
      errors: []
    },
    "broken-game": {
      status: "failed",
      error: "TypeError: Cannot read property 'canvas' of undefined",
      errorLine: 42
    }
  }
}
```

### 성능 목표

#### 게임별 기준
- 로드 시간: <2초
- 초기 프레임 레이트: 60 FPS (모바일 30 FPS)
- 메모리: <50MB
- 저장소: <5MB

#### 플랫폼 레벨
- 동시 게임 실행: 100+
- 평균 응답 시간: <500ms
- 가용성: 99.9%+

### 배포 전략

#### 자동 배포 (CI/CD)
```
git push
  ↓
GitHub Actions trigger
  ↓
npm install
  ↓
npm run test (모든 게임 검증)
  ↓
npm run i18n (국제화 적용)
  ↓
npm run build (번들 생성)
  ↓
Deploy to games.eastsea.xyz
  ↓
DNS purge (캐시 초기화)
```

#### 수동 배포
- 개별 게임 폴더 업로드
- 버전 번호 증가
- 테스트 실행
- 라이브 배포

### 호환성

#### 브라우저 지원
- Chrome 70+, Firefox 65+, Safari 12+, Edge 79+

#### 모바일 지원
- iOS 12+, Android 8+
- 모바일 데이터 연결 최적화 (네트워크 재시도)

#### 오프라인 지원
- Service Worker 캐싱
- 오프라인 모드 (제한 기능)
