# RetroTone Lab — Development Handoff

## Version
- v0.1.0
- Initial MVP

## Product Goal
사진 한 장을 넣고 2000년대 디카, 레트로 인화사진, 필름 네거티브/일회용 카메라 분위기를 빠르게 만들 수 있는 로컬 브라우저 기반 이미지 스타일링 도구.

## Architecture
- 단일 `index.html`
- 외부 라이브러리 없음
- Canvas 2D 기반
- 서버 통신 없음
- 원본 이미지는 브라우저 메모리에서만 처리

## Processing Pipeline
1. Source image decode
2. Preview resize (max 1600px)
3. Exposure
4. Temperature / Tint
5. Contrast
6. Saturation
7. Shadows / Highlights
8. Fade / lifted blacks
9. Grain
10. Chromatic aberration
11. Softness
12. Halation
13. Vignette
14. Dust / scratches
15. Date stamp
16. Export canvas render

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
- HEIC/HEIF 디코딩은 브라우저 지원 여부에 의존.
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
9. Smartphone HEIC fallback decoder integration option

## Development Policy
- 기존 프리셋 결과가 크게 바뀌는 경우 preset schema에 version을 부여할 것.
- 대용량 사진 처리 시 preview와 final render를 분리 유지.
- 원본 이미지는 절대 변형하지 않고 source를 기준으로 매번 재렌더링.
- 외부 서버 업로드 기능은 명시적 요구 전까지 추가하지 않음.

