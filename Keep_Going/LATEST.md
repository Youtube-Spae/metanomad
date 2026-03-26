# MetaNomad — 작업 상태
- 최종 업데이트: 2026-03-26 (야간)
- 작업 폴더: D:\projects\metanomad

## ✅ 완료 항목
- [x] Vercel-GitHub 연결 복구 (Youtube-Spae/metanomad)
- [x] Gemini API 키 갱신 (VITE_API_KEY), Claude API 키 추가 (VITE_CLAUDE_API_KEY)
- [x] 전체 파이프라인 작동 확인 (10씬, 약 16분)
- [x] alert 팝업 → 상단 배너로 전면 교체 (App.tsx + StageInspiration.tsx)
- [x] isFatal 체크 문자열 버그 수정 (claudeService.ts)
- [x] TTS voice 성별 분기: 여성→kore, 남성→charon (252c19e)
- [x] TTS Rate Limit 재시도: 3회 retry + 2초 딜레이 (252c19e)
- [x] 이미지 프롬프트 순서: claudeService.ts 순차처리 이미 완료
- [x] syncSpeakers localStorage 버그 수정 — sessionStorage→localStorage (9aec5f8)
  → Noah 등 남성 캐릭터 성별 감지 실패 원인 해결
- [x] TTS 429 에러 감지 → 5초 대기 강화 (기존 2초) (9aec5f8)

## 🔴 미완료 (다음 세션 시작점)
- [ ] Noah(남성) Charon voice 적용 확인 — F12 콘솔에서 "syncSpeakers: Noah(male) → charon" 확인
- [ ] TTS 배치 실행 → 씬 4,8,9 Rate Limit 실패 재현 여부 확인 (9aec5f8 적용 후)
- [ ] 새 스토리보드 생성 → 나레이션 560~620자 정상 생성 확인 (10씬 기준)
- [ ] TTS 배치 실행 → 씬당 85~94초 범위 달성 확인
- [ ] error_check/checklist.md #15~#17 — CharacterManager.tsx
- [ ] error_check/checklist.md #18~#27 — StageFinalization, geminiService, tsconfig

## 앱 실행 방법
```powershell
cd D:\projects\metanomad
npm run dev
# 브라우저 → localhost:3000
```

## 다음 세션 시작 프롬프트
```
D:\projects\metanomad\Keep_Going\LATEST.md 읽어줘.
미완료 항목 확인 후 우선순위대로 수정 시작해줘.
작업 폴더: D:\projects\metanomad, C: 드라이브 절대 금지.
```