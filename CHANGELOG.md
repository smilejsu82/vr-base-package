# Changelog

All notable changes to this package will be documented in this file.

## [Unreleased]
### Changed
- 런타임 스크립트를 핸드포즈 그립 핵심만 남기고 정리. 데모/에디터에서 쓰이지 않는 소화기·소방호스·라이플 계열 10개 제거(`ExtinguisherBodyBridge`, `FireHoseDesktopTester`, `FireHoseNozzle`, `FireHydrantSystem`, `FireTarget`, `HoseBuilder`, `HosePointRenderer`, `NozzleTriggerBridge`, `SimpleFireHose`, `Rifle`).
- `Doc/index.html` 강의 문서를 흰색 일반 테마로 변경.

## [1.0.0] - 2026-06-23
### Added
- 완전 독립 패키지로 구성 (다른 패키지 의존 없음).
- `Runtime/` — 핸드포즈 적용 · Rifle · FireSafetyVR 런타임 스크립트 + asmdef
- `Editor/` — Hand Pose Recorder 등 에디터 도구 + asmdef
- `Content/Animations`, `Content/Materials`(GhostHand·HandGlow), `Content/Shaders`(GhostHand·HandGlow)
- `Content/HandPoses` — 핸드포즈 스냅샷(SO) + 프리팹
- `Samples~/Demo/Test_1` — 데모 씬
- `Documentation~/` — 가이드 문서
