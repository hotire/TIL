# Gradle

![gradle](img/gradle.png)

Grooby 기반의 빌드 도구이다. 


### Task
실행할 처리를 모아놓은 단위로 그레이들에 처음부터 포함된 것도 있고, 프로그래머가 커스텀할 수도 있다.
테스크를 실행하는 것이 그레이들에서 빌드를 관리하는 기본적인 방법이다. (프로젝트를 컴파일, 실행하는 모든처리에 테스크를 이용한다.)


### build.gradle
그레이들은 build.gradle에 기술된 코드를 필요에 따라 실행하여 빌드를 실행한다. 



### Build Life Cycle

- 초기화 : 빌드 대상 프로젝트를 결정하고 각각에 대한 Project 객체를 생성. settings.gradle 파일에 프로젝트 구성

- 구성 : 빌드 대상이 되는 모든 프로젝트의 빌드 스크립트를 실행

- 실행 : 구성 단계에서 생성하고 생성된 프로젝트의 테스트 중에 실행 대상 결정. gradle 명령행에서 지정한 테스크  이름 인자와 현재 디렉토리를 기반으로 테스크를 결정하여 선택된 Task들을 실행

  

  https://www.egovframe.go.kr/wiki/doku.php?id=egovframework:dev3.6:dep:build_tool:gradle



### 테스트 실행하기

build.gradle 다음과 같이 수정해보자. 



```groovy
task hello {
    doLast {
        println();
        println("******************");
        println("Welcom to Gradle");
        println("******************");
        println();
    }
}
```



수정 후 명령행에서 다음과 같이 실행한다. 

```
gradle hello
```

```
> Task :hello

******************
Welcom to Gradle
******************


BUILD SUCCESSFUL in 869ms
1 actionable task: 1 executed
```



- quiet 모드로 실행하기 

  오직 task 안의 내용만을 실행하고 싶을 경우 

  ```
  gradle -q hello
  ```

  ```
  ******************
  Welcom to Gradle
  ******************
  ```

  

### 액션 리스트

hello 예제에서 doLast가 포함되어있다. doLast는 테스크의 액션 리스트 마지막에 처리를 추가한다. 

테스크는 다양한 '액션'을 내부에 가지고 있다. 테스크를 실행하면 준비된 액션이 순서대로 실행된다.

이 액션들을 관리하는 것이 액션 리스트이다. (doFirst / doLast) 

액션 중에서 doFirst, doLast가 가장 많이 사용된다. 

- doFirst : 처음에 실행되는 액션
- doLast : 마지막에 실행되는 액션


### 매개변수 이용

매개변수에서 전달되는 값을 프로퍼피토 사용할 수 있다. 단 'String'이다. 

'-P프로퍼티=값'형태로 특정 변수에 값을 전달할 수 있다.  

```
gradle parameter -q -Pnum=100
```

```
total :5050
```

### 동적 태스크 생성 

```
task "$ 변수" {...처리...} 
```

다음과 같이 스크립트를 사용해서 동적으로 태스크를 생성할 수 있다. 


```
gradle -q one
```

```
this is one task.
```

### gradle java와 gradle build

gradle java는 자바 프로그램의 빌드를 수행하지만, gradle build는 어떤 언어라도 프로젝트를 빌드한다.

그레들은 자바 이외에도 그루비나 스칼라 등 많은 언어를 지원하고 각각의 언어에서 빌드를 수행하는 플러그인을 제공한다.








