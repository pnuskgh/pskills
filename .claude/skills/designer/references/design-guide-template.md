# design-guide.md 작성 가이드

`design-guide.md`를 새로 만들 때 이 구조를 뼈대로 쓴다. 프로젝트에 해당 없는 섹션은 빼고, 필요한
섹션은 자유롭게 추가한다 — 아래는 빠뜨리기 쉬운 항목을 놓치지 않기 위한 체크리스트지, 고정 양식이
아니다. 값은 실제로 코드/설정 파일(예: `tailwind.config`, 설치된 패키지)에서 확인한 것을 쓴다 —
추측해서 채우지 않는다.

## UI/UX Design Rules 예시

```md
## UI/UX Design Rules

### 기본
- UI Library: Tailwind CSS + Shadcn/UI
- Icon Library: Lucide-react
- Font: Inter (or System Sans-serif)

### 컬러
- Brand: primary #4F46E5, secondary #06B6D4
- Neutral: Tailwind gray 스케일 그대로 사용 (gray-50 ~ gray-900)
- 상태색: success emerald-500 / warning amber-500 / danger red-500 / info sky-500
- Dark mode: 지원함 — `dark:` variant, 토글은 localStorage에 저장

### 타이포그래피
- 크기 스케일: text-xs ~ text-4xl (Tailwind 기본값 그대로)
- 제목 굵기: font-semibold, 본문: font-normal
- 줄간격: leading-relaxed 기본

### 스페이싱
- Scale: Tailwind 기본(4px 배수)
- 섹션 간 간격: 최소 py-12 이상
- 컨테이너 최대폭: max-w-5xl, 좌우 padding px-4

### 컴포넌트 스타일
- Card: rounded-xl(12px), shadow-sm
- Button: rounded-md, hover 전환 200ms, disabled는 opacity-50
- Input: border-gray-300, focus:ring-2 focus:ring-primary

### 반응형 브레이크포인트
- Tailwind 기본(sm 640 / md 768 / lg 1024 / xl 1280) 그대로 사용
- 모바일: 1열, md 이상: 2~3열 그리드로 전환하는 패턴을 기본으로 삼음

### 접근성
- 텍스트 대비 WCAG AA(4.5:1) 이상
- 포커스 링: ring-2 ring-offset-2 (outline 제거 금지)

### 모션
- 기본 트랜지션: 150~200ms, ease-in-out
- 화려한 애니메이션은 요청 없이 추가하지 않음

### 컴포넌트 위치/네이밍
- 재사용 컴포넌트: `src/components/ui/`
- 화면 단위: `src/pages/` 또는 `src/features/<feature>/pages/`
- 파일명: PascalCase 컴포넌트명과 동일
```

## 작성 시 주의

- **실제로 설치/설정된 값만 적는다** — `package.json`, `tailwind.config.*`, 이미 만들어진 컴포넌트를
  실제로 열어서 확인한 값을 옮긴다. 이상적인 값을 지어내지 않는다.
- **예시가 없는 프로젝트(그린필드)라면** SKILL.md 본문의 "기존 관례부터 읽는다 — 없으면 만든다"
  절차대로 먼저 최소 토큰(색상 1~2개 + 중립 그레이 + 4px spacing scale)을 정하고, 그 결정을 그대로
  이 파일의 초안으로 옮겨 적는다 — 빈 파일로 시작하거나 갑자기 방대한 표를 만들지 않는다.
- **모노레포에서 프론트엔드 앱이 여러 개면** 앱마다 서로 다른 UI 라이브러리/스타일을 쓸 수 있으므로,
  `design-guide.md`도 각 앱 루트(그 앱의 `package.json`이 있는 위치)에 따로 둔다.
- **Font를 적기 전에 주요 사용자 언어의 문자를 실제로 지원하는지 확인한다** — UI 킷 프리셋 기본 폰트는
  대개 라틴 전용이다. 예를 들어 한국어 사용자가 주력이면 Pretendard처럼 한글을 포함하는 폰트로 바꾼다
  (SKILL.md 본문 "판단 순서 5번" 참고).
