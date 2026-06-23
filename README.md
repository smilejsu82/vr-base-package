# VR Base Package (`com.smilejsu82.vr-base`)

Hand Pose Recorder 도구 · 잡기 그립 포즈 적용(Rifle) · 두 손 VR 소화기(FireSafetyVR) 런타임 · 핸드포즈/머티리얼/셰이더 · 데모 씬을 **모두 담은 완전 독립 UPM 패키지**입니다.

> ✅ **다른 패키지에 의존하지 않습니다.** 스크립트(`HandPoseData`, `Rifle`, `FireHoseNozzle` 등), 에디터 도구(Hand Pose Recorder), 셰이더(`GhostHand`·`HandGlow`)가 전부 이 패키지 안에 포함되어 있습니다. Git URL 하나만 추가하면 됩니다.

---

## 설치 (Package Manager)
1. Unity ▸ **Window ▸ Package Manager**
2. 좌상단 **`+` ▸ Add package from git URL...**
3. 입력:
   ```
   https://github.com/smilejsu82/vr-base-package.git
   ```
4. Add → **XR 의존성 자동 설치**

> 특정 버전 고정: URL 뒤에 `#v1.0.0` 처럼 태그를 붙일 수 있습니다.

## 필수 패키지 (의존성)
아래 패키지가 함께 설치되어야 합니다. `package.json`에 의존성으로 선언되어 있어 **자동 설치**되지만, 버전 충돌 등으로 자동 설치가 안 될 경우 **Package Manager에서 직접 설치**하세요.

| 패키지 | 버전 | 식별자 |
|--------|------|--------|
| OpenXR Plugin | **1.16.1** | `com.unity.xr.openxr` |
| XR Hands | **1.7.3** | `com.unity.xr.hands` |
| XR Interaction Toolkit | **3.4.1** | `com.unity.xr.interaction.toolkit` |
| XR Plugin Management | **4.6.0** | `com.unity.xr.management` |
| Input System | 1.19.0 | `com.unity.inputsystem` |
| Universal RP (URP) | 17.4.0 | `com.unity.render-pipelines.universal` |

직접 설치하는 법: **Window ▸ Package Manager ▸ `+` ▸ Add package by name...** 에 위 식별자와 버전을 입력
(예: `com.unity.xr.openxr` / `1.16.1`).

## 필수 샘플 임포트
데모 씬의 XR 리그·손 모델은 아래 두 패키지의 **샘플**을 사용합니다. (라이선스/용량상 이 패키지에 포함하지 않음)
**Window ▸ Package Manager** 에서 각 패키지를 선택 → **Samples 탭 ▸ Import** 하세요.

| 패키지 | 임포트할 샘플 |
|--------|--------------|
| XR Hands (`com.unity.xr.hands`) | **HandVisualizer** |
| XR Interaction Toolkit (`com.unity.xr.interaction.toolkit`) | **Starter Assets** |

> 임포트하면 `Assets/Samples/...` 아래에 들어옵니다. 이걸 먼저 임포트한 뒤 데모 씬을 열어야 손/리그 참조가 채워집니다.

## 설치 후 1회 설정 (XR)
- **Project Settings ▸ XR Plug-in Management** ▸ (Android/PC 탭) **OpenXR** 체크 + **Hand Tracking** + Meta Quest/Oculus Touch 프로파일
- **URP**를 활성 렌더 파이프라인으로 지정 (URP 템플릿이면 자동)
- **Player ▸ Active Input Handling = New (또는 Both)**

---

## 포함 내용
- `Runtime/` — 핸드포즈 적용(`HandPoseApplier`), `Rifle`, FireSafetyVR(`FireHoseNozzle`·`FireHydrantSystem`·`FireTarget` 등) 런타임 스크립트 + asmdef
- `Editor/` — **Hand Pose Recorder** 윈도우, Grab Attach·Tracked Pose Driver Setup 등 에디터 도구 + asmdef
- `Content/`
  - `Animations/XRHand/` — 컨트롤러 손 그립/오픈 애니메이션 + Animator(`XRHand_L/R`)
  - `Materials/` — `GhostHand`, `HandGlow`
  - `Shaders/` — `GhostHand`, `HandGlow`
  - `HandPoses/` — 녹화한 핸드포즈 스냅샷(SO) + 프리팹
- `Samples~/Demo/` — `Test_1` 데모 씬 (Package Manager에서 **Import**)
- `Documentation~/` — 가이드 문서

## 도구
- 메뉴 **Tools ▸ Hand Pose Recorder**
- 그립 포즈 캡처 → Attach to Target → 프리팹/포즈 SO 자동 저장
- 손목까지 일치: `Ghost Hand Model`에 그립용 손 모델 지정
- 문서: `Documentation~/HandPose-Attach-Guide.md`

## 쓰는 법
- 본인 XR 리그(컨트롤러 손)에 `XRHand_L/R` 컨트롤러를 Animator에 물리고, 잡을 오브젝트에 `Rifle`(또는 그립 스크립트) + `HandPoseData`를 할당하면 그립 포즈가 동작합니다.
- 데모 씬은 XR 리그·손 모델로 XRI Starter Assets / XR Hands 샘플 또는 본인 모델을 사용하세요(모델은 라이선스/용량상 미포함).

## 주의
- 핸드트래킹 포즈 캡처는 실제 기기(Quest / Link)에서만 동작합니다.
- 이 패키지는 `com.smilejsu82.vr-handpose-fire`의 모든 기능을 포함한 **독립 버전**입니다. 두 패키지를 **동시에 설치하지 마세요**(스크립트 GUID·asmdef가 겹쳐 충돌합니다).
