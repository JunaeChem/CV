# Jaejun Park, Academic CV (웹페이지)

정적 HTML/CSS 사이트. 빌드 과정 없음.

- `index.html`: CV (소개, 연구 이미지, 학력, 대표 논문, 기술, 교육, 수상, 과제, 경력)
- `publications.html`: 논문 목록, 준비 중 논문, 특허, 학회 발표
- `style.css`, `images/`

2026-11-16 전면 개편본(v6). 근거: CV 설문 1차·2차 응답, 수료증·상장 PDF, 학회 포스터 PPT, 대화 중 지시.

## 영문 / 한글 전환

- 두 언어가 한 파일 안에 나란히 들어 있음. `class="en"` 요소는 영문, `class="ko"` 요소는 한글에서만 보임. 클래스가 없는 요소는 두 언어 공통.
- 상단의 English / 한국어 버튼으로 전환하며, 선택은 브라우저에 저장됨. 주소 끝에 `#ko` 또는 `#en`을 붙이면 해당 언어로 열림.
- 한글판 규칙: 섹션 제목과 기술 용어는 영문 유지. 기관명, 상 이름, 과목명, 학회명, 인명은 한글 이름이 있으면 한글. 논문 제목, 저자, 저널명은 원문 유지.
- **내용을 고칠 때는 `en`과 `ko` 두 곳을 함께 고칠 것.**

## 주석 표식

| 표식 | 의미 | 처리 방법 |
|---|---|---|
| `PENDING:<id>` | 자료가 아직 없어 비워 둔 자리 | 자료를 받으면 채우고 표식 삭제 |
| `EDIT:<id>` | 초안 또는 미확인 값이 들어가 있는 자리 | 본인 확인 후 표식만 삭제 |

찾는 법: `grep -n "PENDING:\|EDIT:" *.html`

원칙: 제공되지 않은 값은 추정해서 채우지 않음. 공개 페이지에 "준비 중" 같은 빈자리 문구를 두지 않음.

## 미완료 항목

| ID | 위치 | 내용 |
|---|---|---|
| PENDING:c4 | index `#training` | COMSOL 다른 모듈 교육(AC/DC, Microfluidics, Particle Tracing)의 과정명, 주관, 날짜 |
| EDIT:summary | index 소개문 | 영문·한글 1인칭 초안. 문장 검토 |
| EDIT:metrics | index 우측 표 | Publications는 [1]–[12](게재 승인 1편 포함). Citations, h-index는 Google Scholar 2026-11 기준 |
| EDIT:p12 | publications `#p12` | *Nano Convergence* 게재 승인 논문. 출판되면 권, article number, DOI 추가. Review 태그는 제목으로 판단한 것 |
| EDIT:d3 | publications `#prep` | 준비 중 논문 2편. 두 번째 논문의 앞 세 저자를 equal contribution으로 표기한 것이 맞는지 확인 |

확인하지 못한 값: 표지 4건의 front cover 구분과 권·호(본인 제공, 출판사 페이지 대조 못 함), 한글 학회명 표기(예: 대한화학회 "학술발표회"), 한글 학위 표기("응용화학과 박사과정 수료").

## 게시하지 않기로 한 것 (본인 결정)

- COMSOL near-field map 이미지: 비공개. 저장소에 올리지 않음
- 수료증·상장 이미지: 텍스트로만 기재
- 프로필 사진
- 대표 논문의 Contribution 문구
- 저널 표지 갤러리: 표지는 해당 논문 오른쪽에 표시

## 수정 방법

- 항목 추가: 같은 섹션의 `<div class="item">` 또는 `<div class="pub">` 블록을 복사.
- 논문 추가: `publications.html` 목록 맨 위에 추가하고 번호, 상단 문장의 편수, 섹션 제목의 편수, `index.html` 우측 표를 함께 수정.
- 표지가 있는 논문: `<div class="pub withcover">` 구조(본문은 `.text` 안, 표지 `<img>`는 그 뒤).
- 색: `style.css` 맨 위 변수. 상단 띠 `--green-pale`, 하단 띠 `--blue-pale`, 한양 블루 `--blue`.
- PDF: 브라우저 인쇄(PDF로 저장)용 스타일이 `style.css` 끝에 있음. 현재 보이는 언어로 출력됨.
- 날짜 표기: 영문 `Jul. 2022`, `Sep. 12, 2024` / 한글 `2022.07`, `2024.09.12`.
- 더 이상 쓰지 않는 기존 파일: `images/CEC.png`, `EA.png`, `LoC.png`, `NA.png`, `logo_*.png` (삭제 가능).
