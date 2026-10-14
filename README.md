# 오늘뭐먹지

냉장고 관리 + 레시피 저장 + 지금 만들 수 있는 요리 추천 PWA (나만 쓰는 용도).

## 파일
- `index.html` — 앱 전체 (HTML/CSS/JS 한 파일)
- `manifest.json` — 홈 화면 앱 설정
- `sw.js` — 오프라인 지원 (네트워크 우선, 오프라인이면 캐시)
- `icon-180.png`, `icon-192.png`, `icon-512.png` — 아이콘

데이터는 아이폰 Safari의 IndexedDB에만 저장돼요. 서버 없음.

## GitHub Pages로 배포
1. GitHub에서 새 저장소 만들기 (예: `ohneul`). 비공개 저장소는 Pages가 유료 플랜에서만 되니 공개로 만들면 돼요. 주소만 안 알려주면 나만 씁니다.
2. 이 폴더의 파일을 전부 올리기
   ```bash
   git init && git add . && git commit -m "first version"
   git branch -M main
   git remote add origin https://github.com/<아이디>/ohneul.git
   git push -u origin main
   ```
3. 저장소 Settings → Pages → Source: `Deploy from a branch`, Branch: `main` / `(root)` → Save
4. 1~2분 뒤 `https://<아이디>.github.io/ohneul/` 접속 확인

## 아이폰에 설치
1. Safari로 위 주소 열기 (Chrome 말고 Safari)
2. 공유 버튼 → "홈 화면에 추가"
3. 홈 화면 아이콘으로 열면 주소창 없이 앱처럼 열림

## 업데이트
파일 고쳐서 `git push` 하면 끝. 앱을 껐다 켜면 최신 버전으로 열려요.
(캐시 문제로 안 바뀌면 `sw.js`의 `CACHE = 'ohneul-v1'` 숫자를 올리기)

## 백업
설정 → 내보내기로 JSON 파일 저장 (파일 앱/iCloud). 폰 바꿀 때 가져오기.

## 다음 단계 (AI)
- 텍스트 붙여넣기 → AI가 레시피 정리 (서버 + API 키 필요: Cloudflare Workers 등)
- 화면 녹화 영상 업로드 → 프레임/음성 분석
- iOS 단축어로 릴스 공유 버튼에서 바로 저장
