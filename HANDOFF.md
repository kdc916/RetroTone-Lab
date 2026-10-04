# RetroTone Lab — Development Handoff

## Version
- v0.1.1
- HEIC / HEIF Import Patch

## Product Goal
사진 한 장을 넣고 2000년대 디카, 레트로 인화사진, 필름 네거티브/일회용 카메라 분위기를 빠르게 만들 수 있는 로컬 브라우저 기반 이미지 스타일링 도구.

## Architecture
- 단일 `index.html`
- 기본 이미지 처리는 외부 런타임 라이브러리 없음
- HEIC/HEIF 입력 시 `heic-to 1.5.2` IIFE를 jsDelivr CDN에서 로드해 클라이언트 디코딩
- Canvas 2D 기반
- 서버 통신 없음
- 원본 이미지는 브라우저 메모리에서만 처리

## Processing Pipeline
1. Source image detect
2. HEIC/HEIF일 경우 `heic-to`로 client-side JPEG decode
3. Source image decode
4. Preview resize (max 1600px)
5. Exposure
6. Temperature / Tint
7. Contrast
8. Saturation
9. Shadows / Highlights
10. Fade / lifted blacks
11. Grain
12. Chromatic aberration
13. Softness
14. Halation
15. Vignette
16. Dust / scratches
17. Date stamp
18. Export canvas render

## UI Structure
- Left: image load + presets
- Center: live preview + compare
- Right: detailed controls + export
- Mobile: preview first, controls stacked vertically

## Stability Baseline
v0.1.0을 초기 안정 기준으로 사용. 이후 기능 추가 시 아래 동작을 회귀시키지 말 것.
- 프리셋 선택
- 모든 슬라이더 실시간 반영
- 원본 비교 버튼
- JPG/PNG/WEBP 저장
- 모바일 레이아웃
- 로컬 처리

## Known Technical Limitations
- Canvas 2D CPU 처리이므로 40MP+ 원본 export는 모바일에서 메모리 부족 가능.
- HEIC/HEIF는 `heic-to 1.5.2`로 브라우저 내부 디코딩. 최초 사용 시 CDN 접근이 필요.
- HEIC → JPEG 디코딩 단계에서 EXIF/메타데이터는 현재 보존하지 않음.
- 특수 HEIC 컨테이너(버스트/애니메이션)는 첫 프레임 기준 처리 가능성이 있음.
- 색관리(ICC profile)와 Wide Gamut P3는 현재 별도 처리하지 않음.
- Halation은 highlight mask + screen blur 방식의 근사 구현.
- Chromatic aberration은 채널 shift 방식.

## Recommended v0.2.0
1. WebGL2 shader pipeline
2. 3D LUT (.cube) import
3. HSL 8-color mixer
4. RGB curves
5. Film profile custom preset save/load
6. EXIF date parsing
7. Before/After split slider
8. High-res tiled export
9. HEIC decoder self-host/bundle option + EXIF preservation

## Development Policy
- 기존 프리셋 결과가 크게 바뀌는 경우 preset schema에 version을 부여할 것.
- 대용량 사진 처리 시 preview와 final render를 분리 유지.
- 원본 이미지는 절대 변형하지 않고 source를 기준으로 매번 재렌더링.
- 외부 서버 업로드 기능은 명시적 요구 전까지 추가하지 않음.


## v0.1.1 Change Log
- `.heic`, `.heif`, `image/heic`, `image/heif` 입력 허용
- 파일 확장자 기반 HEIC/HEIF 감지 추가
- `heic-to 1.5.2` client-side decoder 연결
- HEIC/HEIF → JPEG(quality 0.96) → 기존 Canvas 파이프라인
- decoder 실패 시 브라우저 native image decode fallback
- HEIC 로딩 상태 UI 및 오류 메시지 개선
