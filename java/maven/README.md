# Maven

Maven 구성 요소 및 개념
* plugin
* goal
* phase
* lifecycle

## Plugin
* 메이븐에서 제공하는 모든 기능은 플러그인을 기반으로 동작
* 메이븐의 자체는 기본적인 기능만 가지고 있고, 대부분의 기능들은 플러그인을 통해 제공
* 플러그인들은 몇가지 goal을 가지고 있고, goal은 플러그인에 포함되어 있는 명령
  + 즉 플러그인은 하나 이상의 goal 집합체

# Goal
* 메이븐에서 실행해야할 명령
* 메이븐에서 사용하는 기본 명령어
  + mvn [-option][<goal(s)>][<phase(s)>]
* 
