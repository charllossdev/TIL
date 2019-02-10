# Project XML Setting

# 타일즈 설정

<div id=tiles></div>

Tiles Import Path
```Javascript
	<%@ taglib uri="http://tiles.apache.org/tags-tiles" prefix="tiles"%>
```

## pom.XML
```xml
<properties>
	    <spring.maven.artifact.version>4.1.2.RELEASE</spring.maven.artifact.version>
		<egovframework.rte.version>3.6.0</egovframework.rte.version>
		<org.apache.tiles-version>3.0.8</org.apache.tiles-version>
	</properties>
```

```xml
<!-- 타일즈 -->
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

<dependency>
    <groupId>commons-dbcp</groupId>
    <artifactId>commons-dbcp</artifactId>
    <version>1.4</version>
</dependency>
```
## dispatcher-servlet.xml

viewResolver 우선순위 변경 1 -> 2로 변경
```xml
<bean class="org.springframework.web.servlet.view.UrlBasedViewResolver" p:order="2"
  p:viewClass="org.springframework.web.servlet.view.JstlView"
  p:prefix="/WEB-INF/jsp/egovframework/example/" p:suffix=".jsp"/>
```

타일즈 우선순위를 1로 변경 및 타일즈 경로 설정

```xml

<!-- 타일즈 viewResolver -->
<bean id="tilesViewResolver" class="org.springframework.web.servlet.view.UrlBasedViewResolver">
<property name="viewClass" value="org.springframework.web.servlet.view.tiles3.TilesView" />
<property name="order" value="1" />
</bean>

<!-- Tiles 3 Configurer -->
<bean id="tilesConfigurer" class="org.springframework.web.servlet.view.tiles3.TilesConfigurer">
<property name="definitions">
  <list>
      <value>/WEB-INF/tiles/default-layout.xml</value>
  </list>
</property>
</bean>
```

> Tiles 3 Configurer Setting File Path Create 'default-layout.xml'



# 인터셉터

<div id=interceptor></div>

## dispatcher-servlet.xml

인터셉터 경로 설정

```xml
<mvc:interceptors>
  <mvc:interceptor>
    <mvc:mapping path="/**"/>
    <bean class="egovframework.example.cmmn.Interceptor" />
  </mvc:interceptor>
</mvc:interceptors>
```

## 그 외

```xml
<!-- gson -->
<dependency>
    <groupId>com.google.code.gson</groupId>
    <artifactId>gson</artifactId>
    <version>2.8.2</version>
</dependency>

<!-- 암호화 -->
<dependency>
    <groupId>org.apache.directory.studio</groupId>
    <artifactId>org.apache.commons.codec</artifactId>
    <version>1.8</version>
</dependency>

<!--  gmail 서비스 -->
<dependency>
	<groupId>javax.mail</groupId>
	<artifactId>mail</artifactId>
	<version>1.4</version>
</dependency>

<!-- 빈문자열 + null 체크를 한번에 -->
<dependency>
	<groupId>org.apache.commons</groupId>
	<artifactId>commons-lang3</artifactId>
	<version>3.8</version>
</dependency>
```

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
