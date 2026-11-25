# STRUCTURE · studio-ditto-sample (v0.1 · 흰 인화지 + 상품별 검정 필름 롤(컨택트시트) · 중성 팔레트 + 빨강 표시 · 모서리 2px · 배포 예정 studio-ditto-sample.lgt3232.workers.dev)

```
studio-ditto-sample/
├─ index.html                 단일 파일 (CSS · JS 인라인)
├─ wrangler.toml              name = studio-ditto-sample
├─ .assetsignore              img/ · _old/ · 문서 · index_*.html · _deploy 배포 제외
├─ sd-logo.svg                사장님 로고 벡터(헤더 · 히어로 h1 · 푸터는 invert)
├─ sd-dmserif-v01.woff2       영문 제목 (DM Serif Display 400 · ASCII)
├─ sd-dmmono-v01.woff2        필름 글자 · 번호 · 라벨 (DM Mono 400 · ASCII)
├─ sd-pretendard-v01.woff2    한글 · 본문 (Pretendard 400–600 · 페이지 글자만 → 문구 바꾸면 재생성 + 이름 버전 올리기 R-43)
├─ sd-id-1~4 · sd-semi-1~4 · sd-black-1~4 · sd-mono-1~2 · sd-velvet-1~4 · sd-vintage-1 · sd-duo-1~2 · sd-group-1~2 · sd-x-1~6 .webp   롤 사진(720×900 · velvet은 460×575)
├─ og-sd.jpg · favicon.png    og = 로고 + 필름 3컷 · 파비콘 = 로고 「D」
├─ img/                       다올 제공 원본 + _원문.md + _sd-logo.png(로고 원본 자름 · 배포 제외)
└─ CHANGELOG.md / STRUCTURE.md  (로컬 정본 · 업로드 안 함, R-38)
```

## 섹션 순서
헤더 `.top`(sticky · 로고 · PC 메뉴 4 · 카카오톡 예약 / 900 미만 `.snav` 4칸 · 헤더 버튼 숨김 `.top .head-cta` R-52)
→ 히어로(로고 h1 · 소개 원문 2줄 · 버튼 3 · 히어로 필름 띠 `#hero-frames` 흐름)
→ `#price` 가격 목록 `.index` 8(각 줄 → `#roll-N`) + 안내 3줄
→ `#rolls` 롤 `article.roll#roll-1~8`(번호 · 영문 이름 · 한글 상품명 · 보정 · 가격 + `.strip` 필름 띠) + `#roll-9` More Frames + 인스타 한 줄
→ `#reserve`(원문 2줄 · 버튼 3 · 요일 띠 `.week`)
→ `#visit`(주소 · walk · tel · map + 구글 지도)
→ 푸터(검정 · 로고 반전) + 900 미만 `.quick` 하단 바.

## 롤 추가 · 사진 바꾸기
- 롤 하나 = `<article class="roll" id="roll-N">`. 사진 = `.frames` 안 `<figure class="frame">`(4:5). 첫 컷에 `pick` 클래스 = 빨간 표시.
- 가격을 바꾸면 `.index` 목록과 롤 머리 두 곳을 같이.
- 1100px 이상에서 롤 띠는 4컷이 한 줄에 맞게(`#roll-9`는 6컷).

## 버튼 · 링크
- 카카오톡 채팅 `https://pf.kakao.com/_mxaxaxhn/chat`: 헤더 · 히어로 · 예약 · 푸터 · 하단 바
- 전화 `tel:050714316365`: 히어로 · 예약 · 오시는 길 · 하단 바
- 인스타 `instagram.com/studio_ditto_/` · 네이버 지도 `map.naver.com/p/entry/place/1879187652` · 네이버 플레이스(푸터)

## 모션 (강제 재생)
- `.reveal`(setInterval · 화면 90% 선 · 바닥이면 전부) · 히어로 필름 띠(setInterval 16ms · 화면 밖이면 멈춤 · 복제 이어 붙이기) · 앵커 rAF 스크롤(R-25 · 헤더 + 10px). reduced-motion 분기 없음.

## 폰트 재생성
문구 바꾸면 빠진 글자 검사(LESSONS §26). Pretendard는 `fonts/Pretendard-1.3.9/public/variable/PretendardVariable.ttf` → `fonttools varLib.instancer wght=400:600` → pyftsubset(페이지 글자 + ASCII). DM 두 종은 `fonts/fonts-main/ofl/dmserifdisplay · dmmono`.
