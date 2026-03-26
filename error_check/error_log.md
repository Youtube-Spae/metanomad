# MetaNomad 에러 로그

> 분석 일자: 2026-03-23
> 분석 범위: 전체 파일 (tsx, ts, jsx, js, json)

---

## 높음 (즉시 수정 권장)

| # | 파일명 | 라인 | 에러 내용 |
|---|--------|------|-----------|
| 1 | `claudeService.ts` | 4 | API_KEY 미설정 시 빈 문자열 폴백 → 401 에러 발생, 사용자 혼동 유발 |
| 2 | `claudeService.ts` | 447-450 | JSON 파싱 실패 시 빈 배열 반환 → 공백 씬 생성 가능 |
| 3 | `StageMultimedia.tsx` | 59-60 | sessionStorage 결과 null 체크 없이 JSON.parse → 파싱 에러 |
| 4 | `StageInspiration.tsx` | 135 | allCharacters undefined 시 .some() 호출 → 런타임 에러 |
| 5 | `StageStoryboard.tsx` | 286 | dangerouslySetInnerHTML 사용 → XSS 취약점 가능성 |

---

## 중간 (가능하면 수정)

| # | 파일명 | 라인 | 에러 내용 |
|---|--------|------|-----------|
| 6 | `App.tsx` | 115 | `catch (error: any)` — any 타입 사용, 타입 안전성 상실 |
| 7 | `App.tsx` | 89 | generateStoryArc 응답 구조 변경 시 호환성 문제 가능 |
| 8 | `claudeService.ts` | 31-32, 75-76 | 에러 메시지에 민감한 정보 노출 위험 |
| 9 | `claudeService.ts` | 104 | `catch (_) {}` — 에러 무시, 이미지 분석 실패 시 무음 처리 |
| 10 | `claudeService.ts` | 119 | JSON.parse 실패 처리 없음, undefined 반환 가능 |
| 11 | `claudeService.ts` | 321 | 에러 메시지에 응답 300글자 노출 → 프롬프트 인젝션 위험 |
| 12 | `claudeService.ts` | 434 | non-null assertion(`!`) 사용, 배열 길이 검증 필요 |
| 13 | `claudeService.ts` | 478-481 | 최대 재시도 후 빈 나레이션 반환 시 UI에서 감지 안 됨 |
| 14 | `claudeService.ts` | 577-579 | 에러 throw 후 fallback 반환으로 실패 이유 불명확 |
| 15 | `characterManager.tsx` | 108 | `canvas.getContext('2d')!` — null 반환 가능성 있음 |
| 16 | `characterManager.tsx` | 122 | img.src → onload 순서 race condition 가능 |
| 17 | `characterManager.tsx` | 189 | `ev.target?.result as string` — 타입 단언, result가 string 아닐 수 있음 |
| 18 | `StageInspiration.tsx` | 109-110 | localStorage JSON.parse에 try-catch 없음 |
| 19 | `StageInspiration.tsx` | 362, 376 | `catch (e) {}` — localStorage 에러 무시 |
| 20 | `StageMultimedia.tsx` | 76 | selectionMode 초기값 불일치 가능 |
| 21 | `StageMultimedia.tsx` | 202 | allPcmBytes 빈 배열 체크 후 throw하지만 buffer 사용 가능 |
| 22 | `StageFinalization.tsx` | 75-79 | item.vibes 배열 여부 미검증 시 .forEach() 에러 |
| 23 | `StageStoryboard.tsx` | 293 | scenes.find() 실패 시 null, 이미지 프롬프트 체크 필요 |
| 24 | `geminiService.ts` | 37 | 응답 파싱 실패 시 공백 배열 반환 |
| 25 | `geminiService.ts` | 422 | API 에러와 빈 씬 에러 구분 안 됨 |
| 26 | `types.ts` | 32 | placeName이 optional이지만 필수 필드로 실제 사용됨 |
| 27 | `tsconfig.json` | - | noImplicitAny, strict 미설정 → 암묵적 any 허용 |

---

## 낮음 (참고용)

| # | 파일명 | 라인 | 에러 내용 |
|---|--------|------|-----------|
| 28 | `App.tsx` | 23 | abortControllerRef 선언만 되고 미사용 |
| 29 | `claudeService.ts` | 578 | 에러 발생 시 제네릭 fallback 반환, 사용자가 실패 이유 모름 |
| 30 | `characterManager.tsx` | 195 | catch 블록에서 에러 객체 무시 |
| 31 | `StageInspiration.tsx` | 193 | 불안정한 정렬 알고리즘 (Fisher-Yates shuffle 권장) |
| 32 | `StageMultimedia.tsx` | 343 | CSV 생성 시 BOM 없음 → Excel 한글 깨짐 위험 |
| 33 | `StageFinalization.tsx` | 41-43 | storage 접근 후 JSON.parse (try-catch로 보호는 됨) |
| 34 | `Navbar.tsx` | 28-29 | window.aistudio 타입 선언 부족 |
| 35 | `index.tsx` | 7-8 | rootElement null 체크 방식 개선 여지 있음 |
| 36 | `package.json` | - | Anthropic SDK 미사용, claudeService.ts에서 직접 fetch 호출 |
