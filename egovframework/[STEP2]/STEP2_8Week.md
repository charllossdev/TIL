# Week8


# STS setting

## Gradle

+ Mysql
+ MyBatis
+ TomcatServer
+ Tiles
+
```JavaScript
plugins {
	id 'org.springframework.boot' version '2.1.5.RELEASE'
	id 'java'
}

apply plugin: 'io.spring.dependency-management'

group = 'com.example'
version = '0.0.1-SNAPSHOT'
sourceCompatibility = '1.8'

configurations {
	developmentOnly
	runtimeClasspath {
		extendsFrom developmentOnly
	}
}

repositories {
	mavenCentral()
}

dependencies {
	implementation 'org.springframework.boot:spring-boot-starter-web'
	implementation 'org.mybatis.spring.boot:mybatis-spring-boot-starter:2.0.1'
	developmentOnly 'org.springframework.boot:spring-boot-devtools'
	runtimeOnly 'mysql:mysql-connector-java'
	testImplementation 'org.springframework.boot:spring-boot-starter-test'
	compile group: 'org.apache.tomcat.embed', name: 'tomcat-embed-jasper', version: '9.0.19'
	compile group: 'javax.servlet', name: 'jstl', version: '1.2'
	compile group: 'org.apache.tiles', name: 'tiles-servlet', version: '3.0.8'
	compile group: 'org.apache.tiles', name: 'tiles-extras', version: '3.0.8'
	compile group: 'org.apache.tiles', name: 'tiles-jsp', version: '3.0.8'
}

```

## application.property

EgovFramework - Mybatis 설정 관련

  + Context-datasource.xml
  + Context-Mapper.xml

```JavaScript
spring.mvc.view.prefix=/WEB-INF/jsp
spring.mvc.view.suffix=.jsp

spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
spring.datasource.url=jdbc:mysql://localhost:3306/test?serverTimezone=UTC
spring.datasource.username=root
spring.datasource.password=root

mybatis.mapper-locations=classpath:mapper/**/*.xml
```


# EgovFramwork

## JSTL - c:out

 c:out을 써야 하는 이유
 보안 - script를 방지

- escapeXml 속성 : Default = true
```JavaScript
<c:out value ="${scriptTag}" escapeXml="false" />
```

## SQL - ParameterTYpe =String

```SQL
<select id="selectWelcomeWebStringServiceList" parameterType="String" resultType="egovMap">

  SELECT format(@rownum := @rownum + 1, 0) num
         ,A.*
    FROM (
          SELECT ur.user_id
                ,ur.user_nm
                ,ur.age
                ,ur.cafe_nick
                ,ur.phone
                ,gs.class_nm
                ,gs.gisu_nm
                ,gs.jucha_nm
            FROM t_user ur
            JOIN t_gisu gs
              ON ur.user_id = gs.user_id

           UNION ALL
          SELECT ur.user_id
                ,ur.user_nm
                ,ur.age
                ,ur.cafe_nick
                ,ur.phone
                ,'생존전략' class_nm
                ,'없음' gisu_nm
                ,'없음' jucha_nm
            FROM t_user ur
           WHERE NOT EXISTS (SELECT user_id
                               FROM t_gisu
                              WHERE user_id = ur.user_id)
          ) A
          ,(SELECT @rownum := 0) rnum
  <where>
    <if test='_parameter != null'>
      A.age = #{_parameter}
    </if>
  </where>		        
</select>
```

```SQL
<if test='_parameter != null'>
  A.age = #{_parameter}
</if>

<if test='value != null'>
  A.age = #{value}
</if>
```
파라메터 타입이 string 일 경우에 파타메터는 반드시 1개일 것이고,
if가 있을 경우 반드시 _paraemter or value_
