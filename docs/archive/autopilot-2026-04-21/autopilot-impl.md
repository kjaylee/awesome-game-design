# Autopilot Implementation Plan — game-docs 재구성

**작성일**: 2026-04-21
**Input**: `.omc/autopilot/spec.md`
**Phase**: 1 (Planning)
**Delivery**: 로컬 변경만

---

## 1. 보류 결정 확정 (spec §4)

| ID | 결정 | 근거 |
|---|---|---|
| R-1 | `skill-test-game.md` **리네이밍 안 함** | NFR-1(최소 침습). 파일 본문의 "먹빛 서울 (Ink Seoul)"은 new-concepts/README.md 소개 문구로 인식성 충분. 외부 링크 없음. |
| R-2 | `game-v10/game_design.md` **중간 깊이**로 작성 | functional_spec.md에 명시된 사실(기술 스택, 10개 게임 리스트, 아키텍처 3레이어, 접근성 WCAG AAA, 타겟 플랫폼)만 추출 후 vision·타겟·메카닉 분류·플레이어 가치·KPI 스켈레톤·리스크 섹션으로 재구성. 허위 수치·인원 추정·로드맵 일정 금지. |

---

## 2. 작업 단위 (T-1 ~ T-7)

### T-1. game-docs/README.md 갱신 (spec G-1, G-6, G-8, G-9 해결)

**파일**: `game-docs/README.md`

**편집 지점**:

| 위치 | 변경 |
|---|---|
| §폴더 구조 코드블록 | `new-concepts/`를 평면 `.md` 목록으로 재묘사. 10개 `.md` + `skill-test-game.md`(실험) + `README.md` 반영 |
| §섹션 2 "Game Hub / Games Catalog" 라인 | "600+" 수치를 실측(`games/` 하위 279 폴더 + 1 배치 메타 = 280 항목)에 맞춰 교체. 배치 메타는 별도 각주로 설명 |
| §섹션 5 "전체 게임 목록" | 기존 15개 목록 유지, 신규 목록에 `skill-test-game.md`(11번째, 실험 기획) 추가. 가나다 순 재정렬 시 "Ink Seoul (먹빛 서울)"을 ㅇ로 삽입 |
| §사용 가이드 | 컨벤션 문구를 실제 `functional_spec.md` + `game_design.md`로 교체. 허위 `README.md / DESIGN.md / CODE.md` 문구 제거 |
| §통계 표 | "기존 게임 15" / "신규 기획 10 + 실험 1" / "총 25→26". 커버 메카닉 18 유지. 자동 생성 카탈로그 항목(games/ 하위 279) 별도 라인 추가 |

**도구**: `Edit` (섹션 단위 block replace, 병렬 불가 — 같은 파일)

**검증**:
- `grep "DESIGN.md\|CODE.md" game-docs/README.md` → 새 컨벤션 문구 외 미매칭
- `grep "600+" game-docs/README.md` → 0 매칭
- `grep "skill-test-game" game-docs/README.md` → ≥1 매칭

---

### T-2. game-v10/game_design.md 신규 작성 (spec G-2)

**파일**: `game-docs/game-v10/game_design.md` (Write)

**구조** (functional_spec 사실만 사용):

```
# Generator v10 — Game Design Document

## 1. 제품 컨셉 및 비전
  - "접근성 퍼스트 멀티장르 10게임 생성기"
  - Generator 시리즈 포지션 (v6: FPS 모니터링·멀티터치·저장 / v9: AI NPC·동적 난이도 / v10: 크로스플랫폼·반응형·A11y)
  - 핵심 가치: 장애인·저사양·다양한 입력 환경 포괄

## 2. 타겟 플레이어
  - 접근성 요구 사용자(스크린리더, 고대비, 애니메이션 감소)
  - 모바일/데스크톱/게임패드 다중 디바이스 사용자
  - (plan: functional_spec 기반 — 연령·세션길이·DAU 추정치 금지)

## 3. 메카닉 분류
  - 10게임 장르 매트릭스 (Puzzle/Arcade/Strategy/Idle/...)
  - Puzzle: Gridlock Puzzle, Word Cascade
  - Arcade: Stellar Breach
  - Strategy: Mirror Match
  - Idle: Pixel Factory
  - 추가 5개 (functional_spec 4.4 인용)

## 4. 플레이어 가치 및 차별점
  - 접근성 WCAG AAA 표준 (고대비)
  - 3-in-1 입력(Keyboard + Touch + Gamepad) 동시 지원
  - 반응형 320px~1920px 대응
  - 움직임 감소 / 리매핑 / 스크린리더 완전 호환

## 5. 게임플레이 루프 (Generator 관점)
  - 제작자 루프: 장르 선택 → 템플릿 파라미터 → 빌드 → 접근성 검증
  - 플레이어 루프: 입력 감지 → 정규화된 이벤트 → 반응형 렌더 → ARIA 피드백

## 6. 기술 스택 요약 (functional_spec 인용)
  - Python 3.x (gen_v10.py)
  - HTML5 Canvas + Vanilla JS ES6+
  - Input: Keyboard/Touch Events/Gamepad API
  - Layout: Container Queries + clamp()
  - A11y: ARIA Live Regions

## 7. UX 원칙
  - 입력 자동 감지 + 변경 프롬프트
  - 모바일 세로/가로 자동 전환
  - 고대비/폰트 크기/음성 안내 토글

## 8. 성공 지표 (KPI 스켈레톤)
  - 접근성 감사 통과율 (WCAG AAA)
  - 입력 지연 <N ms (N 명시 금지 — functional_spec에 없음)
  - 반응형 레이아웃 재계산 횟수
  - 접근성 기능 on/off 시 성능 영향 <5% (functional_spec 원문)

## 9. 리스크 및 완화
  - 브라우저 호환성 편차 (Safari prefers-reduced-motion)
  - 게임패드 맵핑 파편화 (Xbox/PS/Pro 편차)
  - 스크린리더별 ARIA 해석 차이 (NVDA/JAWS/VoiceOver/TalkBack)

## 10. Generator 시리즈 내 포지셔닝
  - v6 → v9 → v10 진화 경로 (단, v6/v9의 기능은 각 spec 참조, 본 문서에서 추정 금지)
```

**금지 사항 (NFR-3)**:
- 개발 기간/팀 규모/ARPU/MAU 수치 언급 금지
- functional_spec에 없는 기능(예: 블록체인, 멀티플레이어) 추가 금지
- "향후 v11 계획" 유추 금지

**검증**:
- `[ -f game-docs/game-v10/game_design.md ]`
- `wc -l game-docs/game-v10/game_design.md` ≥ 50 줄

---

### T-3. new-concepts/README.md 재작성 (spec G-3, G-4)

**파일**: `game-docs/new-concepts/README.md` (전면 Write)

**구조**:

```
# 신규 게임 기획서 컬렉션

본 디렉토리는 신규 게임 기획으로 작성된 10개의 풀 GDD + 1개의 실험적 장르 기획을 포함합니다.

## 🆕 신규 기획 10개 (메카닉별)

### Tower Defense — Void Watch
(existing entry)

### Roguelike / Roguelite — Echo Depths
(existing entry)

### Match-3 / Gem Swap — Astral Cascade
(existing entry)

### Deck Building / Card Roguelite — Rune Forge
(existing entry)

### City Builder / Casual Tycoon — Neon District
(existing entry)

### Battle Royale / Last Stand — Nano Swarm
(신규 항목 — battleroyal-nanoswarm.md의 실제 내용 요약)

### Auto Chess / Tactical RPG — Starfield Tactics
(신규 항목 — autochess-starfield-tactics.md)

### Dungeon Crawler / Action RPG — Abyssal Gate
(신규 항목 — dungeon-abyssal-gate.md)

### Clicker / Incremental — Cosmic Forge
(신규 항목 — clicker-cosmic-forge.md)

### Survival / Crafting — Last Signal
(신규 항목 — survival-last-signal.md)

## 🧪 실험 기획 (장르 탐색)

### Ink Seoul (먹빛 서울) — 파쿠르 액션 + 리듬 퍼즐
- 파일: skill-test-game.md
- 포지션: 장르 실험 — 한국 전통 수묵화 + 사이버펑크 서울
- 상태: 장르 실험 기획

## 📋 각 기획서 공통 구성 요소
(기존 섹션 유지)

## ⚙️ 기술 명세 요약 표
| 게임 | 엔진 | 언어 | 플랫폼 | 예상 개발 |
(10개로 확장)
```

**편집 전략**: 기존 5-게임 설명 구조를 10개로 확장하되, 내용은 각 개별 `.md` 파일의 실제 §1 핵심 컨셉 및 §2 게임 루프에서 사실만 인용. 추정 금지.

**검증**:
- `grep -c "^### " game-docs/new-concepts/README.md` ≥ 11 (10 신규 + 1 실험)
- 10개 파일명 각각 `grep "파일명.md" README.md` 매칭

---

### T-4. new-concepts/_auto-generated-batch/ 빈 디렉토리 제거 (spec G-5)

**명령**: `rmdir game-docs/new-concepts/_auto-generated-batch`

**주의**: `rm -rf` 사용 금지. `rmdir`로 빈 디렉토리만 제거 (안전). 내용이 있으면 실패.

**검증**: `[ ! -d game-docs/new-concepts/_auto-generated-batch ]`

---

### T-5. games/_auto-generated-batch/game_design.md 현실 반영 (spec G-7)

**파일**: `game-docs/games/_auto-generated-batch/game_design.md` (Edit)

**편집 지점**:

| 섹션 | 변경 |
|---|---|
| §폴더 목록 (56개) | 본문을 "**히스토리 카탈로그 — 현재 `games/` 하위에 `gen-*` 폴더는 존재하지 않음**"으로 교체. 과거 배치 네이밍 패턴 설명은 유지(참고용). |
| §처리 방침 | "정리 완료 — 모든 gen-* 실험 인스턴스는 archive되었거나 이름이 부여된 게임 폴더로 승격됨" 문구 추가 |
| 헤더/푸터 | 버전 2.0 및 날짜 2026-04-21 갱신 |

**검증**:
- `grep -c "gen-" game-docs/games/_auto-generated-batch/game_design.md` 감소 (카탈로그 표 제거)
- `grep "현재.*존재하지 않음\|archive" game-docs/games/_auto-generated-batch/game_design.md` ≥1

---

### T-6. (병렬 가능) — 현재 없음

모든 편집 대상이 쓰기·링크 의존 관계를 가지므로 직렬 실행.

---

### T-7. Phase 3 QA 자동 검증 스크립트

**파일**: 임시 검증 (파일 생성하지 않음, Bash로 직접 실행)

```bash
# QA-1: 모든 기존 게임 폴더 두 파일 존재
for d in ball-sort-puzzle game-flip-gravity game-gen game-hub game-proposals \
         game-v6 game-v9 game-v10 horse-racing horse-racing-prototype \
         idle-hero mahjong-zen p0-colosseum-w2 rhythm-pulse-prototype; do
  [ -f "game-docs/$d/functional_spec.md" ] || echo "MISSING spec: $d"
  [ -f "game-docs/$d/game_design.md" ]     || echo "MISSING design: $d"
done

# QA-2: 빈 디렉토리 없음 (new-concepts 하위)
find game-docs/new-concepts -type d -empty

# QA-3: README 문구 검사
grep "DESIGN.md\|CODE.md" game-docs/README.md | \
  grep -v "functional_spec\|game_design"
grep "600+" game-docs/README.md

# QA-4: new-concepts/README.md 10+1 파일 모두 언급
for f in tower-defense-voidwatch roguelike-echo-depths match3-astral-cascade \
         deckbuild-runeforge citybuilder-neon-district battleroyal-nanoswarm \
         autochess-starfield-tactics dungeon-abyssal-gate clicker-cosmic-forge \
         survival-last-signal skill-test-game; do
  grep -q "$f" game-docs/new-concepts/README.md || echo "MISSING MENTION: $f"
done

# QA-5: games/_auto-generated-batch ghost 카탈로그 제거
grep -c "gen-054\|gen-1775" game-docs/games/_auto-generated-batch/game_design.md
```

**통과 기준**: 각 QA-n이 예상 출력(빈 결과 또는 0 카운트 또는 미출력)을 반환.

---

## 3. 변경 영향 범위

| 변경 대상 | 신규 | 편집 | 삭제 |
|---|---|---|---|
| `game-docs/README.md` | | ✓ | |
| `game-docs/game-v10/game_design.md` | ✓ | | |
| `game-docs/new-concepts/README.md` | | ✓ (전면 재작성) | |
| `game-docs/new-concepts/_auto-generated-batch/` | | | ✓ |
| `game-docs/games/_auto-generated-batch/game_design.md` | | ✓ | |

**총 5개 파일 시스템 엔티티**. 기존 14개 게임 폴더 및 10개 new-concepts 풀 GDD 본문은 **불변**.

---

## 4. 실행 순서

1. **T-2**: `game-v10/game_design.md` 신규 (파일 생성, 위험 낮음)
2. **T-4**: 빈 디렉토리 `rmdir` (빠른 정리)
3. **T-5**: `games/_auto-generated-batch/game_design.md` 편집 (독립)
4. **T-3**: `new-concepts/README.md` 전면 재작성 (T-4 이후 정리된 상태 반영)
5. **T-1**: `game-docs/README.md` 최종 갱신 (T-2, T-3, T-4, T-5 완료 후 정합된 카운트 반영)

**근거**: T-1 (최상위 README)은 다른 모든 하위 변경을 반영해야 하므로 맨 마지막. T-4 빈 디렉토리 제거는 T-3 README 재작성 전 완료되어 카운트가 확정돼야 함.

---

## 5. Critic 자체 검증 (plan 제출 전)

| 체크 | 결과 |
|---|---|
| spec의 모든 G-1~G-9가 T-1~T-5로 매핑되는가? | ✅ G-1·6·8·9→T-1, G-2→T-2, G-3·4→T-3, G-5→T-4, G-7→T-5 |
| NFR-1(최소 침습) 위반 없는가? | ✅ 10개 풀 GDD 본문 편집 없음, 폴더 리네이밍 없음 |
| NFR-3(허구 금지) 위반 없는가? | ✅ T-2는 functional_spec 인용만 |
| 링크 파괴 위험? | ⚠️ skill-test-game.md 리네이밍 보류로 해소 (R-1). `_auto-generated-batch/` 제거는 빈 디렉토리라 링크 없음 |
| QA 검증 기준이 자동화 가능한가? | ✅ Bash 한 줄씩 |
| 롤백 가능한가? | ✅ 5개 파일만 변경. Git 이력 기반 복원 가능. 신규 파일 1개(game_design.md)는 단순 삭제 가능 |

→ **Plan 승인**. Phase 2 진입 준비 완료.
