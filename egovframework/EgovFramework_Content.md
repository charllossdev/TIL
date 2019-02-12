# WEEK1

## 전자정부 프레임워크

![egov_logo](./assets/egov_logo.png)
> - 전자정부 프레임워크는 대표적으로 스프링(spring), 아이바티스(ibatos)등 대표적인 오픈소스를 조합하여 만든 자바 기반의 프레임워크이다.
> - 스프링 프레임워크를 기반으로 하기 때문에 수많은 오픈소스 또는 상용 솔루션 탑재 및 연계를 할 수 있는 범용성이 있다.
> - 닷넷(.NET), php, asp를 위한 프레임워크가 아니로 오로지 Java 기반의 정보시스템(웹, 홈페이지, 하이브리드 앱) 등을 구축하기 위한 개발환경이다.

### 특징
![img_sub01](./assets/img_sub01.png)

### 전자정부 표준 프레임워크 라이센스
[전자정부 표준프레임워크 라이센스](http://www.egovframe.go.kr/EgovLicense.jsp?menu=1&submenu=4)는 Apache License, Version 2.0 을 채택합니다.
단, 표준프레임워크 내에서 사용된 외부 오픈소스의 경우 원 오픈소스의 라이선스 정책을 유지합니다.

### 전자정부 프레임워크 폴더 구조
![folder_java](./assets/folder_java_55mhy03gx.PNG)
- Java
  - 자바코드(컨트롤러, 모델)를 관리 한다.
  - cmmn (공통 업무)
  - main (model controller)
  - sample

![folder_resource](./assets/folder_resource_xkm29gual.PNG)
- resources
  - spring, mapper, sql 자바 코드에서 사용할 리소스를 관리 한다.

![folder_webapp](./assets/folder_webapp_sepe45wdg.PNG)
- webapp
  - View 관련 소스 및 js, jsp, css, image 등등을 관리 한다.
  - jsp를 제외한 js, css, image 등은 webapp의 하위 폴더에 명시 되있다.
  - jsp 폴더의 경로는 webapp/WEB-INF/jsp 로 구성되 있다.
    ![folder_jsp](./assets/folder_jsp.PNG)
  - jsp 폴더 구조와 java 폴더의 구조가 같다.

### 전자정부 프레임워크 흐름
로컬 이클립스에서 톰캣으로 서버를 실행하고, 웹 브라우져에서 http://localhost:8080/first/ 로 접속을 하면 화면에 보여지는 흐름은 이렇다.
1. 이클립스의 톰캣 서버의 설정-module-path 탭에 저장된 path가 입력이 됬는지 확인
2. 톰캣 서버의 localhost-config 폴더안에 context.xml에 <WatchedResource> 테그로 경로로 요청
![watchedResource](./assets/watchedResource.PNG)
3. WEB-INF/web.xml 에 <welcome-file-list> 테그로 웹 요청시 지정한 리소스를 Call
![welcome-file-list](./assets/welcome-file-list.png)
4. jsp 페이지 내에 forward 액션 태그를 만나게 되면, 그전까지 출력 버퍼에 저장되어 있던 내용을 제거하고 forward 액션 태그가 지정하는 page 속성의 논리적 주소로 Get방식 이동
![jsp_forward](./assets/jsp_forward.PNG)
5. Get방식으로 넘겨받은 논리적 주소값이 @RequestMapping 명령어의 Value 속성값과 일치하면 하위 메서드가 실행
![RequestMapping](./assets/requestMapping.png)
6. return 명령어의 지시는 경로/파일이름으로 main.jsp의 논리적 주소로 이동
7. main.jsp로 인해 웹 브라우져에서 view가 보여지게 됩니다.


# Interceptor Setting

```java

package egovframework.example.cmmn;

import java.util.List;

import javax.annotation.Resource;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import org.springframework.web.servlet.ModelAndView;
import org.springframework.web.servlet.handler.HandlerInterceptorAdapter;

import egovframework.example.cmmn.service.CmmnService;
import egovframework.rte.psl.dataaccess.util.EgovMap;

public class Interceptor extends HandlerInterceptorAdapter{
	
	private final Logger log = LoggerFactory.getLogger(getClass());
	
	@Resource
	private CmmnService cmmnService;
	
	@Override
	public void postHandle(HttpServletRequest request, HttpServletResponse response, Object handler,
			ModelAndView modelAndView) throws Exception {
		
		if (!"XMLHttpRequest".equals(request.getHeader("X-Requested-With"))) {
			
			List<EgovMap> menuList = cmmnService.selectMenuList();
			
			log.debug("Debug Intercepter " , menuList.toString());
			
			System.out.println(menuList);
			
			modelAndView.addObject("menuList", menuList);
		}		
	}
}

```



## Logger Setting

```java
private final Logger log = LoggerFactory.getLogger(getClass());
```

> Import org.slf4j.Logger;


---

## Maria DB Connection

# 데이터베이스

<div id=db></div>
DB - mariadb Setting

## pon.xml

```xml
<dependency>
    <groupId>commons-dbcp</groupId>
    <artifactId>commons-dbcp</artifactId>
    <version>1.4</version>
</dependency>

<dependency>
    <groupId>org.mariadb.jdbc</groupId>
    <artifactId>mariadb-java-client</artifactId>
    <version>2.2.1</version>
</dependency>
```


## context-datasource.xml

DB 경로 및 데이터베이스 경로 계정

```XML
<bean id="dataSource" class="org.apache.commons.dbcp.BasicDataSource" destroy-method="close">
  <property name="driverClassName" value="org.mariadb.jdbc.Driver"/>
  <property name="url" value="jdbc:mariadb://localhost:3306/test" />
  <property name="username" value="root"/>
  <property name="password" value="root"/>
</bean>
```

### DB SQL 문

### <selectKey>

parameterType의 VO가 가지고 있는 속성의 변하는 값을 DB에 넣고싶을때 사용하는 설정

```xml
<insert id="insertJoinMbr" parameterType="joinVO">

	<selectKey order="BEFORE" keyProperty="mbrNo" resultType="String">

		SELECT CONCAT('F', LPAD(IFNULL(REPLACE(MAX(MBR_NO), 'F', ''), 0) + 1, 9, 0)) as mbrNo
		FROM T_MBR

	</selectKey>

	INSERT INTO T_MBR
	(
	   MBR_NO
	 , LOGIN_ID
	 , PWD
	 , EMAIL
	 , CP_NO
	 , JOIN_DT
	 , EMAIL_RCP_YN
	 , SMS_RCP_YN
	 , REGR
	 , REG_DT
	 , UPDR
	 , UPD_DT
	)
	VALUES
	(
	   #{mbrNo}
	 , #{loginId}
	 , #{pwd}
	 , #{email}
	 , #{cpNo}
	 , now()
	 , #{emailRcpYn}
	 , #{smsRcpYn}
	 , #{mbrNo}
	 , now()
	 , #{mbrNo}
	 , now()
	)
</insert>
```

### 트랜젝션 설정하기

context-transaction.XML

```XML

<tx:advice id="txAdvice" transaction-manager="txManager">
	<tx:attributes>
		<tx:method name="*Tx" rollback-for="Exception"/>
	</tx:attributes>
</tx:advice>

<aop:config>
	<aop:pointcut id="requiredTx" expression="execution(* egovframework.example.**..impl.*Impl.*(..))"/>
	<aop:advisor advice-ref="txAdvice" pointcut-ref="requiredTx" />
</aop:config>

```