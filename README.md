# 스프링 부트와 AWS로 혼자 구현하는 웹 서비스

<img src="http://image.yes24.com/goods/83849117/XL.png" width="200" height="300"/>

출처 : http://www.yes24.com/Product/Goods/83849117

<br>

## 2022-09-29

### 1장 : 인텔리제이로 스프링 부트 시작하기

#### 호기심 : 그래이들에 적혀있는 코드를 잘 모르겠다.

* 그래이들은 라이브러리의 추가를 도와주고, 라이브러리의 버전을 쉽게 동기화하기 위해 등장했다.
* buildscript 메소드 : 빌드 스크립트 자체를 빌드하는 과정에서 필요한 라이브러리를 클래스패스에 추가시킨다.
* repositories 메소드 : 저장소의 설정을 담당한다. 라이브러리들을 어떤 원격 저장소에서 받을 지를 정한다.
* ext 메소드 : build.gradle에서 사용되는 전역변수를 설정한다.
* dependencies 메소드 : 프로젝트 개발에 필요한 의존성들을 선언하는 곳이다.
* apply plugin : Gradle 플러그인을 사용하기 위한 것이다. -> 특히 io.spring.dependeny-management 플러그인은 스프링 부트의 의존성들을 관리해는 플러그인이라 꼭 추가해야 한다.

참고 자료 : https://codecrafting.tistory.com/1

<br>

#### 호기심 : 그래이들 관련 기본 구조

* gradlew : 리눅스 또는 맥OS용 실행 쉘 스크립트 파일이다.
* gradlew.bat : 윈도우용 실행 배치 스크립트 파일이다.
* gradle-wrapper.jar : JAR 형식으로 압축된 Wrapper 파일이다. gradlew나 gradlew.bat파일이 프로젝트 안에 설치되는 이 파일을 사용하여 Gradle task를 실행한다.
* gradle-wrapper.properties : Gradle Wrapper 설정 정보 파일이다. Wrapper의 버전 등을 설정할 수 있다.
* build.gradle : 프로젝트의 라이브러리 의존성, 플러그인, 라이브러리 저장소 등을 설정할 수 있는 빌드 스크립트 파일이다.
* settings.gradle : 프로젝트의 구성 정보 파일이다. 멀티 프로젝트를 구성하여 프로젝트를 모듈화할 경우, 하위 프로젝트의 구성을 설정할 수 있다.

참고 자료 : https://limdevbasic.tistory.com/12

<br>

### 2장 : 스프링 부트에서 테스트 코드를 작성하자

#### 차이점 : @RunWith와 @ExtendWith

> @RunWith(SpringRunner.class)
* 테스트를 시작할 때 JUnit에 내장된 실행자 외에 다른 실행자를 실행시킨다.
* 여기서는 SpringRunner라는 스프링 실행자를 사용한다.
* 즉, 스프링 부트 테스트와 JUnit 사이에 연결자 역할을 한다.

> @ExtendWith(SpringExtension.class)
* JUnit5가 되면서 @RunWith 에서 @ExtendWith로 변경되었다.
* JUnit5에서는 @SpringBootTest 애노테이션이 메타 애노테이션으로 가지고 있다.

<br>

#### 의문점 : @WebMvcTest가 단위 테스트인가?

* @WebMvcTest는 스프링 컨텍스트를 완전하게 실행시키지 않고, Present Layer에 관련된 컴포넌트만 스캔을 하기 때문에 단위 테스트라 볼 수 있다. 만약 서비스나 레포지토리가 필요할 시에는 @MockBean으로 주입 받아서 테스트를 진행한다.

참고 자료 : https://gom20.tistory.com/123

<br>

#### 차이점 : @InjectMocks VS @Mock VS @MockBean

* @Mock : 테스트 클래스 위에 @ExtendWith(MockitoExtension.class)를 붙여줘야 한다.
* @InjectMocks : @Mock으로 만들어진 인스턴스들을 자동으로 주입해준다.
* @MockBean : @MockBean이 붙으면 mock 객체를 스프링 컨텍스트에 등록하게 된다. 그 후, @Autowired로 스프링 컨텍스트에 등록된 mock 객체들을 주입받아서 의존성 처리를 해준다. -> 스프링 컨텍스트에 등록을 하는 것이므로 @SpringBootTest를 통해 테스트를 할 때 사용된다.

참고 자료 : https://giron.tistory.com/115

<br>

#### 새로 알게된 부가적인 내용

* Jar파일은 스프링 부트로 만들어졌다.
* 톰캣은 서블릿으로 이루어진 자바 애플리케이션이다.

<br>

#### 인상 깊은 구절

* 단위 테스트는 계발단계 초기에 문제를 발견하게 도와줍니다.
* 단위 테스트는 개발자가 나중에 코드를 리팩토링하거나 라이브러리 업그레이드 등에서 기존 기능이 올바르게 작동하는지 확인할 수 있습니다.(예, 회귀 테스트)
* 단위 테스트는 기능에 대한 불확실성을 감소시킬 수 있습니다.
* 단위 테스트는 시스템에 대한 실제 문서를 제공합니다. 즉, 단위 테스트 자체가 문서로 사용할 수 있습니다.
* 브라우저로 한 번씩 검증을 하시되, 테스트 코드는 꼭 따라 해야 합니다. 그래야만 견고한 소프트웨어를 만드는 역량이 성장할 수 있습니다.
* 절대 수동으로 검증하고 테스트 코드를 작성하지 않습니다.
