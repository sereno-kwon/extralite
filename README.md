# Extralite · Rubi Workshop

extralite.rubiworkshop.com 원페이지 정적 사이트. quoc.rubiworkshop.com · whiteind.rubiworkshop.com과 같은 구조와 디자인(레이아웃, 서체, 빌드 방식)입니다.

- 사이트 표기: 운영 주체는 "루비워크샵"(사이트 이름, og:site_name, 구조화 데이터, 헤더, 저작권 표기). "익스트라라이트 코리아"라는 표현은 쓰지 않습니다.
- `index.html` 한국어 원페이지 (Extralite · Range · Cockpit · Hubs · Wheels · Brompton · Drivetrain · Fit · Story · Showroom)
- 디자인은 rubi.kr 체계: 영문 Pretendard · 한글 에스코어 드림, 웨이트 400, 흑백과 얇은 라인, 각진 버튼, 라이트/다크 자동. 일본어 페이지는 빌드 시 Noto Sans JP로 바뀝니다.
- 공식 로고 이미지는 깃털과 글자가 겹쳐 단색 처리가 어려워, 헤더 로고는 글자 워드마크(Extralite + Rubi Workshop)로 씁니다. 단색 SVG 로고를 받으면 `.logo` 안을 이미지로 바꾸면 됩니다.
- 제품 사진은 배경이 흰색~옅은 회색으로 제각각이라 4:3 옅은 회색 무대에 `mix-blend-mode:multiply`로 얹습니다. 라이프스타일 사진은 3:2, 세로 사진은 4:5(`tall`). 포인트 컬러는 퍼플(#6a3fa0)로 포커스 표시에만 씁니다.
- 자바스크립트가 꺼져 있어도 본문이 보이도록 등장 모션은 `html.js`일 때만 적용합니다.
- `index.src.html` 편집용 한국어 원본. 규격 표는 `{{HUB_TABLE}}`, `{{STEM_TABLE}}`, `{{WHEEL_TABLE}}` 자리에 빌드 시 채워집니다 (`tools/build.py` 안의 HUBS, STEMS, WHEELS).
- `en/index.html`, `ja/index.html` 영어 · 일본어 페이지 (빌드로 생성, 직접 수정하지 않음)
- `i18n/tr_source.py` 한국어 · 영어 · 일본어 번역 묶음, `en.json` · `ja.json`은 여기서 생성
- `404.html` 하위 주소(/hyperstem, /hubs, /brompton, /cybercity, /qrc, /fit, /dealers 등)를 섹션으로 연결
- `.github/image-manifest.txt` + `fetch-images.yml` 익스트라라이트 공식 사이트(extralite.com) 이미지 이전용 워크플로. 매니페스트를 고쳐 푸시하면 비어 있는 파일만 받아 커밋합니다.

## 배포
1. 이미지는 첫 푸시 때 워크플로가 extralite.com에서 48개를 받아 `images/`에 커밋했습니다.
2. 배포: Cloudflare Pages(저장소 연결, 빌드 명령 없음, 출력 폴더 `/`) 또는 GitHub Pages.
3. 도메인 DNS에 `extralite` CNAME 레코드를 추가합니다. CNAME 파일은 이미 들어 있습니다.
4. 파비콘은 별도로 넣어야 합니다: `images/favicon-48.png`, `images/favicon-96.png`, `images/apple-touch-icon.png`(180px), `images/logo-512.png`.
5. 네이버 서치어드바이저 소유 확인 파일(`naver….html`)은 사이트 등록 후 받아 루트에 넣습니다.

## 문구 수정과 번역
1. `index.src.html`의 한국어 문구를 고칩니다.
2. `python3 tools/build.py` → `python3 i18n/extract.py` 로 `ko.json`을 갱신합니다.
3. 바뀐 문장을 `i18n/tr_source.py`에서 같은 한국어 키로 고치거나 (한국어, 영어, 일본어)로 추가하고 `python3 i18n/tr_source.py`.
4. 다시 `python3 tools/build.py`. 번역되지 않은 문장이 있으면 목록으로 알려줍니다.

빌드에는 `beautifulsoup4`가 필요합니다.

## 링크
- 헤더 Shop, "루비워크샵에서 보기" 버튼: `https://rubiworkshop.com/extralite`
- 거래처 문의: 루비서플라이 02-516-8465, 카카오톡 채널 `https://pf.kakao.com/_NFnBj/chat`
- 푸터 Instagram: `https://www.instagram.com/rubi.workshop`

## 한글 표기
익스트라라이트(Extralite), 스튜디오 리바(Studio Riva), 세르지오 리바(Sergio Riva), 브롬톤(Brompton), 버드(Berd) 스포크, 마작(Mazak). 제품명 HyperStem, HyperSmart 3+, CyberCity 349B, QRC3S-B 등은 원문 표기.

## 출처
- 수치와 규격: extralite.com 제품별 Configure · Tech info, Product History (2026-11 확인)
- 브랜드: extralite.com 홈 · MTB 컬렉션 소개, Cicli Corsa 「Extralite Visit」
