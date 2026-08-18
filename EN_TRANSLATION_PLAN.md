# ainmath.com 영어 번역 로드맵

278개 페이지(체험 152 + 설명글article 126)를 학년/카테고리 단위로 나눠 순차 진행한다.
아래 "Stage N"을 그대로 다음 요청에 붙여넣으면 그 범위만 작업한다. 학년 구분은
`curriculum-map.html`의 `GRADES` 배열(2022 개정 교육과정 기준)을 그대로 따른다.

## 매 단계 공통 작업 방식 (2026-08-17 Stage 0에서 확립한 패턴)

1. **파일 목록 재확인**: 아래 목록은 curriculum-map.html에서 뽑은 것이지만 그 파일 자체가
   최신이 아닐 수 있다(예: `article-water-jug-puzzle.html`, `article-geoboard-area.html`은
   실제로 존재하는데도 curriculum-map.html엔 링크가 안 걸려 있었음). 각 파일 작업 전
   `ls article-<name>.html`로 실제 존재 여부를 다시 확인할 것.
2. **체험 페이지(en/<name>.html) 번역**: 한국어 원본을 그대로 읽어 CSS/디자인 시스템(Do Hyeon·
   Gowun Dodum 폰트, paper/violet/coral/green/blue 색상 토큰), JS 로직(퀴즈 랜덤화, 캔버스/SVG
   렌더링, 사운드 피드백)을 100% 유지한 채 텍스트만 번역해 새로 작성한다.
   - `speechSynthesis` lang은 `en-US`로.
   - localStorage 퀴즈 기록 키(`QUIZ_KEY='ainmath_quiz_v1'`, `QUIZ_ID`)는 한국어판과 **동일하게
     재사용** — 같은 활동이면 언어와 무관하게 최고기록을 공유한다.
   - GA4 스니펫(G-MTLD2D08XH)은 그대로 복사.
   - SEO 메타(title/description/og:*/twitter:*)는 영어로, `og:locale`은 `en_US`, `og:url`은
     `https://ainmath.com/en/<name>.html`.
   - 상단 "← 전체 목록으로" 링크는 해당 학년의 EN 허브 페이지로 교체 (예: `elementary.html`,
     `grade-3-4.html` 등 — 없으면 이번 단계에서 새로 만든다. 아래 "학년 허브 페이지" 참고).
   - "📖 설명 글 읽기" 버튼은 그 설명글이 이미 en/에 번역되어 있을 때만 유지하고, 없으면 이번
     단계에서 설명글도 같이 번역하거나(권장) 버튼을 생략한다.
   - 하단 이전/다음 탐구 내비게이션은 **이번 단계에서 번역하는 페이지들끼리만** 체인으로 연결한다
     (전체 사이트 순서를 억지로 따라가지 않는다).
3. **설명글(en/article-<name>.html) 번역**: 원본 article-*.html의 구조(.back-link, .card,
   .article-body, footer, cta 등)를 유지한 채 본문을 자연스러운 영어로 번역. SEO 메타/GA4 동일 규칙.
4. **학년 허브 페이지**: `en/elementary.html`(초 1~2용으로 이미 있음)과 같은 패턴으로 학년별 허브를
   새로 만든다. `en/index.html`에서 진행된 학년으로 가는 링크를 추가한다.
5. **KO 원본 쪽 스위처 갱신**: 이번 단계에서 번역한 파일들의 한국어 원본에는 이미 사이트 전역에 깔린
   `EN` 알약 링크가 `en/index.html`로 뭉뚱그려 걸려 있다. 해당 파일들만 골라 그 링크를
   `en/<name>.html`(또는 `en/article-<name>.html`)로 구체적으로 바꿔준다.
6. **중복 파일 처리**: 같은 체험/설명글이 여러 학년에 걸쳐 등장하는 경우(예: `mean-median-mode.html`은
   초5~6, 중1, 고2에 모두 나옴), 처음 번역한 단계에서 완료된 것으로 보고 이후 단계는 그 학년 허브
   페이지에 링크만 걸고 재번역하지 않는다. 아래 목록에서 "(중복, 이미 있으면 스킵)"으로 표시.
7. **마무리 체크**: `grep -l '[가-힣]' en/새파일들` 로 의도치 않은 한국어 잔존 텍스트 없는지 확인,
   `git status`/`git diff` 스팟체크, **커밋은 하지 않음** (사용자가 검토 후 직접 커밋).

---

## Stage 0 — 인프라 + 초 1~2학년군 (완료, 2026-08-17)

사이트 전역 EN 스위처 알약, `en/index.html`, `en/elementary.html`, 체험 9개(make-ten,
multiplication-array, pattern-finder, shape-finder, solid-shape-families, comparison-basics,
clock-reading, classify-objects, pictogram-graph) 완료.

## Stage 1 — 초 1~2학년군 마무리 (완료, 2026-08-18)

설명글 9개(article-make-ten, article-multiplication-array, article-pattern-finder,
article-shape-finder, article-solid-shape-families, article-comparison-basics,
article-clock-reading, article-classify-objects, article-pictogram-graph) 번역 완료, Stage 0의
9개 EN 체험 페이지에 "📖 Read the article" 버튼 연결 완료.

## Stage 2 — 초등학교 3~4학년군 (완료, 2026-08-18)

체험 12개 + 설명글 12개(place-value-blocks, mixed-multiplication-division, fraction-compare,
equal-sign-balance, lines-angles-basics, shape-classify, polygon-name-quiz, coordinate-transform,
time-calculator, measurement-estimate, protractor-measure, bar-line-graph + 각각의 article-*) 전부
번역 완료. `en/grade-3-4.html` 허브 신규 작성, `en/index.html`/`en/elementary.html`에서 링크 연결,
관련 KO 원본 33개 파일의 EN 스위처 알약을 구체적 링크로 갱신 완료.

## Stage 3 — 초등학교 5~6학년군 (체험 23 + 설명글 ~21)

mixed-calculation, number-range-rounding, gcd-lcm, divisor-finder, water-jug-puzzle(설명글 있음,
curriculum-map엔 안 걸려 있으니 확인), fraction-simplify, corresponding-quantities, ratio-proportion,
proportion-equation, symmetry-shapes, cuboid-parts, prism-pyramid, cylinder-cone-sphere,
unit-cube-count, geoboard-area(설명글 있음, 위와 동일), triangle-base-height, pi-circumference,
circle-area, cuboid-surface-volume, cube-net-lab, mean-median-mode, coin-dice-simulator, pie-chart
(+ 각각의 article-*, article-divisors.html은 divisor-finder 것).
→ `en/grade-5-6.html` 허브 신규 작성.

## Stage 4 — 중학교 1학년 (체험 16 + 설명글 ~15)

prime-sieve, prime-factor-tree, exponent-notation, integer-number-line, integer-sign-rules,
equation-balance, proportion-inverse, parallel-angles, congruence-conditions, polygon-angle-sum,
exterior-angle-sum, cylinder-cone-volume, solid-cross-sections-lab, frequency-table,
relative-frequency, **mean-median-mode(중복, Stage 3에서 이미 했으면 스킵)**.
→ `en/middle-1.html` 허브 신규 작성.

## Stage 5 — 중학교 2학년 (체험 11 + 설명글 ~10)

repeating-decimal, repeating-decimals-lab(설명글 없음), monomial-calculation,
inequality-and-system, linear-function-graph(→ 설명글 파일명은 `article-linear-function.html`,
이름 다름 주의), triangle-quadrilateral-properties, similarity-congruence, pythagorean-theorem,
distance-formula, permutations-combinations, **coin-dice-simulator(중복, 스킵 가능)**.
→ `en/middle-2.html` 허브 신규 작성.

## Stage 6 — 중학교 3학년 (체험 6 + 설명글 6)

square-root, factoring-quadratic, quadratic-function-graph(→ 설명글 `article-quadratic-function.html`,
이름 다름 주의), trig-ratios, inscribed-angle, boxplot-scatter.
→ `en/middle-3.html` 허브 신규 작성.

## Stage 7 — 고등학교 1학년 (체험 9, 신규 4 + 설명글 해당분)

polynomial, sets-propositions, imaginary-complex-numbers-lab(설명글 없음), line-equation,
counting-principle 가 신규. **factoring-quadratic / linear-function-graph / quadratic-function-graph
/ coordinate-transform 은 중복 — 이미 했으면 스킵, 안 했으면 이번에 같이.**
→ `en/high-1.html` 허브 신규 작성.

## Stage 8 — 고등학교 2학년 (체험 19, 신규 17 + 설명글 해당분)

exp-log-function, log-properties, fibonacci-spiral, pascal-triangle(→ 설명글
`article-pascals-triangle.html`, 이름 다름 주의), sequences, sequence-limits, unit-circle,
trig-function-graphs, limits-continuity, derivative, derivative-applications, integral,
probability-complement, conditional-probability, standard-deviation, correlation-regression가 신규.
**coin-dice-simulator / permutations-combinations / mean-median-mode 는 중복 — 스킵 가능.**
→ `en/high-2.html` 허브 신규 작성.

## Stage 9 — 고등학교 3학년 (체험 7, 신규 6 + 설명글 해당분)

derivative-rules, parametric-implicit-derivative, integration-techniques, integration-methods,
space-coordinates, vectors가 신규. **solid-cross-sections-lab 중복 — 스킵 가능.**
→ `en/high-3.html` 허브 신규 작성.

## Stage 10 — "쉬는 시간" 보너스 퍼즐/실험실 모음 (체험 42, 설명글 있는 것 25)

학년에 안 묶이는 재미 콘텐츠. curriculum-map.html의 `EXPLORE` 배열 참고.
설명글 있음(25): pascal-triangle(중복), fibonacci-spiral(중복), sequences(중복), tessellation,
magic-square, hanoi-tower, game-24, four-fours, mini-sudoku, tangram-puzzle, number-baseball,
number-detective, speed-math-challenge, platonic-solids-lab, fibonacci-in-nature,
finger-multiplication-trick, fractal-explorer, mathematician-stories, spirograph, number-bases,
monty-hall, nim-game, optical-illusion, mobius-klein, sphere-volume-proof.
설명글 없음(17, 체험만): circle-roll-locus, birthday-paradox-lab, collatz-conjecture-lab,
curious-digit-numbers-lab, divisor-chain-numbers, elliptic-curve-crypto-lab,
huge-numbers-infinity-lab, number-properties-lab, prime-mysteries-lab, rsa-encryption-lab,
special-numbers-lab, zeno-paradox-lab, monte-carlo-pi-lab, catalan-numbers-lab, game-of-life-lab,
konigsberg-bridges-lab, simpsons-paradox-lab.
→ `en/explore.html` (또는 `en/playground.html`) 허브 신규 작성. 분량이 크니 필요하면 이 Stage를
   다시 여러 번에 나눠 요청해도 됨.

## Stage 11 — 사이트 공통 페이지

about.html, contact.html, terms.html, privacy-policy.html + `explore.html`(전체 목록 페이지)과
`curriculum-map.html` 자체의 영어판. 이 시점이면 en/ 쪽 콘텐츠가 충분히 쌓여 있으므로 전체 목록/교과
과정 지도 페이지도 의미가 생김. 그전에는 만들어봐야 텅 빈 리스트라 우선순위 낮음.

---

## 진행 상황 확인

`ls en/*.html`로 지금까지 번역된 파일을 확인하고, 위 Stage 목록과 대조해서 다음 단계를 고른다.
