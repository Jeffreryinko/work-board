# 작업 현황판 (work-board)

여러 채팅에 맡긴 일이 어디까지 왔는지 폰에서 한눈에 보는 개인 웹앱. 홈 화면에 설치할 수 있고(PWA), 채팅이 일을 끝내거나 답이 필요하면 알림이 온다.

- 주소: https://jeffreryinko.github.io/work-board/
- 기록: Supabase(vendingforme 프로젝트) `public.work_log`. 허용된 구글 계정만 읽음(`think_is_owner`).
- 채팅이 남기는 법: `select public.work_post('채팅 이름', '진행'|'완료'|'질문'|'막힘', '한 줄', '자세히', '링크');` — '진행'은 알림 없음.
- 알림: 새 줄이 들어오면 트리거 `work_log_notify` → `planner_private.dispatch`(자판기·플래너와 같은 발송기). 구독은 `work_push_subs`.
- 화면: 첫 탭 '한눈에'(답 필요·진행 중·최근 끝남), 칸마다 최대 20개. 3시간 넘게 소식 없는 진행은 '소식 없음'.
