## Flutter 위젯 개념 정리

### 개념

- 위젯(widget)은 UI를 구성하는 모든 요소의 기본 단위  
- Flutter앱의 모든 것은 위젯으로 구성됨  
- 텍스트, 버튼, 아이콘, 레이아웃 구조, 애니메이션 까지 포함하는 개념  
f

### 핵심 개념

#### 모든 것은 위젯

- 버튼, 텍스트,이미지 같은 UI 요소뿐만 아니라, 패딩, 정렬, 행, 열 같은 레이아웃도 모두 위젯이다.  

#### 위젯은 불변(immutable)

- 위젯 자체는 상태를 변경하지 않는다.  
- 상태가 바뀌면 새로운 이젯을 생성해서 UI를 다시 그린다.  


### 위젯 유형

- **StatelessWidget** → 상태가 변하지 않는 위젯 (e.g. 아이콘, 고정 텍스트)  
- **StatefulWidget** → 상태에 따라 바뀔 수 있는 위젯 (e.g. 체크박스, 입력 폼)  


### 위젯 트리

- Flutter 앱은 위젯 트리라는 구조로 모든 UI를 구성  
- 부모 - 자식 구조로 이루어져 있다.  
- 하나의 위젯 안에 다른 위젯들을 포함 가능

## Flutter Widget vs SwiftUI View

| 항목 | **Flutter (Dart)** | **SwiftUI (Swift)** |
|------|---------------------|----------------------|
| **기본 단위** | `Widget` | `View` |
| **상태가 없는 UI** | `StatelessWidget` | `View` 구조체 |
| **상태가 있는 UI** | `StatefulWidget` + `State` 객체 | `@State`, `@Binding`, `@ObservedObject` 등 |
| **UI 정의 방식** | 메서드 기반 (`build(context)`) | 선언형 구조체 (DSL 스타일) |
| **재빌드 방식** | 상태 변경 시 `build()` 재실행 | 상태 변경 시 `body` 재실행 |
| **레이아웃 구조** | `Row`, `Column`, `Stack`, `Container` | `HStack`, `VStack`, `ZStack` |
| **핫리로드** | 지원 (Hot reload/Hot restart) | 지원 (Xcode Canvas, Previews) |
| **UI 구성** | 위젯 중첩 (Widget Tree) | View 조합 (View Hierarchy) |
| **스타일/모디파이어** | 속성이나 `style` 객체 전달 | `.modifier()` 체이닝 방식 |
