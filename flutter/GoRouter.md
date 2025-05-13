# SwiftUI → Flutter 전환 가이드: 라우팅 구조와 GoRouter 활용 전략

SwiftUI 기반 앱을 Flutter로 전환할 때 가장 큰 구조적 차이 중 하나는 라우팅(Routing) 시스템.
Flutter에서는 `GoRouter` 패키지를 통해 구조적이고 선언적인 라우팅 구현이 가능하며, 이는 SwiftUI의 방식과 큰 차이를 보인다.  
본 문서는 Flutter에서 GoRouter를 도입했을 때의 주요 이점과 SwiftUI와의 차이점, 전환 시 고려사항을 정리한다.

---

## 1. SwiftUI와 Flutter의 라우팅 구조 비교

| 항목 | SwiftUI Navigation (iOS 16+) | Flutter GoRouter |
|------|------------------------------|------------------|
| 라우팅 정의 위치 | View 내부에 직접 정의 (`NavigationLink`) | 전역 라우터 객체에서 선언적으로 정의 (`GoRoute`) |
| 화면 전환 방식 | 상태 기반 (`@State`, `NavigationLink`) | 경로 기반 (`context.go('/path')`) |
| 중첩 라우트 구성 | `NavigationStack` 사용 (구조 복잡) | `ShellRoute` + 중첩 `GoRoute` |
| 조건부 라우팅 처리 | 상태 기반 수동 제어 | `redirect` 함수 사용 |
| 딥링크 및 웹 대응 | 별도 구현 필요 (`SceneDelegate` 등) | URL 기반 라우팅 기본 지원 |

SwiftUI는 라우팅과 UI가 결합된 구조이며, Flutter + GoRouter는 라우팅 로직을 별도로 분리해 관리할 수 있다.

---

## 2. GoRouter 도입 시 장점

### 2.1 명확한 라우팅 선언

GoRouter는 화면 경로를 `GoRoute` 객체로 정의하며, 중앙 집중식으로 관리 가능하다.

```dart
final GoRouter router = GoRouter(
  routes: [
    GoRoute(path: '/', builder: (_, __) => HomeScreen()),
    GoRoute(path: '/profile', builder: (_, __) => ProfileScreen()),
  ],
);
```

### 2.2 context 기반 화면 전환
- Flutter는 명시적으로 라우팅을 수행한다.
  
```
context.go('/profile');
라우팅 로직을 UI와 분리하면 테스트 및 유지 관리가 간단해진다.
```

##3. 고급 기능

### 3.1 ShellRoute
- 공통 레이아웃(예: 하단 탭바)이 필요한 경우 ShellRoute를 사용한다.

```
ShellRoute(
  builder: (context, state, child) => AppScaffold(child: child),
  routes: [
    GoRoute(path: '/home', builder: ...),
    GoRoute(path: '/settings', builder: ...),
  ],
);
```
- 공통 UI를 기준으로 하위 라우트를 구분할 수 있음
- 탭 전환 시 상태 유지에 유리함
- 
### 3.2 Redirect
- 조건부 라우팅이 필요한 경우, 예를 들어 로그인 여부에 따라 이동을 제한할 수 있다.
```
redirect: (context, state) {
  final isLoggedIn = ref.read(authProvider).isLoggedIn;
  if (!isLoggedIn && state.subloc != '/login') {
    return '/login';
  }
  return null;
}
```
- 라우팅 조건을 선언적으로 관리
- UI 코드에 분기 로직이 분산되지 않음

## 4. 전환 시 고려사항

SwiftUI의 화면 전환 방식과 Flutter + GoRouter 구조는 개념적으로 차이가 있다.  
전환 과정에서는 각 기능이 어떤 식으로 재구성되어야 하는지 고려해야 한다.

| SwiftUI 기준                                      | Flutter 전환 시 고려                                 |
|--------------------------------------------------|------------------------------------------------------|
| `NavigationLink`, `NavigationStack` 기반 화면 이동 | `context.go()` 또는 `context.push()` 사용             |
| 상태 기반 화면 전환 트리거                         | 명시적인 경로 기반 전환 방식 적용                    |
| `TabView`를 통한 탭 화면 구성                      | `ShellRoute`를 사용해 탭 구조 구현                    |
| 딥링크 및 외부 경로 처리                           | URL 기반 자동 처리 (딥링크 및 Flutter 웹 포함)       |

## 5. 라우팅과 UI 분리의 이점

- UI에서 라우팅이 분리되면 다음과 같은 실무적 장점이 있다.

### 5.1 UI 컴포넌트 재사용성 증가
- 라우팅이 컴포넌트 내부에 있으면 재사용이 어려움
- 라우팅을 외부에서 주입하면 테스트 및 확장이 쉬워짐
 
### 5.2 테스트 용이성
- 라우팅이 분리되면 UI 단위 테스트 시 실제 네비게이션 호출 없이 테스트 가능
  
### 5.3 관심사 분리
- UI는 시각적 표현에 집중
- 화면 전환은 상태나 로직이 담당

### 5.4 조건부 라우팅 구현 용이
- 로그인, 권한 등 조건에 따라 흐름 제어가 깔끔해짐
- 뷰 코드에 조건 분기가 혼합되는 현상 방지

### 5.5 협업 효율 향상
- 라우팅 설계자와 UI 개발자의 역할 분리 가능
- 라우팅 변경 시 UI 컴포넌트에 영향 없음

## 6. 결론
- Flutter의 GoRouter는 라우팅과 UI를 분리하여 구조적 유연성을 제공
- 복잡한 앱 구조(탭, 중첩 라우트, 로그인 가드, 딥링크 등)에 효과적으로 대응
- SwiftUI의 상태 기반 라우팅과 비교해 명확하고 유지 관리가 쉬운 구조 설계 가능
- 전환 초기에는 기존 SwiftUI 화면 구조를 기준으로 Flutter 라우팅 방식을 재설계하는 것이 핵심
