# RetroTone Lab v0.1.7

브라우저에서 사진을 불러와 2000년대 디지털 카메라, 레트로, 필름 인화 색감을 빠르게 만드는 단일 HTML 도구입니다.

## 실행

`index.html` 파일을 Chrome / Edge / Safari 등 최신 브라우저로 열면 됩니다. 별도 설치나 서버가 필요하지 않습니다.

## 주요 기능

- 2000년대 디지털 감성 프리셋
  - CCD Compact 2003
  - Flash Party 2007
  - Minihome 2004
  - Phone Cam 2009
- 필름 프리셋
  - Color Print 200
  - Consumer 400
  - Disposable Flash
  - Cool Negative
- 레트로 프리셋
  - Family Album
  - Y2K Pop
  - Expired Film
- 수동 조절
  - 노출 / 대비 / 채도 / 색온도 / 틴트
  - 페이드 / 그림자 / 하이라이트
  - 필름 그레인 / 비네팅 / 소프트니스 / 할레이션 / 색수차 / 먼지·스크래치
- 날짜 스탬프
- 원본 비교
- HEIC / HEIF 불러오기 및 브라우저 내부 자동 JPEG 디코딩
- 사진 붙여넣기 지원
- JPG / PNG / WEBP 내보내기
- 원본 / 50% / 25% 크기 저장
- 서버 업로드 없이 로컬 처리
- 모바일 대응 UI

## 권장 사용법

1. 사진 열기
2. 프리셋을 먼저 선택
3. Basic Tone에서 노출과 대비를 정리
4. Retro Character에서 그레인과 비네팅을 조절
5. 필요하면 날짜 스탬프 활성화
6. 보정본 저장

## 알려진 제한

- HEIC/HEIF는 `heic-to 1.5.2`를 이용해 브라우저 안에서 JPEG로 디코딩합니다. 이미지 파일은 서버로 업로드하지 않습니다.
- HEIC 디코더는 저장소의 `vendor/heic-to.js`에 포함되어 있어 CDN 연결 없이 동작합니다.
- HEIC 변환 과정에서 원본 EXIF/메타데이터는 현재 보존하지 않습니다.
- 매우 큰 고해상도 이미지는 내보내기 시 모바일 메모리 한계에 영향을 받을 수 있습니다.
- 현재 버전은 LUT 파일 직접 불러오기 기능이 없습니다.

## 다음 개발 후보

- LUT(.cube) Import / Export
- 필름 프로파일 관리
- RGB Curve / HSL Color Mixer
- Bloom / Highlight Roll-off 고도화
- JPEG 2000s 압축 질감
- CCD Noise / CMOS Noise 분리
- 스캔 테두리 / 인화지 / 날짜 폰트 추가
- Before / After 스플릿 뷰
- 프리셋 저장 / 불러오기(JSON)
- EXIF 기반 실제 촬영일 날짜 스탬프
- WebGL 가속


## v0.1.1

- HEIC / HEIF 파일 선택 지원
- MIME이 비어 있거나 `application/octet-stream`으로 들어오는 `.heic/.heif`도 확장자로 감지
- HEIC/HEIF를 브라우저 내부에서 JPEG로 자동 변환 후 기존 RetroTone 파이프라인에 연결
- 변환 라이브러리 실패 시 브라우저 네이티브 디코딩 fallback
- 로딩 상태 표시 및 모바일 파일 선택 호환성 개선


## v0.1.4

- 프리셋을 사진 바로 아래 고정형 LOOK PRESETS 도크로 이동
- 2000s / FILM / RETRO 카테고리 탭 추가
- 프리셋을 세로 목록이 아닌 가로 스크롤 칩으로 변경
- 선택한 프리셋 이름을 사진 아래에서 항상 확인 가능
- 우측 설정을 톤 / 필름 질감 / 날짜 / 저장 4개 탭으로 분리
- 데스크톱 전체 화면 높이에 맞춘 편집 레이아웃으로 페이지 스크롤 최소화
- 모바일에서는 사진 미리보기를 상단에 sticky 처리하여 설정을 조절하면서 사진 확인 가능
- 모바일의 불필요한 왼쪽 패널을 숨기고 상단 사진 열기 버튼 중심으로 단순화


## v0.1.4

- 모바일 미리보기의 기존 `56vh / min-height:390px` 강제값 제거
- `dvh` 기반 모바일 전용 미리보기 높이 적용
- 세로 스마트폰에서 미리보기 영역을 약 190~260px 범위로 자동 조절
- 390px 이하 소형 화면 추가 최적화
- 가로모드에서는 sticky 미리보기를 해제해 편집 공간 확보
- 모바일 상단바, 버튼, 프리셋 카드, 설정 컨트롤 크기 재조정
- 화면 가로 넘침 방지
- 안전영역(safe-area inset) 대응
- 모바일에서 **사진 작게 / 사진 크게** 토글 추가
- 기존 HEIC/HEIF, 필름 프리셋, 원본 비교, 저장 기능 유지


## v0.1.4

- HEIC 로딩 실패 원인 수정: 외부 CDN 의존 제거
- `heic-to 1.6.5 / libheif 1.23.5`를 `vendor/heic-to.js`로 저장소에 포함
- Android/Samsung Internet에서 HEIC 변환 시 ImageBitmap 우선 디코딩
- JPEG Blob 디코딩 fallback 유지
- 모바일 미리보기 위에 변환 중/완료/실패 상태 표시
- 변환 결과의 실제 width/height 검증 후 Canvas에 전달
- 다운로드용 standalone HTML은 HEIC decoder까지 파일 내부에 포함


## v0.1.5

- 일반 이미지 로더와 HEIC 로더를 완전히 분리
- JPG / JPEG / PNG / WebP / GIF / BMP 확장자 및 파일 시그니처 감지
- Android `content://` 파일 제공자의 빈 MIME / `application/octet-stream` 대응
- 일반 이미지는 `createImageBitmap → FileReader DataURL → Blob URL` 3단계 fallback
- HEIC 디코더는 HEIC 파일을 선택할 때만 lazy-load
- GitHub Pages에서는 저장소 내 `vendor/heic-to.js` 우선, 실패 시 CDN fallback
- 다운로드한 단일 HTML에서는 CDN HEIC decoder를 필요할 때만 로드
- 이미지가 디코딩되면 효과 처리 전에 원본을 Canvas에 먼저 표시
- 효과 렌더링 실패가 발생해도 사진 자체는 계속 표시
- 실패 시 실제 오류 메시지를 화면에 표시
- Samsung/Android 브라우저를 위해 `[hidden]{display:none!important}` 추가


## v0.1.6

- 실제 사용자 JPG 2종(1536×1027 sRGB, 1536×1152 Display P3)으로 모바일 브라우저 재현 테스트
- 이미지 디코딩은 정상인데 모바일 Grid의 implicit column이 프리셋 목록의 min-content 폭(약 1253px)까지 확장되는 문제 확인
- 그 결과 preview canvas가 390px 화면에서 x≈471px 바깥으로 밀려 “이미지가 안 열린 것처럼” 보이던 버그 수정
- `.viewer`에 `grid-template-columns:minmax(0,1fr)` 및 `min-width:0` 적용
- `.stage`, `.preset-dock`, `.preset-dock-head`, `.preset-tabs`, `.preset-strip`의 min/max width 제한
- 모바일 viewer에 `max-width:100vw` 강제
- 패치 후 두 테스트 이미지 모두 canvas가 화면 안에 위치하고 실제 픽셀 표시 확인


## v0.1.7

- 실제 제공 JPG 2종 + PNG + WebP + EXIF Orientation=6 JPEG 브라우저 회귀 테스트
- 390 / 412 / 768 / 1280px viewport에서 전 포맷 화면 내부 표시 확인
- JPEG EXIF Orientation parser 추가 및 회전 메타 검증
- Android content:// 안정성을 위해 FileReader → ObjectURL → ImageBitmap fallback 유지
- 이미지 연속 교체 시 이전 비동기 로드가 최신 이미지를 덮어쓰지 않도록 load sequence guard 추가
- ImageBitmap 교체/페이지 종료 시 close()로 메모리 정리
- HEIC 디코더에 버전 쿼리 cache-busting 적용
- standalone HTML은 HEIC decoder를 inert inline payload로 포함해 로컬 실행 시 네트워크 없이 지연 활성화
- 220MB 초과 단일 이미지 입력 보호
