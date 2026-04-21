# Autopilot Spec — game-docs 재구성

**작성일**: 2026-04-21
**Phase**: 0 (Expansion)
**Scope**: `game-docs/` 하위 17개 최상위 항목 재구성
**Delivery**: 로컬 변경만 (커밋/푸시 없음)
**Non-goals**:
- `resources/`, `SKILL.md`, 루트 `README.md` 본문 편집 (단, 게임 수치 표기만 필요 시 정정)
- 새로운 게임 기획 작성
- 기술 스택 변경 또는 신규 태그 시스템 도입

---

## 1. 현 상태 스냅샷 (as-is)

### 1.1 최상위 목록

| 항목 | 유형 | 내부 파일 컨벤션 | 비고 |
|---|---|---|---|
| `ball-sort-puzzle/` | 기존 게임 | `functional_spec.md` + `game_design.md` | 정상 |
| `game-flip-gravity/` | 기존 게임 | `functional_spec.md` + `game_design.md` | 정상 |
| `game-gen/` | 기존 게임 | `functional_spec.md` + `game_design.md` | 정상 |
| `game-hub/` | 기존 게임 | `functional_spec.md` + `game_design.md` | 정상 |
| `game-proposals/` | 기존 게임 | `functional_spec.md` + `game_design.md` | 정상 |
| `game-v6/` | 기존 게임 | `functional_spec.md` + `game_design.md` | 정상 |
| `game-v9/` | 기존 게임 | `functional_spec.md` + `game_design.md` | 정상 |
| **`game-v10/`** | 기존 게임 | `functional_spec.md` only | ⚠️ `game_design.md` 누락 |
| `horse-racing/` | 기존 게임 | `functional_spec.md` + `game_design.md` | 정상 |
| `horse-racing-prototype/` | 기존 게임 | `functional_spec.md` + `game_design.md` | 정상 |
| `idle-hero/` | 기존 게임 | `functional_spec.md` + `game_design.md` | 정상 |
| `mahjong-zen/` | 기존 게임 | `functional_spec.md` + `game_design.md` | 정상 |
| `p0-colosseum-w2/` | 기존 게임 | `functional_spec.md` + `game_design.md` | 정상 |
| `rhythm-pulse-prototype/` | 기존 게임 | `functional_spec.md` + `game_design.md` | 정상 |
| `games/` | 자동 생성 카탈로그 | 하위 279 폴더 각 `game_design.md`, + `_auto-generated-batch/game_design.md` | ⚠️ 수치·ghost 카탈로그 |
| `new-concepts/` | 신규 기획 | 평면 `.md` 파일 10개 + `README.md` + `skill-test-game.md` + `_auto-generated-batch/`(빈) | ⚠️ 다수 |
| `README.md` | 인덱스 | 섹션 1~5, 통계 표 | ⚠️ 컨벤션 문구 오류, 통계 수치 미동기 |

### 1.2 감지된 불일치 (G-1 ~ G-9)

| ID | 위치 | 현상 | 증거 |
|---|---|---|---|
| **G-1** | `game-docs/README.md` §사용 가이드 | 컨벤션을 `README.md / DESIGN.md / CODE.md`로 기술 | 실제 15개 폴더 모두 `functional_spec.md / game_design.md` 사용 |
| **G-2** | `game-docs/game-v10/` | `game_design.md` 누락 | 다른 13개 기존 게임 폴더는 2개 파일 모두 보유 |
| **G-3** | `game-docs/new-concepts/README.md` | "신규 게임 5개"라고 기술 | 실제 10개 `.md` + `skill-test-game.md` 존재 |
| **G-4** | `game-docs/new-concepts/skill-test-game.md` | README 미기재 | "먹빛 서울" 풀 GDD이나 §메카닉 분류·§게임 목록에 부재 |
| **G-5** | `game-docs/new-concepts/_auto-generated-batch/` | 빈 디렉토리 | `ls` 결과 0 파일 |
| **G-6** | `game-docs/README.md` §섹션 2 | "Games Catalog — 600+ 게임 배포 카탈로그" | 실제 `games/` 하위 279 폴더 + 1 메타 = 280 |
| **G-7** | `game-docs/games/_auto-generated-batch/game_design.md` | "gen-YYYYMMDD* 패턴 폴더 56개" 카탈로그 | `games/` 하위에 `gen-*` 폴더 0개 (ghost 카탈로그) |
| **G-8** | `game-docs/README.md` §폴더 구조 | `new-concepts/`가 10개 하위 폴더 구조로 묘사 | 실제는 평면 `.md` 파일 구조 |
| **G-9** | 루트 `README.md` 인접 커밋 메시지 | "338 games full catalog" | 실제 `games/` 280 폴더, 어디서도 338이라는 숫자가 재현되지 않음 |

### 1.3 확인된 정상 컨벤션

- 14/15 기존 게임 폴더: `functional_spec.md`(기능 명세) + `game_design.md`(디자인 문서)
- 10/11 new-concepts 기획서: 단일 `.md` 파일에 풀 GDD 포함
- `games/` 하위 각 폴더: 단일 `game_design.md` 파일 (자동 생성용 경량 스키마)

---

## 2. 목표 구조 (to-be)

### 2.1 최상위 불변 요소

재배치 없음. 모든 최상위 항목의 경로·이름 보존. (리팩터 비용 대비 가치 낮음)

### 2.2 폴더별 목표 컨벤션

| 대분류 | 목표 컨벤션 | 근거 |
|---|---|---|
| 기존 게임 15개 | `functional_spec.md` + `game_design.md` 모두 존재 | 이미 14/15 적용, 최소 편차 |
| new-concepts | 평면 `.md` + `README.md`(인덱스) | 실제 구조 반영 |
| games (auto-gen) | 각 폴더 단일 `game_design.md`, 상위 `_auto-generated-batch/` 는 배치 메타데이터로만 유지 | 현 구조 유지 |

### 2.3 해결 매핑 (G-* → 해결책)

| ID | 해결책 | 예상 변경 |
|---|---|---|
| G-1 | `game-docs/README.md` §사용 가이드를 실제 컨벤션 문구로 교체 | Edit README.md (섹션 단위) |
| G-2 | `game-docs/game-v10/game_design.md` 신규 작성 — `functional_spec.md` 내용 기반으로 vision/메카닉/타겟/밸런싱·KPI 섹션 추출·확장. 허위 데이터 없이 "Generator 제품 특성 설계 문서" 포지션 | Write 신규 파일 |
| G-3 | `new-concepts/README.md` 를 10(+1)개 풀 GDD 기반으로 재작성 | Write (전면 재작성) |
| G-4 | `skill-test-game.md`를 new-concepts/README.md "보너스 — 장르 실험 기획" 섹션에 추가. 또는 파일명을 `experimental-ink-seoul.md`로 리네이밍 검토 | Edit README, rename 검토 |
| G-5 | `new-concepts/_auto-generated-batch/` 빈 디렉토리 제거 | rm -d |
| G-6 | `game-docs/README.md` 의 "600+" 수치를 실제 수치로 교체 | Edit |
| G-7 | `games/_auto-generated-batch/game_design.md` 의 ghost 56-카탈로그 내용을 실제 상태로 교체 (gen-* 폴더 부재 사실, 카탈로그가 히스토리 유물임 명시) | Edit |
| G-8 | `game-docs/README.md` §폴더 구조에서 new-concepts를 평면 `.md` 파일 목록으로 수정 | Edit |
| G-9 | `game-docs/README.md` 통계 표 및 본문에서 게임 수치를 실제 집계에 맞춰 갱신 (기존 15 + 신규 11 + auto-gen 279 + 메타 1 = 심층 수치) | Edit |

### 2.4 산출물 구조 예측

```
game-docs/
├── README.md                          ← 통계·컨벤션·폴더 구조 수정
├── game-v10/
│   ├── functional_spec.md             (변경 없음)
│   └── game_design.md                 ← 신규 작성
├── new-concepts/
│   ├── README.md                      ← 10(+1)개 반영 재작성
│   ├── autochess-starfield-tactics.md
│   ├── battleroyal-nanoswarm.md
│   ├── citybuilder-neon-district.md
│   ├── clicker-cosmic-forge.md
│   ├── deckbuild-runeforge.md
│   ├── dungeon-abyssal-gate.md
│   ├── match3-astral-cascade.md
│   ├── roguelike-echo-depths.md
│   ├── skill-test-game.md             (그대로. 파일명 변경은 plan에서 결정)
│   ├── survival-last-signal.md
│   └── tower-defense-voidwatch.md
│   (_auto-generated-batch/ 삭제)
├── games/
│   └── _auto-generated-batch/
│       └── game_design.md             ← 현실 반영 업데이트
└── [기타 14개 기존 게임 폴더 불변]
```

---

## 3. 요구사항 (FR / NFR)

### 3.1 기능 요구 (Functional)

- **FR-1**: 모든 기존 게임 폴더 15개에 `functional_spec.md` + `game_design.md` 두 파일이 모두 존재해야 한다.
- **FR-2**: `game-docs/README.md`의 폴더 구조 다이어그램·사용 가이드·통계 표는 파일 시스템 실체와 일치해야 한다.
- **FR-3**: `new-concepts/README.md`는 해당 디렉토리의 모든 풀 GDD를 누락 없이 나열한다.
- **FR-4**: `new-concepts/` 내 빈 디렉토리(`_auto-generated-batch/`)는 존재하지 않는다.
- **FR-5**: `games/_auto-generated-batch/game_design.md`는 현재 `games/` 하위에 `gen-*` 폴더가 존재하지 않는다는 사실을 반영한다.

### 3.2 비기능 요구 (Non-functional)

- **NFR-1** (최소 침습): 기존 개별 게임 기획 파일의 본문은 편집하지 않는다(인덱스/메타 정정 제외).
- **NFR-2** (링크 무결성): 모든 내부 링크는 재구성 후에도 유효해야 한다.
- **NFR-3** (허구 금지): `game-v10/game_design.md` 작성 시 `functional_spec.md`에 명시된 사실만 확장한다. 신규 기능·수치·팀 인원 추정 금지.
- **NFR-4** (경로 불변): 기존 폴더명 변경은 허용하지 않는다(외부 링크 파괴 방지). 단, `skill-test-game.md` 리네이밍은 plan 단계에서 찬반 결정.
- **NFR-5** (문서 스타일): 한국어 본문, 이모지 헤더 허용(기존 README 스타일 따름).

### 3.3 검증 기준 (Phase 3 QA에서 확인)

1. `find game-docs -type d` 결과에 빈 디렉토리 없음 (`games/_auto-generated-batch` 제외, 이건 파일 보유).
2. 15개 기존 게임 폴더 각각 `[ -f functional_spec.md ] && [ -f game_design.md ]`.
3. `grep -r "DESIGN.md\|CODE.md" game-docs/README.md`가 새 컨벤션 문구에 대해서만 매칭 (기존 오문구 제거).
4. `grep "600+" game-docs/README.md` 결과 없음.
5. `new-concepts/README.md`에 `tower-defense-voidwatch.md ... survival-last-signal.md` 10개 파일명 모두 언급.
6. `games/_auto-generated-batch/game_design.md`에 "gen-* 폴더가 현재 games/ 하위에 존재하지 않음" 또는 동등 표현.

---

## 4. 위험 및 결정 보류

| ID | 내용 | 결정 시점 |
|---|---|---|
| R-1 | `skill-test-game.md` 리네이밍 여부 (정보 아키텍처 개선 vs 링크 파괴 위험) | Phase 1 Planning |
| R-2 | `game-v10/game_design.md` 신규 파일을 어느 깊이까지 채울지 (최소 스켈레톤 vs 전체 GDD) — NFR-3에 의해 spec 기반 확장만 허용 | Phase 1 Planning |
| R-3 | `games/` 실제 279 폴더 개별 검증 (각 폴더 `game_design.md` 존재) — Phase 3 QA에서 샘플 검증 | Phase 3 QA |

---

## 5. 다음 단계

- Phase 1 (Planning): 본 spec을 기반으로 `.omc/plans/autopilot-impl.md` 작성
  - 변경할 파일 × 편집 행위 × 검증 테스트 × 커밋 단위(로컬) 매핑
  - R-1, R-2 의사결정 확정
- Phase 2 (Execution): plan에 따라 순차 구현
- Phase 3 (QA): §3.3 검증 기준 자동 실행
- Phase 4 (Validation): 다면 리뷰
- Phase 5 (Cleanup): `.omc/state/` 상태 정리
