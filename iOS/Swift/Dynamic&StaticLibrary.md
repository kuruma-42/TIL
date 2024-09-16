# Dynamic & Static Library 🧨

## Definition
- Xcode Target의 일부로 빌드되지 않은 코드 및 데이터 조각을 정의한 것
- 라이브러리는 다른 프로젝트에서 재사용 할 수 있는 코드 및 리소스 모음을 나타낸다.
- 특정 기능을 제공하거나 일반적인 프로그램이 문제를 해결하는 미리 작성된 함수, 클래스 및 기타 구성 요소가 포함되어 있다.
- 단순히 코드 및 데이터 조각을 정의했고 이걸 내 앱 코드에 가져다 쓰고싶다.
- 라이브러리와 앱의 소스코드 파일을 병합(merge)하는 프로세스를 Link라고 한다.
- 라이브러리는 앱에 Link되는 방식에 따라 두 가지로 나뉘게 된다.
    - Static Library: “ .a” 접미사를 가진다.
    - Dynamic Library: “ .dylib” 접미사

## Static Library
<img width="638" alt="image" src="https://github.com/user-attachments/assets/76cda90e-3cfe-49b7-8b76-aab822affabe">

- Static Library는 빨간색 네모의 Static Libraries에 위치하게 된다.
- Static Library를 가져다 쓰려면 라이브러리와 앱의 소스코드 파일을 병합(Merge)하는 Link 작업이 필요하다.
<img width="635" alt="image" src="https://github.com/user-attachments/assets/463ba510-a1f4-4105-a47b-229fabada98a">


- 이 때 Static Linker를 사용해 앱의 Source files와 Static Libraries를 merge하게 된다.
- 이 파일들을 받아서 단일 파일로 결합해주는 역할을 한다.
<img width="634" alt="image" src="https://github.com/user-attachments/assets/adff9407-c6ba-41cc-ad52-b292e8b66dd3">


- 보통 link 과정은 컴파일 마지막에 일어나기 때문에
- linker는 excitable file을 생성한다고 보면 된다.
<img width="637" alt="image" src="https://github.com/user-attachments/assets/1328a8f8-c3e4-4614-b08c-3c6644ee76f2">


- 앱의 소스 코드는 excutable file 내부에 복사되게 된다.
- 그리고 static libraries 코드 역시 executable file에 복사된다.
- static library가 excitable file의 일부가 되기 때문에 앱이 실행되면 앱 소스코드 + static library 코드를 포함하는 것들이 앱의 주소 공간에 로드된다.
<img width="633" alt="image" src="https://github.com/user-attachments/assets/1863ca06-35a6-4322-b525-b349374ec272">


### Static Library Summary

- 앱에 static library를 추가한다.
- 컴파일 타임에 static linker가 library코드 + 앱 코드를 merge하고
- 단일 excitable file을 만든다.
- 앱이 실행되면 library코드 + 앱 코드가 앱 주소 공간에 로드 된다.

### supposition🤔

- 많은 static library를 앱에 link하면 큰 excutable file이 생성된다.
    - excitable file 내부에 static library코드가 복사되기 때문이다.
- 큰 excitable file은 느린 시작시간(Launch Time) + 큰 메모리 공간을 가져간다.
- static library가 업데이트 되면 클라이언트 앱은 개발자가 업데이트된 library와 다시 link 하지 않는 이상 업데이트된 기능을 사용할 수 없다.

### Trouble 🚨

- Static Library가 많아질수록 큰 executable file이 만들어지고, 새 버전이 나오면 또 다시 컴파일해서 Link해줘야 한다.
- 여기서 나온 개념이 Dynamic Library이다.

## Dynamic Library
<img width="638" alt="image" src="https://github.com/user-attachments/assets/b1c58157-396a-4321-b3e3-9230c740e479">
- Dynamic Library 역시 Library이고 Library는 Xcode target의 일부가 아닌 코드 및 데이터 조각을 정의하는 파일이다.

<img width="637" alt="image" src="https://github.com/user-attachments/assets/97a27658-5ecb-404d-a015-acebe562afa3">
- Dynamic Library 역시 Link 프로세스를 거쳐야 한다.
- 결과물이 Static Library와 조금 다르다.
- Linker에 의해 만들어진 Excutable File에 Library 코드가 모두 포함됐던 static과 달리
Dynamic Library에 대한 참조만 Excutable File에 포함된다.
- 참조가 포함된다는 뜻은
    - excutable file에 dynamic library에서 제공하는 함수, 변수, 리소스 등 찾고 사용하는 방법에 대한 정보는 포함되어 있지만 실제 구현 코드는 포함되어있지 않는 것을 의미한다.
    
<img width="636" alt="image" src="https://github.com/user-attachments/assets/b4376bc0-40c7-4d7c-ad2a-1b01239ea13e">
- excutable file과 Link 됐지만 복사가 안 됐다는 점이 가장 중요하다.
- 즉, excutable file의 크기가 Static에 비해 작다.
- Library 코드가 excutable file에 포함이 되어 excutable file이 비대해진다는 점은 해결됐다.
- Library 코드를 참조만 가지고 사용하는 원리
    - Dynamic Library는 앱이 실행될 때 앱 주소 공간에 로드
    1. 앱을 실행함
    2. 앱 코드 + Dynamic library에 대한 참조가 주소공간에 로드된다.
    3. 참조를 이용해 Dynamic Library를 로드한다. 

### supposition🤔

- 참조를 이용한다면 Dynamic Library가 많다면 Library를 가져올 때 시간이 많이 걸릴 것이라는 생각을 할 수 있다.
- Static Library의 특징은 Big Excutable File → 느린 시작시간 + 큰 메모리 공간
- Dynamic Library의 특징은 Static 보다 작은 Excutable File dynamic library를 로드하는 시간이 있고 그 만큼 launch time이 오래 걸리게 된다.
- Static Library는 업데이트된 Library의 기능을 사용하려면 다시 Link를 해야한다.
- Dynamic Library는 그렇지 않고, 컴파일 하지 않고도 업데이트 된 기능을 사용할 수 있게 된다.

### Conclusion

- 모든 iOS, macOS 시스템 라이브러리는 Dynamic이다.
- Dynamic Library의 executable 파일에는 Dynamic library에 정의된 기능 및 리소스에 대한 place holder역할을 하는 symbol, identifier가 포함되어있다.
- 이런 것들은 라이브러리에서 필요한 구성요소의 이름과 위치를 지정한다.
- 런타임에 운영체제의 linker는 이런 참조를 이용하여 Dynamic Library에서 해당 file을 찾아 메모리에 load하게 된다.
- 참조만을 포함하므로 executable file은 전체 라이브러리 코드를 포함하지 않기 때문에 Static 링크에 비해 크기가 더 작게 유지된다.
- 이를 통해 시스템 리소스를 보다 효율적으로 사용할 수 있고 여러 실행파일이 동일한 Dynamic Library를 공유할 수 있는 모듈식 개발, 배포가 용이해진다.
