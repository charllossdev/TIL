
# Gradle Setting

  1. Check Gradle Install Y&N
  ![](assets/Gredle-Setting-4af516d5.png)
  2. Delete Gradle Set
  ![](assets/Gredle-Setting-96b8757b.png)
  3. Install Gradle
  ![](assets/Gredle-Setting-100cc5a9.png)
  ![](assets/Gredle-Setting-07166425.png)
  4. Add Gradle View
  ![](assets/Gredle-Setting-32929417.png)
  5. Gradle Location Setting
  ![](assets/Gredle-Setting-43bbf1dd.png)
  6. Make Gradle files
  ![](assets/Gredle-Setting-f832675a.png)
  ![](assets/Gredle-Setting-e5778676.png)
  7. Setting Gradle Add Dependency Config
  ```JAVASCRIPT
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
  	implementation 'org.springframework.boot:spring-boot-starter-web-services'
  	implementation 'org.mybatis.spring.boot:mybatis-spring-boot-starter:2.0.1'
  	developmentOnly 'org.springframework.boot:spring-boot-devtools'
  	runtimeOnly 'mysql:mysql-connector-java'
  	testImplementation 'org.springframework.boot:spring-boot-starter-test'
  }

  ```
  8. Disabled Marven Nature
  ![](assets/Gredle-Setting-e6e533c7.png)
  9. Add Gradle Nature
  ![](assets/Gredle-Setting-c18cb27c.png)
  10. Add Deployment Assembly
  ![](assets/Gredle-Setting-000e598b.png)
  ![](assets/Gredle-Setting-7c489f23.png)
