# 카플래너 관련 장애 이슈


# 2020.07.17
## MG서버 네트워크 장애 이슈
org.springframework.web.client.ResourceAccessException

Java에서 발생하는 ValidatorException 에러로, keysotre에 SSL/TLS 인증서를 Import 시켜 해결할 수 있다.

### 증상
```java
org.springframework.web.client.ResourceAccessException: I/O error on POST request for "https://hmp.mggeneralins.com:443/CONTBIZCARDR.form": sun.security.validator.ValidatorException: PKIX path building failed: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target;
```

### 원인
다음과 같이 여러 가지 원인이 있을 수 있다.

1. 연결하려는 remote site의 인증서가 신뢰하는 인증기관 인증서 목록(keystore)에 없음
2. 서버/클라이언트 간 사용하려는 SSL/TLS버전이 맞지 않음(Ex: TLS 1.0 만 지원하는 서버에 1.2로 hand shaking 요청 등)
3. SSL/TLS 통신에 사용하려는 cipher suite가 오래되거나 지원핮 않음. (Ex: JDK 1.8 부터는 RC4를 사용하려고 하면 에러 발생)
4. 웹 브러우저의 경우 인증서 경로 설정을 참고하여 웹 서버에 Intermediate CA certificate 를 설치한다.

### 해결
장애의 원인은 1번 사항으로 구동되는 JDK의 keystroe에 상대방의 인증서를 등록해주면 해결된다.

> JDK나 JRE가 Update 될 경우 인증서 등록을 다시 해야 한다.

#### CMD

1. gist에서 InstallCert.java를 다운로드
```CMD
curl -O https://gist.githubusercontent.com/lesstif/cd26f57b7cfd2cd55241b20e05b5cd93/raw/InstallCert.java
```

2. 다운받은 자바 파일 컴파일
```CMD
javac InstallCert.java
```

3. InstallCert 구동
```BASH
# localhost 에 SSL 인증서를 받아올 호스트명을 입력
# ex) java -cp ./ InstallCert  lesstif.com
java -cp ./ InstallCert TARGET_HOST_URL
```

4. 다음과 같은 화면이 나오면, 구동한 결과를 1을 눌러 저장

```py
ssl import
Caused by: java.lang.UnsupportedOperationException
at InstallCert$SavingTrustManager.getAcceptedIssuers(InstallCert.java:183)
at sun.security.ssl.AbstractTrustManagerWrapper.checkAlgorithmConstraints(SSLContextImpl.java:926)
at sun.security.ssl.AbstractTrustManagerWrapper.checkAdditionalTrust(SSLContextImpl.java:872)
...

Server sent 2 certificate(s):

1 Subject CN=wiki.modernpug.org
Issuer CN=Let's Encrypt Authority X3, O=Let's Encrypt, C=US
sha1 47 0a 15 c4 5d ed 62 0a 4b 18 d5 d8 58 14 42 5d 36 e0 d5 8f
md5 3a 0d ab ce 27 be dd bd e5 c1 d5 e8 b6 25 aa eb

2 Subject CN=Let's Encrypt Authority X3, O=Let's Encrypt, C=US
Issuer CN=DST Root CA X3, O=Digital Signature Trust Co.
sha1 e6 a3 b4 5b 06 2d 50 9b 33 82 28 2d 19 6e fe 97 d5 95 6c cb
md5 b1 54 09 27 4f 54 ad 8f 02 3d 3b 85 a5 ec ec 5d

Enter certificate to add to trusted keystore or 'q' to quit: [1]
2
```
서버가 2 개의 인증서를 전송했는데 2번째가 Let's Encrypt 의 CA 인증서이므로 2번을 선택해서 저장해야 한다.

5. 다음과 같은 메세지가 나오고 저장됨. keystore명과 alias명을 기억
```py
Added certificate to keystore 'jssecacerts' using alias 'letsencrypt'
```

6. keytool로 keystore에서 인증서 추출(keystore의 암호는 charngeit이라 가정!)

```CMD
## alias 옵션뒤에 위의 alias명 입력
keytool -exportcert -keystore jssecacerts -storepass changeit -file output.cert -alias letsencrypt
```

7. 현재 JDK 의 keystore에 cert import
```CMD
## Java Version & Path Check
## JAVA_HOME=/usr/java/jdk1.8.0_91

keytool -importcert -keystore ${JAVA_HOME}/jre/lib/security/cacerts -storepass changeit -file output.cert -alias letsencrypt
```

> 만약 이미 존재할 경우 삭제<br>
> keytool -delete  -alias letsencrypt -keystore ${JAVA_HOME}/jre/lib/security/cacerts -storepass changeit




관련 해결 링크

* https://www.lesstif.com/system-admin/java-validatorexception-keystore-ssl-tls-import-12451848.html
* http://blog.naver.com/kgj1/220584997842
