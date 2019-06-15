# 2Week

* [Tiles](#tiles)

# EgovFrameWork - Maven Setting


porm.xml 전자정부 프레임워크를 구동하기 위한 필수 자바 클래스 파일(.jar)들의 모음으로 jar파일의 모음은 Maven이라 하며, Maven Dependencies 에 모여있다.

Maven 설정 <-> gradle 설정
Dependencies 추가 : 인젝션이며 인젝션한 메이븐을 사용하는것을 룩업

```
preference -> Maven User Setting -> Path Rebulid
```


## Jar 파일 경로 재설정
로컬 루트에서 공통 절대 루트로 변경


# EgovFrameWork - Gradle Setting

전자정부 프레임워크 필수 자바 설정 관련하여 방안은 2가지 이다.
1. Maven
2. Gradle

## Install

```
Eclipse - Help - Install SoftWare -
```
Download Path : http://download.eclipse.org/buildship/updates/e45/releases/1.0

## View

```
Eclipse - Show View - Other

Search gradle - > Choice 2two Tag
```

## Setting

Path Setting

```
Eclipse - preference - Grale
```

## Configurator

```
    compile group: 'egovframework.rte', name: 'egovframework.rte.psl.dataaccess', version:'3.6.0'
```

<dependency> 테그와 같다.

## 타일즈 Dependency 와 비교

```
compile group: 'org.apache.tiles', name: 'tiles-jsp', version:'3.0.8'
compile group: 'org.apache.tiles', name: 'tiles-core', version:'3.0.8'
```
같다

```xml
<!-- 타일즈 라이브러리 : 시작 -->		
<dependency>
<groupId>org.apache.tiles</groupId>
<artifactId>tiles-jsp</artifactId>
<version>${org.apache.tiles-version}</version>
</dependency>
<dependency>
<groupId>org.apache.tiles</groupId>
<artifactId>tiles-core</artifactId>
<version>${org.apache.tiles-version}</version>
</dependency>		
<!-- 타일즈 라이브러리 : 끝 -->
```

환경 변수 설정 필요


# Tiles

타일즈의 강점
하나의 타일즈 설정 xml에 여러개의 레이아웃을 설정하여서 관리 및 생성을 할 수 있는 장점

## 설정

porm.xml

1. <properties> 테그 안에 사용할 타일즈와 버전을 선언
2. 타일즈 관련 <dependency> Maven 추가

Dispatcher-Servlet

3. 타일즈 우선 순위 설정(1)
4. 타일즈 설정 파일 경로 추가
5. ViewResolver 우선 순위 변경(1 -> 2)

경로 설정한 타일즈 설정xml(default-layout.xml)

6. 타일즈 생성 및 타일즈 타일 경로 설정
7. 유동적인 타일즈는 상속 받아서 경로 추가
8. 타일즈 전체 레이아웃 설정하는 jsp 설정(default-layout.jsp)
