# Match 
![match](https://github.com/user-attachments/assets/5dd0d324-71aa-4c6c-9a2f-fcb464410aaa)


## 코드 서명 인증서와 프로비저닝 프로파일이 필요한 이유
-   iOS는 폐쇄된 보안 생태계를 유지하기 위해 앱을 설치하거나 실행할 수 있는 주체를 통제.
-   해당 통제를 위해 필요한 것이 코드 서명과 프로비저닝 프로파일이다.

## 인증서와 프로비저닝 프로파일

iOS는 폐쇄된 보안 생태계를 유지하기 위해 앱을 설치하거나 실행할 수 있는 주체를 강력하게 통제한다.  
이런 통제를 위해 필요한 것이 바로 코드 서명 인증서와 프로비저닝 프로파일이다.

### 코드 서명 인증서

-   누가 이 앱을 만들었는가
-   신뢰할 수 있는 개발자가 만든 코드임을 입증

### 프로비저닝 프로파일

-   이 앱을 어디에 설치할 수 있는가
-   이 앱이 어떤 기기에서 실행 가능한지 결정

## Match 사용의 이유

-   iOS 개발을 하다보면 팀원도 늘어나고 각자의 로컬 머신에서 인증서를 따로 관리하는 경우가 발생
-   평소에 잘 되다가 **꼭 바쁠 때** 인증서가 만료되고 누락되고 한다.
-   인증서가 만료되고 누락되고 잘못된 프로파일이 사용되는 경우 앱 빌드나 배포에 지장을 준다.
-   Match를 사용하면 공통된 인증서를 하나의 저장소에 보관, 필요 시 자동으로 동기화 해서 사용할 수 있다.

## Match 작동 방식

-   인증서 프로비저닝 프로파일 생성
-   Git Repo에 저장
-   다른 팀원들은 match 명령어로 인증서를 로컬에 설치 가능
-   Fastlane은 Git Repo를 Single Source of Truth로 간주  
    이러한 기능은 팀 전체가 일관된 환경을 유지하는데 큰 도움을 준다.

## 사용 방법

```
fastlane match init
```

-   git url을 물어보는데,
-   인증서와 프로파일 저장할 private repo를 지정하면 된다.

```
fastlane match development
fastlane match appstore
```

-   개발용 또는 앱스토어 배포용 인증서를 생성하고 암호화한 후 Git 저장소에 업로드한다.
-   암호는 .env에 저장하는 것을 추천한다.

## MatchFile 예시

```
git_url(ENV['MATCH_GIT_URL'])
storage_mode("git")
type("development") 
git_branch(ENV['GIT_BRANCH'])
app_identifier(ENV['APP_IDENTIFIER'])
username(ENV['APPLE_ID'])
team_id(ENV['TEAM_ID'])
```

-   .env에 실제 값을 넣어주는 형태로 진행하는 것이 좋다.

## FastFile 예시

```
default_platform(:ios)

platform :ios do
  desc "개발용 인증서 설치"
  lane :setup_dev_cert do
    match(
      type: "development",              
      readonly: true,                   // 읽기 전용 (인증서 생성 안 함)
      git_branch: "certs",              // 인증서 저장된 Git 브랜치
      verbose: true
    )
  end

  desc "배포용 인증서 설치 (App Store)"
  lane :setup_appstore_cert do
    match(
      type: "appstore",               
      readonly: true,
      git_branch: "certs",
      verbose: true
    )
  end

  desc "테스트 플라이트 배포용 인증서 설치"
  lane :setup_testflight_cert do
    match(
      type: "appstore",                
      readonly: true,
      git_branch: "certs",
      verbose: true
    )
  end
end
```

-   브랜치 설정을 꼭 해주는 것이 편하다.
-   처음에 테스트 해볼 때 로컬 키체인에 저장된 것이 실행되는지,실제 repo에서 가져오는 알 방법이 없기 때문에
-   브랜치 설정을 하고 가져오는 게 확실하다
-   처음 생성만 readonly 설정 없이 진행하고 나머지는 꼭 readonly 설정을 해주는 것이 편하다
-   나의 경우는 readonly 설정을 빼먹고 작업을 진행해서 귀찮은 일이 발생했다.

## 결론

-   현재 팀원들은 배포하는 경우 인증서에 대한 생각을 크게 안 한지 좀 됐다.
-   CI/CD는 현재 내가 전담해서 관리하고 있는데, 팀원들이 편하게 쓰는 모습을 보니 기분이 좋다.
-   해당 부분에 대해서 신경을 안 쓰게 되니 여기서 아낀 에너지로 더 열정적으로 일할 수 있다.
-   fastlane, 중계 서버 구현, jenkins에 대한 블로그 글은 추가로 작성할 예정이다.
