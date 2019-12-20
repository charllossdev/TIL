# Maria DB Connection

<div id=db></div>
DB - mariadb Setting

## pom.xml

Dependency Injection

```xml
<dependency>
    <groupId>com.googlecode.log4jdbc</groupId>
    <artifactId>log4jdbc</artifactId>
    <version>1.2</version>
    <exclusions>
        <exclusion>
            <artifactId>slf4j-api</artifactId>
            <groupId>org.slf4j</groupId>
        </exclusion>
    </exclusions>
</dependency>

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
## context-mapper.xml
Mapper 경로 설정 변경 필요

```XML

<!-- MapperConfigurer setup for MyBatis Database Layer with @Mapper("deptMapper") in DeptMapper Interface -->
<bean class="egovframework.rte.psl.dataaccess.mapper.MapperConfigurer">
  <property name="basePackage" value="egovframework.example.**.service.impl" />
</bean>

```

### SQL.xml 동적 폴더경로 설정하기 (2019-10-01 Step3-Week6)

```xml
		<property name="mapperLocations" value="classpath:/egovframework/sqlmap/example/mappers/**/*.xml" />

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
