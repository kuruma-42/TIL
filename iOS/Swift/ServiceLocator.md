# Service Loacator

### 개념

-   Service Locator는 의존성 주입(Dependency Injection)의 디자인 패턴 중 하나
-   객체들이 의존성을 외부에서 주입받는 것이 아니라. Locator(중앙 저장소) 에서 직접 가져오는 방식

### 단점

-   의존성 주입이 매우 간단해지지만, 코드가 Service Locator에 강하게 의존
-   Singleton이 가지는 단점 공유
-   컴파일 타임에 코드 에러를 못잡을 가능성 존재
-   클래스의 의존성을 숨기는 면에서 안티패턴으로 보는 사람들도 존재

### 예시 코드

```
protocol OrderValidator {
    func validate(order: Order) -> Bool
}

protocol OrderShipper {
    func ship(order: Order)
}

struct Order {
    let id: Int
}

class SimpleOrderValidator: OrderValidator {
    func validate(order: Order) -> Bool {
        return order.id > 0
    }
}

class SimpleOrderShipper: OrderShipper {
    func ship(order: Order) {
        print("Shipping order \(order.id)")
    }
}

class ServiceLocator {
    static let shared = ServiceLocator()
    private var services: [String: Any] = [:]

    func register<T>(_ service: T) {
        let key = "\(T.self)"
        services[key] = service
    }

    func resolve<T>() -> T {
        let key = "\(T.self)"
        guard let service = services[key] as? T else {
            fatalError("No service registered for \(T.self)")
        }
        return service
    }
}

class OrderProcessor {
    func process(order: Order) {
        let validator: OrderValidator = ServiceLocator.shared.resolve()
        if validator.validate(order: order) {
            let shipper: OrderShipper = ServiceLocator.shared.resolve()
            shipper.ship(order: order)
        }
    }
}
```

### 분석

-   class OrderProcessor를 보면 현재 의존성을 직접 생성하고 있다.
-   OrderProcessor 생성자, 프로퍼티에서 의존성 주입을 알 수 없기 때문에 파일을 열어야만 알 수 있다.
-   테스트할 때 ServiceLocator에 mock을 등록 필요, 테스트가 어렵고 깨지기 쉬움
-   런타임 오류 발생 가능 (fatalError)

### 컴파일 시 에러를 못잡는 이유

```
ServiceLocator.shared.register("adsf" as Any)

let validator: OrderValidator = ServiceLocator.shared.resolve()
```

-   잘못 등록한 경우에 의존성을 호출하는 객체에서 resolve를 시도
-   런타임 Crush 발생
-   private var services: \[String: Any\] = \[:\] 해당 부분에서 Any Type 사용
-   서비스 딕셔너리에는 Any로 저장되기 때문에 Swift 컴파일 타임에 타입을 추론하지 못함
-   강제 타입 캐스팅 (as? T) 사용하기 때문에 T타입을 원하지만, 실제 객체가 다를 수 있다.
-   컴파일러는 register()에서 무슨 타입이 들어가는지 추적하지 않음
