# 카플래너 관련 장애 이슈


# 2020.07.17
## MG서버 네트워크 장애 이슈
org.springframework.web.client.ResourceAccessException

Java에서 발생하는 ValidatorException 에러로, keysotre에 SSL/TLS 인증서를 Import 시켜 해결할 수 있다.

### 증상
```java
org.springframework.web.client.ResourceAccessException: I/O error on POST request for "https://hmp.mggeneralins.com:443/CONTBIZCARDR.form": sun.security.validator.ValidatorException: PKIX path building failed: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target; nested exception is javax.net.ssl.SSLHandshakeException: sun.security.validator.ValidatorException: PKIX path building failed: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target
```

### 원인
다음과 같이 여러 가지 원인이 있을 수 있다.

1. 연결하려는 remote site의 인증서가 신뢰하는 인증기관 인증서 목록(keysotre)에 없음
2. 서버/클라이언트 간 사용하려는 SSL/TLS버전이 맞지 않음(Ex: TLS 1.0 만 지원하는 서버에 1.2로 hand shaking 요청 등)
3. SSL/TLS 통신에 사용하려는 cipher suite가 오래되거나 지원핮 않음. (Ex: JDK 1.8 부터는 RC4를 사용하려고 하면 에러 발생)
4. 웹 브러우저의 경우 인증서 경로 설정을 참고하여 웹 서버에 Intermediate CA certificate 를 설치한다.





관련 해결 링크

* https://www.lesstif.com/system-admin/java-validatorexception-keystore-ssl-tls-import-12451848.html
* http://blog.naver.com/kgj1/220584997842
