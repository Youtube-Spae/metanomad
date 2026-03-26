# MetaNomad 에러 수정 체크리스트

> 최초 작성: 2026-03-23
> 수정 완료 시 `[ ]` → `[x]` 로 변경

---

## 🔴 높음 — 즉시 수정

- [x] **#1** `claudeService.ts:4` — API_KEY 미설정 방어 코드 추가 (에러 메시지 명확화)
- [x] **#2** `claudeService.ts:447-450` — JSON 파싱 실패 시 빈 배열 대신 명시적 에러 throw
- [x] **#3** `StageMultimedia.tsx:59-60` — sessionStorage null 체크 후 JSON.parse
- [x] **#4** `StageInspiration.tsx:135` — allCharacters undefined 가드 추가
- [x] **#5** `StageStoryboard.tsx:286` — dangerouslySetInnerHTML 제거 또는 sanitize 처리

---

## 🟡 중간 — 가능하면 수정

- [x] **#6** `App.tsx:115` — `any` 타입 제거, 구체적 에러 타입 정의
- [x] **#7** `App.tsx:89` — generateStoryArc 응답 구조 타입 검증 강화
- [x] **#8** `claudeService.ts:31-32,75-76` — 에러 응답에서 민감 정보 제거
- [x] **#9** `claudeService.ts:104` — catch 블록에 에러 로깅 추가
- [x] **#10** `claudeService.ts:119` — JSON.parse try-catch 추가
- [x] **#11** `claudeService.ts:321` — 에러 메시지에서 응답 내용 제거
- [x] **#12** `claudeService.ts:434` — non-null assertion 제거, 배열 길이 검증
- [x] **#13** `claudeService.ts:478-481` — 빈 나레이션 반환 시 UI 알림 처리
- [x] **#14** `claudeService.ts:577-579` — 에러 구분 명확화
- [ ] **#15** `characterManager.tsx:108` — canvas.getContext null 체크
- [ ] **#16** `characterManager.tsx:122` — img onload → src 순서 수정
- [ ] **#17** `characterManager.tsx:189` — 타입 단언 제거, instanceof 체크
- [ ] **#18** `StageInspiration.tsx:109-110` — localStorage JSON.parse try-catch 추가
- [ ] **#19** `StageInspiration.tsx:362,376` — catch 블록 에러 로깅 추가
- [ ] **#20** `StageMultimedia.tsx:76` — selectionMode 초기값 일관성 확인
- [ ] **#21** `StageMultimedia.tsx:202` — allPcmBytes 처리 로직 검토
- [ ] **#22** `StageFinalization.tsx:75-79` — item.vibes 배열 여부 검증 추가
- [ ] **#23** `StageStoryboard.tsx:293` — scenes.find() 실패 케이스 처리
- [ ] **#24** `geminiService.ts:37` — 파싱 실패 시 명시적 에러 처리
- [ ] **#25** `geminiService.ts:422` — 에러 유형 구분 처리
- [ ] **#26** `types.ts:32` — placeName optional → required 변경 검토
- [ ] **#27** `tsconfig.json` — strict: true, noImplicitAny: true 활성화

---

## 🟢 낮음 — 참고용

- [ ] **#28** `App.tsx:23` — 미사용 abortControllerRef 제거 또는 구현
- [ ] **#29** `claudeService.ts:578` — fallback 반환 시 원인 로깅
- [ ] **#30** `characterManager.tsx:195` — catch 블록 에러 로깅
- [ ] **#31** `StageInspiration.tsx:193` — Fisher-Yates shuffle로 교체
- [ ] **#32** `StageMultimedia.tsx:343` — CSV BOM 추가 (한글 Excel 호환)
- [ ] **#33** `StageFinalization.tsx:41-43` — storage 접근 안전성 재확인
- [ ] **#34** `Navbar.tsx:28-29` — window 타입 선언 추가
- [ ] **#35** `index.tsx:7-8` — 조건부 마운트 방식으로 개선
- [ ] **#36** `package.json` — Anthropic SDK 도입 검토

---

## 수정 이력

| 날짜 | 항목 | 수정 내용 | 담당 |
|------|------|-----------|------|
| 2026-03-26 | #1~#5 | 🔴 높음 5개 수정 완료 | Claude |
| 2026-03-26 | #6~#14 | 🟡 중간 claudeService 관련 9개 수정 완료 | Claude |
