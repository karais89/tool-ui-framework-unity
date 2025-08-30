# Tool UI Framework for Unity

경량 UI 모듈을 UPM 패키지로 구성해 재사용성과 유지보수성을 높이는 포트폴리오용 프로젝트입니다. 모듈(네비게이션, 팝업, 튜토리얼)을 분리하여 독립 개발·배포가 가능하도록 설계했습니다.

## Quickstart

- 요구 사항: Unity 6000.2.2f1 이상 권장
- 로컬 패키지 참조 방식(권장)
  1) 프로젝트 루트의 `Modules/`에 모듈이 위치합니다.
  2) `Packages/manifest.json`에 아래처럼 `file:` 참조가 추가되어 있어야 합니다.
     - `"com.github.karais89.ui.navigation": "file:../Modules/com.github.karais89.ui.navigation"`
     - `"com.github.karais89.ui.popup": "file:../Modules/com.github.karais89.ui.popup"`
     - `"com.github.karais89.ui.tutorial": "file:../Modules/com.github.karais89.ui.tutorial"`
  3) Unity를 열면 Package Manager에 세 패키지가 Local로 표시됩니다.
  4) 각 패키지의 Samples에서 "Minimal" 샘플을 Import할 수 있습니다.
- 폴더 복사(Embedded) 방식(대안)
  1) `Modules/<package>` 폴더를 `Packages/` 하위로 그대로 복사합니다.
  2) Unity가 자동으로 Embedded 패키지로 인식합니다(별도 manifest 수정 불필요).

## Modules
- com.github.karais89.ui.navigation: 화면 전환/스택 기반 네비게이션 유틸리티
- com.github.karais89.ui.popup: 팝업/오버레이 표시 및 수명주기 관리
- com.github.karais89.ui.tutorial: 온보딩/튜토리얼 단계 표시 및 진행 제어

각 모듈은 다음 공통 구조를 가집니다.
- `Runtime/`: 런타임 코드 및 어셈블리 정의(`.asmdef`)
- `Samples~/Minimal/`: 기본 사용 예제(샘플). 틸드(~)로 기본 컴파일 제외, Package Manager에서 Import 가능
- `Tests/`(옵션): 유닛 테스트 위치

## Repository Structure

```
<repo>
├─ Docs/                      # PRD, TRD, Spikes, 컨텍스트 팩 등 문서 보관
├─ Modules/                   # 실제 UI 모듈(UPM 패키지) 소스
│  ├─ com.github.karais89.ui.navigation/
│  │  ├─ Runtime/
│  │  ├─ Samples~/Minimal/
│  │  └─ Tests/ (optional)
│  ├─ com.github.karais89.ui.popup/
│  └─ com.github.karais89.ui.tutorial/
├─ Packages/
│  └─ manifest.json           # Unity 패키지 의존성 및 로컬 패키지 참조
├─ Assets/                    # 프로젝트 에셋(샘플 씬 등)
├─ ProjectSettings/
├─ CONTRIBUTING.md            # 커밋/브랜치 규칙
└─ .gitignore
```

## Conventions
- 커밋: Conventional Commits(`type(scope): subject`) 사용
  - 예) `chore(modules): scaffold UPM packages (navigation/popup/tutorial)`
  - 예) `build(manifest): link local UPM packages via file:`
- 패키지: 전부 소문자, `com.github.karais89.<domain>` 네이밍
- 샘플: `Samples~` 폴더를 통해 Package Manager에서 Import

## Notes
- asmdef가 빈 경우 Unity가 경고를 표시할 수 있어, 각 모듈 `Runtime/Internal/KeepAssembly.cs`로 경고를 제거했습니다.
- `manifest.json`은 BOM 없이 UTF-8로 저장되어야 합니다.
