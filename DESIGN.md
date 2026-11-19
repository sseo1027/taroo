# 타로카드 (오늘의 타로) — Design System & Style Guide
> Golden Hour Editorial × Modern Mystic Tarot

**Theme:** Light (Warm Editorial)  
**Target:** 20대 대학생 · 사회초년생을 위한 모바일 웹서비스  
**Reference Basis:** Superhuman Editorial Dashboard + Tailwind v4 + shadcn/ui

---

## 1. 개요 (Overview & Mood)

'오늘의 타로'는 신비주의에 치우친 전형적인 운세 서비스의 어둡고 무거운 톤을 탈피하여, **감각적인 에디토리얼 무드(Superhuman Editorial)** 와 **현대적인 타로(Modern Mystic)** 가 결합된 디자인 시스템을 지향합니다.

* **Warm Parchment Canvas:** 차가운 순백색(`#ffffff`) 대신 따뜻한 양피지 빛 크림톤(`#f2f0eb`)을 기본 배경으로 사용하여 종이 위의 인쇄물 같은 편안함과 몰입감을 줍니다.
* **Midnight Wine & Royal Violet:** 브랜드 핵심 액션에는 묵직한 와인 버건디(`#421d24`)를 먹색처럼 사용하고, 별자리 및 신비로운 강조 요소에는 생동감 있는 로열 바이올렛(`#714cb6`)과 라일락 미스트(`#d4c7ff`)로 리듬감을 부여합니다.
* **Hairline & Glass Layers:** 과도한 드롭 섀도우(Drop Shadow)를 배제하고 섬세한 1px 헤어라인 보더(`#e3e3e2`)와 카드 레이어링으로 깊이감을 형성합니다.
* **Mobile-First & Privacy Transparency:** 1분 이내 카드 뽑기를 마치는 모바일 뷰포트(최대 440px 중앙 정렬)에 최적화하며, "개인정보는 서버에 저장하지 않고 즉시 폐기"된다는 안내를 투명하고 깔끔한 컴포넌트로 전달합니다.

---

## 2. 디자인 토큰 — 색상 (Color Tokens)

### 2.1 팔레트 (Palette)

| Token Name | Hex | CSS Variable | Role & Usage |
|---|---|---|---|
| **Midnight Wine** | `#421d24` | `--color-midnight-wine` | **메인 액션 CTA 버튼** (`[타로 시작]`, `[카드 한 장 뽑기]`), 강조 타이틀, 서비스 푸터. 잉크처럼 깊은 버건디 |
| **Royal Violet** | `#714cb6` | `--color-royal-violet` | **신비로운 악센트**, 별자리 아이콘/텍스트, 링크, 선택 상태 테두리 |
| **Lilac Mist** | `#d4c7ff` | `--color-lilac-mist` | **보조 버튼/뱃지 배경**, 토글 선택 활성화 배경, 포커스 링, 연한 하이라이트 |
| **Warm Parchment** | `#f2f0eb` | `--color-warm-parchment` | **페이지 전체 배경 (Canvas)**. 차분하고 따뜻한 크림 양피지 톤 |
| **Paper White** | `#ffffff` | `--color-paper-white` | **타로 카드 면**, 폼 입력창 배경, 캡처용 결과 카드 (양피지 위로 떠오르는 표면) |
| **Soft Mist** | `#e3e3e2` | `--color-soft-mist` | **헤어라인 보더**, 구분선, 비활성 버튼 외곽선 |
| **Ink Charcoal** | `#292827` | `--color-ink-charcoal` | **기본 본문 텍스트**, 주요 헤드라인, 굵은 라벨. 흑색(#000) 대신 따뜻한 먹색 |
| **Stone Gray** | `#666666` | `--color-stone-gray` | **보조 안내 문구**, 플레이스홀더, 오락용 안내 및 개인정보 안내 문구 |
| **Deep Lagoon** | `#0c4243` | `--color-deep-lagoon` | **카드 뒷면 기하학 일러스트 포인트**, 심야 무드 악센트 |

### 2.2 shadcn / Tailwind 시맨틱 토큰 매핑 (Semantic Mapping)

| shadcn Token | CSS Variable / Value | 용도 |
|---|---|---|
| `--background` | `var(--color-warm-parchment)` (`#f2f0eb`) | 모바일 쉘 및 전체 페이지 배경 |
| `--foreground` | `var(--color-ink-charcoal)` (`#292827`) | 주 텍스트 색상 |
| `--card` | `var(--color-paper-white)` (`#ffffff`) | 결과 타로 카드, 입력 폼 컨테이너 |
| `--card-foreground` | `var(--color-ink-charcoal)` (`#292827`) | 카드 내부 텍스트 |
| `--popover` | `var(--color-paper-white)` (`#ffffff`) | 팝업, 툴팁, 토스트 표면 |
| `--primary` | `var(--color-midnight-wine)` (`#421d24`) | 핵심 액션 버튼 배경 |
| `--primary-foreground` | `#ffffff` | 핵심 액션 버튼 텍스트 |
| `--secondary` | `var(--color-lilac-mist)` (`#d4c7ff`) | 보조 액션 버튼 (`[이미지 저장]`), 선택 칩 |
| `--secondary-foreground`| `var(--color-ink-charcoal)` (`#292827`) | 보조 버튼 텍스트 |
| `--muted` | `#e9e6df` (Parchment Tint) | 비활성 영역, 토글 그룹 배경 |
| `--muted-foreground` | `var(--color-stone-gray)` (`#666666`) | 서브 텍스트, 힌트 문구, 안내 라벨 |
| `--accent` | `var(--color-lilac-mist)` (`#d4c7ff`) | 호버/포커스 하이라이트 |
| `--accent-foreground` | `var(--color-royal-violet)` (`#714cb6`) | 악센트 강조 텍스트 |
| `--border` | `var(--color-soft-mist)` (`#e3e3e2`) | 컴포넌트 1px 헤어라인 테두리 |
| `--input` | `var(--color-soft-mist)` (`#e3e3e2`) | 인풋 박스 테두리 |
| `--ring` | `var(--color-royal-violet)` (`#714cb6`) | 포커스 링 (2px offset) |

---

## 3. 타이포그래피 (Typography)

한글 가독성과 에디토리얼 무드를 동시에 구현하기 위해 **Pretendard**를 1순위로 사용하며, 영문/숫자 디스플레이에는 **Inter** 또는 **Super Sans VF**를 사용합니다.

* **Primary Font Stack:**  
  `"Pretendard Variable", Pretendard, Inter, -apple-system, BlinkMacSystemFont, system-ui, Roboto, sans-serif`
* **Headline Voice:** 헤드라인은 과도하게 두껍지 않은 `weight 460 ~ 540`을 사용하여 속삭이듯 단정하고 자신감 있는 톤을 연출합니다.
* **Korean Line Break:** 모든 한국어 문장에는 `break-keep-all`과 `word-break: keep-all`을 필수로 적용하여 단어 단위 줄바꿈을 유지합니다.

### 타입 스케일 (Type Scale)

| Role | Font Size | Weight | Line Height | Letter Spacing | 적용 컴포넌트 |
|---|---|---|---|---|---|
| **display** | 32px | 500 (Medium) | 1.2 | -0.8px | S-01 메인 타이틀 (🔮 오늘의 타로) |
| **heading-lg** | 24px | 500 (Medium) | 1.3 | -0.5px | S-03 카드 이름 (XIX 태양) |
| **heading-sm** | 18px | 600 (SemiBold) | 1.4 | -0.3px | S-02 섹션 헤더, 카드 상단 사용자명 |
| **body-lg** | 16px | 460 / 500 | 1.6 | -0.2px | **F-4 맞춤 해석 3줄** (핵심 문장 가독성) |
| **body-md** | 15px | 400 (Regular) | 1.5 | 0 | 폼 라벨, 폼 입력 텍스트, 버튼 텍스트 |
| **body-sm** | 13px | 400 / 500 | 1.5 | 0 | 주제 토글 버튼, 뱃지, 상태 문구 |
| **caption** | 12px | 400 (Regular) | 1.4 | 0 | ※ 오락용 타로 안내, 🔒 개인정보 미저장 안내 |

---

## 4. 형태 및 간격 (Spacing, Shapes & Elevation)

### 4.1 기본 단위 및 간격 (Spacing Scale)
* **Base Unit:** `4px`
* **Mobile Page Padding:** 수평 `20px` (`px-5`), 수직 `24px~32px` (`py-6`~`py-8`)
* **Component Gap:**
  * 폼 필드 간 간격: `16px` (`gap-4`)
  * 주제 선택 그리드 간격: `10px` (`gap-2.5`)
  * 버튼 그룹 간격: `12px` (`gap-3`)
  * 해석 문장 간격: `8px` (`gap-2`)

### 4.2 모서리 둥글기 (Border Radius)

| 요소 | Radius Token | Value | 용도 |
|---|---|---|---|
| **Pill / Badges** | `rounded-full` | `9999px` | 별자리 뱃지, 주제 선택 칩, 상태 태그 |
| **Action Buttons** | `rounded-2xl` | `16px` | 메인 CTA (`[타로 시작]`, `[카드 한 장 뽑기]`) |
| **Inputs / Controls** | `rounded-xl` | `12px` | 텍스트 인풋창, 날짜 입력창 |
| **Cards & Containers** | `rounded-2xl` | `16px` / `20px` | 타로 결과 카드, 폼 컨테이너 카드 |
| **Small Buttons** | `rounded-lg` | `8px` | `[다시 뽑기]`, `[처음으로]` 보조 버튼 |

### 4.3 그림자 및 깊이 (Elevation)
* 과도한 그림자를 사용하지 않습니다.
* **기본 카드:** `border: 1px solid var(--color-soft-mist)` + 은은한 종이 질감
* **결과 카드 플로팅 (Subtle Depth):**  
  `box-shadow: 0 8px 32px -4px rgba(66, 29, 36, 0.06), 0 2px 8px -2px rgba(66, 29, 36, 0.04);`
* **카드 뒤집기 3D 효과:** `perspective: 1000px`, `transform-style: preserve-3d`

---

## 5. 모바일 뷰포트 & 레이아웃 (Layout Architecture)

* **쉘 구조 (Mobile Container):**
  * 데스크톱에서도 모바일 앱 경험을 유지하기 위해 `max-w-[440px] mx-auto min-h-dvh` 중앙 배치.
  * 좌우 데스크톱 여백은 차분한 Parchment 배경 유지.
* **안전 영역 (Safe Area):**
  * 모바일 브라우저 상/하단 바를 고려한 `padding-bottom: env(safe-area-inset-bottom, 24px)`.
* **인스타 스토리 최적화 이미지 캔버스 (F-5):**
  * 결과 카드 이미지 저장 시 `1080 × 1350 px` (4:5 황금 세로 비율) 규격으로 렌더링.

---

## 6. 컴포넌트 명세 (Component Guidelines)

### 6.1 Primary CTA Button (핵심 액션 버튼)
* **적용:** `[타로 시작]` (S-01), `[카드 한 장 뽑기]` (S-02)
* **스타일:**
  * 배경: `bg-[#421d24]` (Midnight Wine)
  * 텍스트: `text-white`, `font-medium`, `text-[16px]`
  * 크기: 높이 `52px` (`h-[52px]`), `w-full`, `rounded-2xl`
  * 호버/활성: `hover:opacity-95`, `active:scale-[0.98]` (미세한 햅틱 감성)
  * **비활성 상태 (Disabled):** `bg-[#e3e3e2] text-[#666666] cursor-not-allowed`

### 6.2 Secondary & Ghost Button (보조 버튼)
* **적용:** `[이미지 저장]`, `[결과 공유]`, `[다시 뽑기]`, `[처음으로]`
* **스타일:**
  * **`[이미지 저장]` (F-5):** `bg-[#d4c7ff] text-[#292827] border border-[#714cb6]/20 font-medium h-[48px] rounded-xl hover:bg-[#c9b9ff]`
  * **`[결과 공유]` (F-6):** `bg-white text-[#292827] border border-[#e3e3e2] font-medium h-[48px] rounded-xl hover:bg-[#f9f8f6]`
  * **`[다시 뽑기]`, `[처음으로]` (F-7):** 고스트/라이트 버튼, `text-[#666666] text-sm hover:text-[#292827] py-2 px-3`

### 6.3 Form Field (입력 컴포넌트 — shadcn FieldGroup / Field)
* **적용:** 이름 (필수, 10자), 생년월일 (필수, YYYY.MM.DD), 전공 (선택)
* **규칙:**
  * `FieldGroup` 내부 `Field` 구조 준수.
  * 배경: `bg-white`
  * 테두리: `border border-[#e3e3e2] focus:border-[#714cb6] focus:ring-2 focus:ring-[#714cb6]/20`
  * 높이: `48px`, `rounded-xl`, `px-4 text-[15px]`
  * 라벨: `text-[13px] font-semibold text-[#292827] mb-1.5`
  * 에러 상태: `aria-invalid="true" border-red-500 text-red-600 text-xs mt-1`

### 6.4 Topic Selector (주제 선택 — shadcn ToggleGroup)
* **적용:** 6개 주제 (`💼 커리어`, `💰 재물`, `💕 연애`, `🌿 건강`, `📚 학업`, `✨ 종합`)
* **배치:** `grid grid-cols-3 gap-2.5`
* **스타일:**
  * 기본: `bg-white border border-[#e3e3e2] text-[#292827] rounded-xl py-3 text-center text-sm transition-all`
  * 선택(Active): `bg-[#421d24] text-white border-[#421d24] font-medium shadow-sm` 또는 `bg-[#d4c7ff] text-[#421d24] border-[#714cb6] font-semibold`

### 6.5 Privacy Alert Callout (개인정보 안내문)
* **적용:** S-02 입력 화면 하단, S-03 결과 화면 하단
* **스타일:**
  * 외곽선 없는 소프트 배경: `bg-[#e9e6df]/70 rounded-xl p-3.5`
  * 아이콘: `🔒` (단색 라인 아이콘)
  * 문구: `text-xs text-[#666666] leading-relaxed break-keep-all`
  * 내용: *"입력한 이름 · 생년월일 · 전공은 해석을 만드는 데만 쓰고, 서버로 보내거나 저장하지 않아요. 창을 닫거나 [처음으로]를 누르면 바로 지워져요."*

### 6.6 Tarot Card & 3D Flip (타로 카드 및 애니메이션)
* **카드 비율:** 세로 직사각형 (전형적인 타로 황금비 1 : 1.6 ~ 1.7)
* **카드 뒤집기:**
  * 앞면/뒷면 `transform-style: preserve-3d`, `transition: transform 0.8s cubic-bezier(0.34, 1.56, 0.64, 1)`
  * 카드 뒷면: 딥라군/와인 바탕의 미스틱 기하학 문양 + 골드/바이올렛 라인
  * 카드 앞면: 메이저 아르카나 22종 일러스트 + 하단 라벨

### 6.7 맞춤 해석 결과 카드 (F-4 결과 프레임 — 1080×1350 캡처 영역)
* **배경:** `bg-white` (양피지 캔버스 위 깔끔한 흰색 카드 레이어)
* **테두리:** `border border-[#e3e3e2] rounded-2xl p-6`
* **헤더:** `{이름}님의 타로 · {주제}` (14px 라벨)
* **카드 아트:** 중앙 정렬된 고화질 카드 이미지 (`w-36 rounded-lg shadow-sm`)
* **카드 타이틀 & 별자리:** `XIX 태양 · ♌ 사자자리` (18px SemiBold)
* **맞춤 해석 문장 (3줄 · 90자 이내):**
  * `1줄 (카드×주제):` "지민님, 준비한 것을 드러낼 때예요."
  * `2줄 (별자리):` "사자자리의 자신감이 오늘은 무기가 돼요."
  * `3줄 (전공):` "경영학도다운 기획력이 빛나는 날이에요." (입력 시)
  * 서체 스타일: `text-[15px] leading-relaxed text-[#292827] break-keep-all`
* **푸터:** `※ 오락용 타로 해석입니다` (11px Stone Gray) + `🔮 오늘의 타로` 로고 워터마크

### 6.8 피드백 토스트 & 모달 (Toaster & Fallback Dialog)
* **토스트 (Toast):**
  * "이미지를 저장했어요" / "결과를 복사했어요. 원하는 앱에 붙여 넣어 주세요"
  * `bg-[#292827] text-white text-sm rounded-full px-4 py-2.5 shadow-lg`
* **저장/복사 실패 시 모달 (Fallback):**
  * 인앱 브라우저 제한 시 이미지를 화면에 띄우고 *"이미지를 길게 눌러 저장해 주세요"* 안내 레이어 노출

---

## 7. 화면별 UI 와이어프레임 구조 (Screens)

```
[S-01 시작 화면]
┌───────────────────────────┐
│        🔮 오늘의 타로       │  <- display (32px, Ink Charcoal)
│                           │
│     ┌───────────────┐     │
│     │   카드 뒷면   │     │  <- 타로 카드 뒷면 그래픽
│     │   미스틱 패턴 │     │
│     └───────────────┘     │
│                           │
│   내 정보를 넣고 카드 한 장으로   │  <- body-md (15px)
│   나만의 해석을 받아 봐요     │
│                           │
│   [       타로 시작       ]  │  <- Primary CTA (Midnight Wine, 52px)
│                           │
│   ※ 오락용 타로 · 정보는 저장 안 해요│  <- caption (12px, Stone Gray)
└───────────────────────────┘

[S-02 내 정보 & 주제 선택]
┌───────────────────────────┐
│ ←  나에 대해 알려 주세요        │  <- Header with back arrow
│                           │
│ 이름 (닉네임 OK)            │  <- FieldLabel
│ [ 지민                    ]│  <- Input (48px, rounded-xl)
│                           │
│ 생년월일                   │
│ [ 2004 . 08 . 03          ]│  <- Date Input
│                           │
│ 전공 (선택)                │
│ [ 경영학과                ]│  <- Optional Input
│                           │
│ 어떤 주제가 궁금한가요?       │
│ ┌───────┬───────┬───────┐ │
│ │💼커리어│💰재물 │💕연애 │ │  <- ToggleGroup (2x3 Grid)
│ ├───────┼───────┼───────┤ │
│ │🌿건강 │📚학업 │✨종합 │ │
│ └───────┴───────┴───────┘ │
│                           │
│ 🔒 입력한 정보는 해석에만 쓰고│  <- Privacy Callout Alert
│ 저장하지 않아요. 즉시 폐기됩니다.│
│                           │
│ [    카드 한 장 뽑기    ]    │  <- Primary CTA (Active when valid)
└───────────────────────────┘

[S-03 맞춤 해석 결과 화면]
┌───────────────────────────┐
│ ┌───────────────────────┐ │  <- [저장 영역: 1080x1350 카드]
│ │ 지민님의 타로 · 커리어    │ │  <- text-sm text-[#714cb6] font-medium
│ │       ┌───────┐       │ │
│ │       │카드그림│       │ │  <- 뒤집기 애니메이션 완료
│ │       └───────┘       │ │
│ │   XIX 태양 · ♌ 사자자리   │ │  <- heading-sm (18px SemiBold)
│ │                       │ │
│ │ 준비한 것을 드러낼 때예요.    │ │  <- 맞춤 해석 3줄 (body-lg)
│ │ 사자자리의 자신감이 무기가 돼요│ │
│ │ 경영학도다운 기획력이 빛나요. │ │
│ │                       │ │
│ │ ※ 오락용 타로 해석입니다   │ │  <- caption
│ └───────────────────────┘ │
│                           │
│ [ 이미지 저장 ] [ 결과 공유 ] │  <- Secondary Action Buttons
│    [ 다시 뽑기 ]  [ 처음으로 ] │  <- Ghost Actions
│                           │
│ 🔒 정보는 저장되지 않아요.     │  <- Privacy note
└───────────────────────────┘
```

---

## 8. Do's and Don'ts

### Do
- **양피지 캔버스 유지:** 배경에는 항상 `#f2f0eb`를 적용하고, 카드가 떠오르는 부분에만 `#ffffff`를 사용합니다.
- **Midnight Wine CTA:** 가장 중요한 단일 버튼(시작하기, 카드뽑기)에만 `#421d24`를 사용해 무게감을 줍니다.
- **한글 줄바꿈 보호:** 모든 문장에 `break-keep-all`을 주어 모바일에서 조사가 다음 줄로 어색하게 넘어가지 않도록 합니다.
- **헤어라인 테두리:** 깊이감은 무거운 그림자가 아닌 1px `#e3e3e2` 보더와 미세한 톤 차이로 구현합니다.
- **개인정보 투명성:** 입력 단계와 결과 단계 모두에서 개인정보가 서버로 전송되지 않는다는 사실을 눈에 띄게 안내합니다.

### Don't
- **순수 검정/원색 금지:** `#000000` 대신 따뜻한 먹색(`#292827`)을 사용하며, 형광 톤의 원색을 쓰지 않습니다.
- **헤비 섀도우 지양:** 모바일 카드에 둔탁하고 짙은 검은색 그림자를 중첩하지 않습니다.
- **두꺼운 헤드라인 지양:** 700(Bold) 이상의 헤비 폰트 대신 460~540의 정제된 굵기를 사용합니다.
- **결과 링크에 개인정보 노출 금지:** 공유하기 링크는 무조건 서비스 시작 화면(`S-01`) URL이어야 하며 파라미터에 이름/생년월일을 담지 않습니다.

---

## 9. Tailwind v4 & CSS Variables 설정 코드

### `src/index.css` (또는 메인 CSS 파일)

```css
@import "tailwindcss";

@layer base {
  :root {
    /* Palette Tokens */
    --color-midnight-wine: #421d24;
    --color-royal-violet: #714cb6;
    --color-lilac-mist: #d4c7ff;
    --color-deep-lagoon: #0c4243;
    --color-warm-parchment: #f2f0eb;
    --color-soft-mist: #e3e3e2;
    --color-ink-charcoal: #292827;
    --color-stone-gray: #666666;
    --color-paper-white: #ffffff;

    /* shadcn Semantic Tokens */
    --background: var(--color-warm-parchment);
    --foreground: var(--color-ink-charcoal);
    --card: var(--color-paper-white);
    --card-foreground: var(--color-ink-charcoal);
    --popover: var(--color-paper-white);
    --popover-foreground: var(--color-ink-charcoal);
    --primary: var(--color-midnight-wine);
    --primary-foreground: #ffffff;
    --secondary: var(--color-lilac-mist);
    --secondary-foreground: var(--color-ink-charcoal);
    --muted: #e9e6df;
    --muted-foreground: var(--color-stone-gray);
    --accent: var(--color-lilac-mist);
    --accent-foreground: var(--color-royal-violet);
    --destructive: #b91c1c;
    --destructive-foreground: #ffffff;
    --border: var(--color-soft-mist);
    --input: var(--color-soft-mist);
    --ring: var(--color-royal-violet);

    /* Radii */
    --radius-sm: 8px;
    --radius-md: 12px;
    --radius-lg: 16px;
    --radius-xl: 20px;
    --radius-full: 9999px;
  }
}

@theme inline {
  --color-midnight-wine: var(--color-midnight-wine);
  --color-royal-violet: var(--color-royal-violet);
  --color-lilac-mist: var(--color-lilac-mist);
  --color-deep-lagoon: var(--color-deep-lagoon);
  --color-warm-parchment: var(--color-warm-parchment);
  --color-soft-mist: var(--color-soft-mist);
  --color-ink-charcoal: var(--color-ink-charcoal);
  --color-stone-gray: var(--color-stone-gray);
  --color-paper-white: var(--color-paper-white);

  --font-sans: "Pretendard Variable", Pretendard, Inter, system-ui, sans-serif;
}
```
