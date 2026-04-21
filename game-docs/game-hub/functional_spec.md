## game-hub 기능 명세서

### 개요
game-hub는 게임 작업의 중앙 운영 플랫폼입니다. 360개 배포 가능 게임을 관리하고, 카탈로그, 배포 상태, 아카이빙을 통해 게임 생태계의 운영 효율성을 극대화합니다.

### 프로젝트 구조

```
game-hub/
├─ 01-active-deploy/          (현재 배포 게임)
│  ├─ [game-folders] × 360
│  └─ deployment.json
│
├─ 02-master-catalog-docs/    (마스터 카탈로그)
│  ├─ games-list.json (358개)
│  ├─ INDEX.md (검색/네비게이션)
│  ├─ by-genre.md
│  ├─ by-release-date.md
│  ├─ by-rating.md
│  └─ by-mechanic.md
│
├─ 03-source-backlog/         (개발 백로그)
│  ├─ upcoming-games/
│  ├─ in-development/
│  └─ archived-proposals/
│
├─ 04-main-specs/             (주요 명세)
│  ├─ platform-standards.md
│  ├─ technical-requirements.md
│  ├─ monetization-guide.md
│  └─ qa-checklist.md
│
├─ 05-game-archive/           (비활성 게임)
│  ├─ deprecated/ (버그 또는 저성능)
│  ├─ seasonal/ (계절 게임)
│  └─ retired/ (업데이트 중단)
│
├─ 06-game-artifacts/         (자산 저장소)
│  ├─ screenshots/
│  ├─ thumbnails/
│  ├─ descriptions/
│  └─ videos/
│
├─ 07-blog-tools/             (마케팅/블로그)
│  ├─ game-reviews/
│  ├─ update-posts/
│  └─ press-releases/
│
└─ hub-config.json            (허브 설정)
```

### 핵심 기능

#### 1. 배포 상태 관리 (01-active-deploy)
- **현재 배포**: 360개 게임 실시간 호스팅
- **배포 검증**: 각 게임 폴더의 완전성 확인
- **롤백 지원**: 이전 버전으로 복구 기능
- **A/B 테스트**: 버전별 병렬 배포 지원

#### 2. 마스터 카탈로그 (02-master-catalog-docs)
- **게임 목록**: 358개 게임의 중앙 데이터베이스
- **다중 정렬**: 장르, 출시일, 평점, 메카닉별
- **빠른 검색**: 게임명, 장르, 태그 기반 검색
- **메타데이터**: 각 게임의 상세 정보 (제작사, 버전, 업데이트)

#### 3. 개발 백로그 (03-source-backlog)
- **예정 게임**: 다음 분기 출시 게임
- **진행 중**: 현재 개발 게임
- **보관**: 보류/취소된 제안서

#### 4. 표준 명세 (04-main-specs)
- **기술 요구사항**: 모든 게임 준수 사항
- **수익화 가이드**: 광고/IAP 표준화
- **QA 체크리스트**: 출시 전 검증 항목
- **플랫폼 표준**: UI/UX 일관성 기준

#### 5. 게임 아카이빙 (05-game-archive)
- **비활성 게임**: 더 이상 유지보수 안 함
- **계절 게임**: 특정 시즌만 활성화
- **은퇴 게임**: 완전 삭제 전 아카이브

#### 6. 게임 자산 저장소 (06-game-artifacts)
- **스크린샷**: 마케팅용 고품질 이미지
- **썸네일**: 앱스토어 나열용 아이콘
- **설명문**: 다국어 게임 설명
- **영상**: 게임플레이 영상 및 트레일러

#### 7. 블로그 도구 (07-blog-tools)
- **게임 리뷰**: 커뮤니티 리뷰 및 평점
- **업데이트 공지**: 새 버전 릴리스 노트
- **보도자료**: 주요 마일스톤 발표

### 시스템 아키텍처

#### 카탈로그 관리 시스템
```
HubCatalogManager
  ├─ GameRegistry (모든 게임 메타데이터)
  ├─ DeploymentTracker (배포 상태)
  ├─ VersionControl (게임 버전 관리)
  ├─ SearchEngine (빠른 검색 인덱싱)
  └─ ArchiveManager (비활성 게임 관리)
```

#### 데이터 흐름
```
Game Development
  ↓
03-source-backlog (예정/진행)
  ↓ [QA 통과]
  ↓
01-active-deploy (배포)
  ↓
02-master-catalog-docs [동기화]
  ↓
[사용자 접근]
  ↓
[비활성화 시]
  ↓
05-game-archive (보관)
```

### 데이터 구조

#### games-list.json (마스터 카탈로그)
```javascript
{
  version: "2.0.0",
  lastUpdate: "2026-04-21T10:30:00Z",
  totalGames: 358,
  games: [
    {
      id: "block-bounce-001",
      name: "Block Bounce",
      genre: "puzzle",
      mechanics: ["match-3", "block-placement"],
      rating: 4.2,
      downloads: 125000,
      releaseDate: "2025-06-15",
      version: "1.2.3",
      developer: "EastSea Games",
      status: "active",
      url: "/games/block-bounce/",
      thumbnail: "assets/thumbnails/block-bounce.png",
      description: "...",
      tags: ["casual", "puzzle", "colorful"]
    },
    ...
  ]
}
```

#### 배포 상태 파일
```javascript
{
  deploymentId: "deploy-2026-04-21",
  timestamp: "2026-04-21T10:30:00Z",
  activeGames: 360,
  inactiveGames: 5,
  games: {
    "block-bounce": {
      status: "active",
      version: "1.2.3",
      deployed: "2026-04-21T10:00:00Z",
      health: "healthy"
    }
  }
}
```

### 운영 워크플로우

#### 게임 추가 프로세스
```
1. 게임 개발 완료
2. QA 검증 (04-main-specs 기준)
3. 01-active-deploy 에 폴더 추가
4. games-list.json 업데이트
5. 02-master-catalog-docs 동기화
6. 웹사이트 갱신
7. 마케팅 공지
```

#### 게임 업데이트 프로세스
```
1. 코드/자산 수정
2. 로컬 테스트
3. 버전 번호 증가
4. 01-active-deploy 파일 덮어쓰기
5. games-list.json 버전 업데이트
6. 배포 검증
7. 사용자에게 알림
```

### 검색 및 네비게이션

#### 주요 인덱스
- **by-genre.md**: 장르별 분류 (Puzzle, Arcade, Strategy, Idle, Rhythm, Simulation)
- **by-release-date.md**: 출시 시간 순서
- **by-rating.md**: 사용자 평점 순서
- **by-mechanic.md**: 메카닉 분류 (Generator, AI-enhanced, Accessible 등)

#### 검색 기능
- 게임명 자동완성
- 다중 장르 필터링
- 메카닉 태그 기반 검색
- 출시 날짜 범위 검색

### 성능 및 확장성
- 카탈로그 로드: <1초
- 검색 응답: <100ms
- 배포 속도: 게임당 <30초
- 최대 1000개 게임까지 확장 가능

### 호환성
- 모든 웹 브라우저
- 모바일 최적화
- 오프라인 검색 (캐시)
