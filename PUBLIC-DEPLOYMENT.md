# 공간의 참여 — 무료 공개 배포

공개 주소: https://hdongeun.github.io/participation-archive/

공개 저장소: https://github.com/hdongeun/participation-archive

GitHub Pages는 GitHub Free의 공개 저장소에서 사용할 수 있는 정적 호스팅이다. 방문자는 로그인할 필요가 없다. 개인 도메인을 사지 않아도 기본 github.io 주소로 운영할 수 있다. 다른 선택지는 Cloudflare Pages의 무료 정적 호스팅이며 Direct Upload에는 GitHub 연결 없이 Cloudflare 계정을 사용할 수 있다.

## 공개되는 내용

지도, 조건 필터, 비교, 사례 25건의 개별 HTML, 후보·출처 목록, JSON/CSV 내보내기. 공개 데이터 파일로 다시 빌드하는 방식이며, 비공개 수집·검토 서버와 데이터베이스를 포함하지 않는다. 원사진과 위성영상의 저작권은 원출처에 있으며 재이용 권한을 부여하지 않는다.

## 다음 업데이트

1. `app/data`의 검토된 자료를 수정한다. 위치 변경은 출처와 판독 한계를 함께 남긴다.
2. `PUBLIC_SITE_URL=https://hdongeun.github.io/participation-archive/` 환경변수를 설정하고 `npm run build:public`을 실행한다. PowerShell에서는 `$env:PUBLIC_SITE_URL = 'https://hdongeun.github.io/participation-archive/'`를 먼저 실행한다.
3. `out/public`의 내용물을 루트로 하는 `public-site.zip`을 만든다. 비밀키·서버 소스·환경 파일을 섞지 않는다.
4. 공개 저장소의 `public-site.zip`을 교체한다. 배포 워크플로가 파일을 풀어 GitHub Pages로 배포한다. 편집 소스를 공유할 때는 공개 구성요소만 담은 `public-source.zip`도 갱신한다.
5. GitHub Actions 성공 후 공개 주소와 변경한 사례 페이지를 확인한다.

새 저장소에 직접 설정할 경우 Settings → Pages → Build and deployment → Source를 GitHub Actions로 선택한다. 계정 비밀번호나 개인 액세스 토큰을 대화에 붙여 넣을 필요가 없다.

## Google 검색

사례마다 고유 URL, 제목, 설명, canonical, 구조화 데이터를 생성하고 sitemap.xml에 포함한다. 사례 본문은 JavaScript 실행 전에도 HTML로 읽을 수 있다. robots.txt는 수집을 허용한다. GitHub 프로젝트 사이트의 robots.txt는 저장소 경로에 있으므로 도메인 루트 규칙을 대신하지 않는다. sitemap은 Search Console에서 직접 제출할 수 있다.

검색 등록을 요청하려면 Google Search Console에 공개 사이트 URL 접두어 속성을 추가하고 소유권을 확인한다. HTML 확인 파일 또는 메타태그 값을 받은 뒤 사이트에 반영하고, `sitemap.xml`을 제출한다. 계정 소유권 인증은 사용자 Google 로그인으로 진행한다. 이 단계 없이도 외부 링크를 통해 발견될 수 있으나, 등록 요청이나 사이트맵 제출이 검색 노출 또는 순위를 보장하지는 않는다.

## 공식 안내

- https://docs.github.com/en/pages/getting-started-with-github-pages/what-is-github-pages
- https://docs.github.com/en/pages/getting-started-with-github-pages/using-custom-workflows-with-github-pages
- https://developers.cloudflare.com/pages/get-started/direct-upload/
- https://developers.google.com/search/docs/crawling-indexing/sitemaps/build-sitemap
