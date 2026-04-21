# 🎨 Art Direction & Visual Design

> 아트 디렉션은 "예쁜 그림 그리기"가 아니라 "비주얼 언어로 게임의 영혼 전달하기"다.

---

## 🖼️ 픽셀아트 (Pixel Art)

### 원칙

픽셀아트는 기술적 한계에서 태어난 미학이지만, 현대 게임에서는 의도적 예술 선택이다.

**픽셀아트의 7가지 핵심 원칙**:

**1. 앤티-앨리어싱 (Anti-Aliasing) 회피**
픽셀아트에서는 의도적으로 계단 현상을 유지. 의도치 않은 반투명 픽셀(dirty pixels)은 아마추어 티가 남.
```
잘못된 예: 두 색 사이에 중간색 픽셀 자동 생성
올바른 예: 의도된 1픽셀 라인, 명확한 경계
```

**2. 색 수 제한 (Palette Restriction)**
각 스프라이트에 사용하는 색 수를 제한하면 일관성과 레트로 감이 생김:
- GB 스타일: 4색
- NES 스타일: 스프라이트당 4색 (3색 + 투명)
- SNES 스타일: 팔레트당 16색
- 현대 인디 픽셀: 제한 없지만 팔레트 일관성 유지

**3. 일관된 광원 방향**
모든 스프라이트의 빛이 같은 방향에서 와야 함. 일반적으로 좌상단 45도.
```
✓ 모든 캐릭터: 빛이 좌상단에서
✗ 캐릭터A: 좌상단 / 캐릭터B: 우하단 (혼재 금지)
```

**4. 픽셀 클러스터링 (Pixel Clustering)**
비슷한 색상의 픽셀들이 뭉쳐야 자연스러운 형태가 나옴. 고립된 단일 픽셀 줄이기.

**5. 아웃라인 처리**
- 하드 아웃라인 (검은 테두리): 만화/액션 게임 느낌
- 셀프-아웃라인 (더 어두운 같은 색): 부드러운 느낌 (Superbrothers 스타일)
- 아웃라인 없음: 분위기 있는 배경 작업

**6. 해상도와 타일 크기의 통일성**
```
일반적인 타일 크기 조합:
8×8 픽셀: GB/NES 스타일, 매우 극미적
16×16: SNES/GBA 스타일, 인디 표준
32×32: 현대 픽셀 인디 표준
48×48 이상: 디테일 많은 현대 픽셀아트
```

**7. 애니메이션 최소 프레임**
```
걷기: 4~8프레임 (2~4프레임도 가능)
공격: 3~6프레임
아이들: 2~4프레임 (호흡 효과)
피격: 2~3프레임 (플래시 + 넉백)
```

### 주요 도구

**Aseprite**
- 링크: [aseprite.org](https://www.aseprite.org/)
- 가격: $20 (영구 라이선스) / 무료 (소스 컴파일)
- 픽셀아트/스프라이트 애니메이션 전용 업계 표준 도구
- 타임라인 애니메이션, 레이어, 팔레트 관리, 스프라이트 시트 내보내기
- 루아 스크립팅으로 자동화 가능

**Pyxel Edit**
- 링크: [pyxeledit.com](https://pyxeledit.com/)
- 가격: $9 (영구 라이선스)
- 타일맵 작업에 특화됨
- 타일 기반 레벨 설계 동시 가능

**LibreSprite** (무료 Aseprite 포크)
- [libresprite.github.io](https://libresprite.github.io/)

**GraphicsGale** (레거시, 무료)
- NES 시대 픽셀 아티스트들이 많이 사용

### 참고 자료 & 학습

| 자료 | 링크 | 설명 |
|------|------|------|
| Pixel Joint | [pixeljoint.com](https://pixeljoint.com/) | 커뮤니티, 피드백, 갤러리 |
| Lospec | [lospec.com](https://lospec.com/) | 팔레트 공유, 튜토리얼 |
| Pedro Medeiros 튜토리얼 | [saint11.org/blog/pixel-art-tutorials/](https://saint11.org/blog/pixel-art-tutorials/) | 무료 고퀄리티 튜토리얼 |
| Aseprite 공식 문서 | [aseprite.org/docs/](https://www.aseprite.org/docs/) | 도구 완전 정복 |

---

## 🎮 UI/UX 게임 디자인 패턴

### 게임 HUD 설계 원칙

**1. 정보 계층 (Information Hierarchy)**
```
즉각 필요 정보 (항상 화면에):
- HP/생명력
- 탄약/자원
- 현재 스킬/무기

중간 필요 정보 (전투 중):
- 쿨다운
- 미니맵
- 퀘스트 지시자

선택적 정보 (필요 시 꺼낼 수 있게):
- 인벤토리
- 스탯 상세
- 지도
```

**2. 화면 구역별 HUD 배치**
```
┌─────────────────────────────┐
│ [좌상단: HP/MP/자원]          │
│                             │
│    [중앙: 게임 화면]          │
│                             │
│ [좌하단: 스킬]  [우하단: 지도] │
└─────────────────────────────┘

Fitts의 법칙 적용:
- 자주 쓰는 UI = 화면 모서리/엣지 (무한 크기 효과)
- 위험한 버튼 (아이템 버리기 등) = 중앙에서 멀리
```

**3. 색각이상 접근성**
```
적/녹 색각이상 (Deuteranopia/Protanopia): 가장 흔함 (남성의 8%)
- 빨강/녹색 HP 바 → 파랑/주황 또는 아이콘 추가
- 색상만으로 정보 전달 금지 (모양/패턴 병용)

색각이상 시뮬레이터: 
- Sim Daltonism (macOS)
- Coblis (웹)
```

### 메뉴/UI 패턴

**인벤토리 시스템**

| 유형 | 예시 | 장점 | 단점 |
|------|------|------|------|
| 그리드 인벤토리 | Diablo, Resident Evil | 시각적 무게감 | 관리 피로도 |
| 목록 인벤토리 | Final Fantasy | 탐색 빠름 | 시각적 개성 없음 |
| 제한 슬롯 | Dark Souls | 극적 선택 강요 | 관리 스트레스 |
| 무한 인벤토리 | Pokemon | 스트레스 없음 | 경제 밸런싱 어려움 |
| 공간 퍼즐 인벤토리 | Resident Evil 4, Escape from Tarkov | 전략 층위 추가 | 복잡성 높음 |

**온보딩 패턴**

```
1. 맥락 튜토리얼 (Contextual Tutorial)
   행동이 필요할 때 힌트 등장
   "WASD로 이동" → 이동이 필요한 순간에만 표시
   
2. 마스코트 가이드
   마리오의 루마, 젤다의 나비
   귀여움으로 거부감 감소, 반복 설명 수용

3. "학습 후 테스트" 구조
   메카닉 설명 → 안전한 환경에서 실습 → 실전 적용
   Half-Life의 블랙메사 연구소
   
4. 숨겨진 튜토리얼
   플레이어가 배운다는 것을 모르게 가르침
   Super Mario Bros 1-1의 설계
```

---

## 🎨 색상 이론 실전

### 팔레트 제작 방법론

**1. 기반 색상 결정**
```
세계관 → 감정 → 색상 결정 흐름:

공포 게임: 불포화 (채도↓) + 어두운 색조 + 보라/회색 계열
판타지: 선명한 색상, 금색/에메랄드 포인트
사이버펑크: 형광 핑크/시안 + 거의 검은 배경
미니멀리스트: 2~3색 + 대량의 흰색
```

**2. 5계층 팔레트 구조**
```
Primary:   게임의 주인공/핵심 UI 색상 (1~2색)
Secondary: 보조 요소, 동료 UI (1~2색)
Accent:    중요 정보 강조, 보상 (1색)
Neutral:   배경, 텍스트, 그림자 (3~5 단계)
Semantic:  빨강=위험, 녹색=안전, 파랑=정보 (시스템 색상)
```

**3. 밸류 (명도) 우선 설계**
```
색상 이전에 명도 계획이 먼저:
어두운 배경 → 중간 요소 → 밝은 핵심

그레이스케일에서 작동하면 색상을 더해도 작동함
그레이스케일에서 안 보이면 색상만으로는 해결 불가
```

### 접근성 색상 기준

```
WCAG 2.1 기준:
일반 텍스트: 대비 비율 4.5:1 이상
큰 텍스트: 3:1 이상
UI 컴포넌트: 3:1 이상

게임 HUD 권장: 7:1 이상 (빠른 가독성 필요)

도구:
- Contrast (macOS 앱)
- WebAIM Contrast Checker (웹)
- Colorable (웹)
```

### 팔레트 참고 도구

| 도구 | 링크 | 용도 |
|------|------|------|
| Coolors | [coolors.co](https://coolors.co/) | 팔레트 생성/저장 |
| Lospec Palette List | [lospec.com/palette-list](https://lospec.com/palette-list) | 픽셀아트 팔레트 컬렉션 |
| Adobe Color | [color.adobe.com](https://color.adobe.com/) | 색상 이론 기반 팔레트 |
| Paletton | [paletton.com](https://paletton.com/) | 보색/삼색/사색 계산 |

---

## 🔊 사운드 디자인 기초

### FMOD
**링크**: [fmod.com](https://www.fmod.com/)  
**가격**: 인디(연매출 $200k 미만) 무료  
**엔진 통합**: Unity, Unreal, Godot, 거의 모든 엔진

인터랙티브 오디오의 업계 표준. 적응형 음악, 환경 음향, 복잡한 파라미터 시스템.

**핵심 기능**:
- **이벤트 시스템**: 사운드를 코드가 아닌 디자이너 주도로 조정
- **파라미터**: 게임 상태에 따라 음악이 자동 변화
  ```
  예: 플레이어 HP가 낮아질수록 음악 긴장도 상승
  parameter: player_hp (0.0 ~ 1.0)
  → 0.3 이하: 긴장 레이어 페이드인
  → 0.1 이하: 심장박동 효과음 추가
  ```
- **스냅샷**: 전투/탐험 모드 전환 시 전체 믹스 변경

### Wwise
**링크**: [audiokinetic.com/wwise](https://www.audiokinetic.com/wwise/)  
**가격**: 연매출 $150k 미만 / 150개 이하 자산 무료  
**특징**: FMOD보다 강력하지만 학습 곡선이 더 가파름

AAA 게임의 표준 (Assassin's Creed, Fortnite, PUBG 사용).

### 인디 게임 사운드 가이드

**무료 사운드 소스**:
- [freesound.org](https://freesound.org/) — CC 라이선스 사운드 방대
- [BFXR](https://www.bfxr.net/) — 레트로 8비트 SFX 생성기 (온라인, 무료)
- [jsfxr](https://sfxr.me/) — BFXR 웹 버전
- [OpenGameArt](https://opengameart.org/) — 사운드+아트 무료

**사운드 디자인 원칙**:
```
1. 레이어링 (Layering):
   한 효과음 = 여러 사운드의 조합
   폭발음 = 저주파 쿵 + 고주파 파삭 + 공기 이동 소리

2. 피치 랜덤화:
   동일 효과음을 ±10% 피치 변화로 반복 사용
   단조로움 방지

3. 공간감 (Spatialization):
   3D 오디오로 소리가 방향성을 가지게
   게임 내 위치 기반 음량/필터 변화
   
4. 다이나믹 레인지:
   평소 사운드: 50~60%
   중요 효과음: 70~80%
   클라이맥스: 90~100%
   (항상 최대 음량이면 클라이맥스가 없음)
```

---

## 🦴 애니메이션

### Spine
**링크**: [esotericsoftware.com](https://esotericsoftware.com/)  
**가격**: Essential $99 / Professional $299 (영구)  
**특징**: 뼈대 기반 2D 애니메이션, 모든 주요 엔진 지원

픽셀아트 이외의 2D 캐릭터 애니메이션 표준 도구.

**장점**:
- 뼈대 기반으로 1개 에셋으로 다양한 애니메이션 생성
- 런타임 메쉬 변형 (Mesh)으로 자연스러운 움직임
- 아이들/걷기/달리기를 동적으로 블렌딩

**Spine vs 프레임 애니메이션 선택 기준**:
```
Spine 적합:
- 캐릭터 수가 많음 (각각 애니메이션 프레임 그리기 어려움)
- 부드러운 움직임이 필요한 게임
- 개발 시간 단축 필요

프레임 애니메이션 적합:
- 픽셀아트 (Aseprite로 직접 그리기)
- 극도로 개성 있는 스타일 (Cuphead 스타일)
- 팀에 전문 애니메이터 있음
```

### DragonBones
**링크**: [dragonbones.com](http://dragonbones.com/)  
**가격**: 무료 (오픈소스)  
**특징**: Spine의 무료 대안

### 애니메이션 12원칙 (Disney의 12가지 원칙)

모든 애니메이터가 알아야 할 기초:

```
1. 스쿼시 앤 스트레치 (Squash & Stretch)
   형태가 변형되어 무게감/탄성 표현
   
2. 예비 동작 (Anticipation)
   큰 움직임 전의 반대 방향 작은 움직임
   점프 전 무릎 굽히기
   
3. 스테이지 연출 (Staging)
   행동/아이디어를 가장 명확하게 보여주는 구도
   
4. 직접 행동/포즈 투 포즈 (Straight Ahead & Pose to Pose)
   처음부터 순서대로 OR 키프레임 먼저
   
5. 팔로우 스루와 오버래핑 (Follow Through & Overlapping)
   주 움직임 후 머리카락/옷 등이 계속 움직임
   
6. 느린 시작과 끝 (Slow In & Slow Out)
   움직임의 자연스러운 가속/감속 (이징)
   
7. 호 (Arcs)
   생물체의 움직임은 직선이 아닌 호를 그림
   
8. 세컨더리 액션 (Secondary Action)
   주 움직임을 지지하는 부가 움직임
   
9. 타이밍 (Timing)
   프레임 수로 속도와 무게 표현
   
10. 과장 (Exaggeration)
    현실보다 더 극적으로 표현
    
11. 견고한 그리기 (Solid Drawing)
    3D 형태감 유지
    
12. 매력 (Appeal)
    캐릭터의 시각적 매력과 개성
```

---

## 📐 아트 디렉션 프로세스

### 비주얼 컨셉 확립 단계

```
1단계: 레퍼런스 보드 (Mood Board)
   Pinterest, Artstation, ArtStation에서 50+ 이미지 수집
   "이런 느낌을 원한다"
   
2단계: 스타일 가이드 초안
   - 해상도/타일 크기
   - 색상 팔레트 (6~12색)
   - 아웃라인 스타일
   - 빛 방향
   
3단계: 스타일 테스트
   주인공 캐릭터 1개, 타일 세트 1개, UI 요소 1개로 테스트
   "이 세 가지가 같은 게임에 속하는가?"
   
4단계: 전체 적용
   스타일 가이드를 팀 전체가 준수
```

---

## 📚 아트 학습 자료

| 자료 | 링크 | 설명 |
|------|------|------|
| Ctrl+Paint | [ctrlpaint.com](https://www.ctrlpaint.com/) | 디지털 페인팅 기초, 무료 |
| Proko | [proko.com](https://www.proko.com/) | 인체/인물 드로잉 |
| ArtStation | [artstation.com](https://www.artstation.com/) | 프로 게임 아티스트 포트폴리오 |
| GDC Art Summit | [gdcvault.com](https://gdcvault.com/) | 게임 아트 방향성 강연 |
| The Animator's Survival Kit | Richard Williams 저서 | 애니메이션 바이블 |
| Vimlark | [youtube.com/@Vimlark](https://www.youtube.com/@Vimlark) | 픽셀아트 게임 개발 유튜브 |
