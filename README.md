# 스프링 부트와 AWS로 혼자 구현하는 웹 서비스

<img src="http://image.yes24.com/goods/83849117/XL.png" width="200" height="300"/>

출처 : http://www.yes24.com/Product/Goods/83849117

<br>

## 2022-09-29

### 1장 

#### 호기심 : 그래이들에 적혀있는 코드를 잘 모르겠다.

* 그래이들은 라이브러리의 추가를 도와주고, 라이브러리의 버전을 쉽게 동기화하기 위해 등장했다.
* buildscript 메소드 : 빌드 스크립트 자체를 빌드하는 과정에서 필요한 라이브러리를 클래스패스에 추가시킨다.
* repositories 메소드 : 저장소의 설정을 담당한다. 라이브러리들을 어떤 원격 저장소에서 받을 지를 정한다.
* ext 메소드 : build.gradle에서 사용되는 전역변수를 설정한다.
* dependencies 메소드 : 프로젝트 개발에 필요한 의존성들을 선언하는 곳이다.
* apply plugin : Gradle 플러그인을 사용하기 위한 것이다. -> 특히 io.spring.dependeny-management 플러그인은 스프링 부트의 의존성들을 관리해는 플러그인이라 꼭 추가해야 한다.

참고 자료 : https://codecrafting.tistory.com/1
