# 공간의 참여 — 공개 사이트 소스

한국의 참여설계 건축과 놀이터를 지도·필터·사례별 기록·조사 출처로 탐색하는 정적 웹사이트입니다. 공개 주소는 `https://hdongeun.github.io/participation-archive/`입니다.

이 패키지는 공개 열람용 편집 소스입니다. 서버, 데이터베이스, 수집·승인 API, 계정 정보와 배포 자격 증명은 포함하지 않습니다. 데이터 수집과 검토는 별도의 비공개 작업에서 수행하고, 확인된 JSON 자료를 갱신한 후 공개 사이트를 다시 빌드합니다.

## 설치와 빌드

Node.js 22.13 이상과 npm이 필요합니다. 이 폴더에서 실행하세요.

```powershell
npm ci
$env:PUBLIC_SITE_URL = 'https://hdongeun.github.io/participation-archive/'
npm run build:public
```

macOS/Linux에서는 다음과 같이 빌드합니다.

```sh
npm ci
PUBLIC_SITE_URL='https://hdongeun.github.io/participation-archive/' npm run build:public
```

결과물은 `out/public/`입니다. 이 폴더의 **내용**을 정적 웹 호스팅에 배포합니다. 최종 주소가 바뀌면 `PUBLIC_SITE_URL`을 새 주소로 바꾸고 다시 빌드하세요. 이 값은 canonical URL과 `sitemap.xml`, `robots.txt`에 쓰입니다.

주소가 정해지지 않은 로컬 검토는 `npm run build:preview`로 빌드할 수 있습니다. 검토용 빌드는 검색을 차단하므로 공개 배포에는 사용하지 마세요. 지도 모듈은 HTTP 서버를 통해 검토해야 합니다. HTML 파일을 직접 더블클릭해서 여는 방식은 지원하지 않습니다.

## 자료와 화면 수정

- `app/data/cases.json`: 사례별 통일 항목, 참여 주체, 연도, 과정, 사진 원문, 출처
- `app/data/locations.json`: 지도 좌표, 주소, 확인 상태, 위치 근거
- `app/data/research.json`: 검토 후보, 조사한 출처와 검색 기록
- `app/atlas.tsx`, `app/case-map.tsx`, `app/research.tsx`: 공개 탐색 화면
- `app/location-info.tsx`: 주소·좌표와 위치 근거 표시
- `public-export/`: 공개 진입 화면과 사례별 기록 스타일
- `scripts/build-public.mjs`: 지도 화면 번들, 사례별 HTML, 출처 기록, 검색엔진 파일 생성

없는 정보는 임의로 채우지 않고 기존 데이터 기준에 맞춰 `null`, 빈 배열 또는 `-`로 유지하세요. 새로운 사례를 추가할 때에는 참여 과정·실제 결과물·최근 10년의 연도 근거를 확인하고 출처와 확인일을 남겨야 합니다. 전체 사례를 망라한 목록은 아닙니다.

지도 좌표를 갱신할 때에는 주소 근거와 건물 위치 근거를 구분합니다. 위성영상 판독값은 측량 좌표로 설명하지 않으며, 불확실한 위치는 확인 상태와 메모에 명시합니다.

## 공개 배포와 검색

GitHub Pages 등 정적 호스팅에서 `out/public/`의 파일을 배포할 수 있습니다. 하위 경로를 포함하는 사이트 주소는 끝의 `/`까지 `PUBLIC_SITE_URL`에 넣으세요. 생성된 `.nojekyll`, `robots.txt`, `sitemap.xml`도 함께 배포합니다.

사이트는 로그인 없이 접근할 수 있는 공개 호스팅에서 검색엔진의 수집 대상이 됩니다. 실제 검색 등록 여부와 시점은 검색엔진이 결정합니다. 배포 후 Google Search Console에서 사이트 소유권을 확인하고 `https://hdongeun.github.io/participation-archive/sitemap.xml`을 제출할 수 있습니다.

## 자료와 지도 권리

사례 사진과 외부 자료의 권리는 각 원저작자에게 있습니다. 이 소스 패키지는 외부 사진에 대한 재사용 허락이나 새로운 라이선스를 부여하지 않습니다. 사진과 도면은 각 원문 링크와 이용 조건을 확인하세요. 지도에는 Leaflet과 OpenStreetMap을 사용하며, 표시된 출처 표기를 유지해야 합니다. 외부 지도 타일을 대량 내려받거나 재배포하지 마세요.
