# RetroTone Lab v0.1.0

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

- HEIC/HEIF는 브라우저가 해당 형식을 직접 디코딩할 수 있는 환경에서만 열립니다.
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

