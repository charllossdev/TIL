# Eclipse Server Timeout Error
 가끔 이클립스(Eclipse) 개발 환경에서 자바(Java) 개발을 하다 보면, 45초 서버 실행(Server Start) 제한 때문에 오류가 발생할 때가 있습니다. 45초 이내에 서버가 시작이 안 되면 문제가 있다고 보기 때문이에요. 다만 서버에 이것저것 라이브러리를 추가하다 보니까 어쩔 수 없이 서버가 실행되기까지 45초가 넘어가는 경우도 존재합니다. 그럴 때 45초 제한을 해제하는 방법을 알려드리고자 합니다.

![](assets/2020-05-25-eclipse-server-timeout-error-c24a86c2.png)

> 오류 메시지: Server Tomcat v8.5 Server at localhost was unable to start within 45 seconds. If the server requires more time, try increasing the timeout in the server editor.


# Solution

![](assets/2020-05-25-eclipse-server-timeout-error-edad1391.png)

> Timeout 시간 설정을 변경
