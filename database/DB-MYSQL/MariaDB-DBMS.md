# MariaDB
* [MariaDb](#mariadb)
* [MariaDB 특징](#mariadb-특징)
* [MariaDB License](#mariadb-license)


<img src="./img/MariaDB_logo.PNG"  width="150">

MariaDB는 오픈 소스의 관계형 데이터베이스 관리 시스템(RDBMS)이다. MySQL과 동일한 소스 코드를 기반으로 하며, GPL v2 라이선스를 따른다. 오라클 소유의 현재 불확실한 MySQL의 라이센스 상태에 반발하여 만들어졌으며, 배포자는 몬티 프로그램 AB(Monty Program AB)와 저작권을 공유해야 한다.

이것은 MySQL과 높은 호환성을 유지하기 위함이며, MySQL API와 명령에 정확히 매칭하여, 라이브러리 바이너리와 상응함을 제공하여 교체 가능성을 높이고자 함이다.

마리아 DB에는 새로운 저장 엔진인 아리아(Aria)뿐만 아니라, InnoDB를 교체할 수 있는 XtraDB 저장 엔진을 포함하고 있다. 이것은 트랜잭션과 비트랜잭션 엔진 그리고 미래에 나올 MySQL 판에 대응하고자 함일 것이다.

마리아 DB의 주요 개발자는 MySQL과 몬티 프로그램 AB를 설립한 몬티 와이드니어스(Michael Monty Widenius)이다. 그는 이전에 자신의 회사, MySQL AB를 썬 마이크로시스템즈에 10억 달러에 판매를 한 적이 있으며, 마리아 DB는 그의 둘째 딸인 마리아의 이름을 딴 것이다.

[사이트 : https://mariadb.com/](https://mariadb.com/)

## MariaDB 특징

마리아DB는 MySQL과 소스코드를 같이 하므로 사용방법과 구조가 MySQL과 동일하다.[10] 이름만 다르지 명령어나 사용방법 (5.5까지) 모두 MySQL과 동일하다. 편의를 위해 마리아DB는 동일한 MySQL 버전과 바이너리 드롭인 교체를 지원한다. 예를 들어, MySQL 5.1은 마리아DB 5.1과 5.2, 5.3과 호환된다. MySQL 5.5는 마리아DB 5.5와 호환되는 식이다.

* 데이터와 테이블 정의 파일(.frm) 파일이 바이너리 호환이 된다.
* 모든 클라이언트 API, 프로토콜 그리고 구조가 동일하다
* 모든 파일이름과 바이너리, 경로, 포트, 소켓 그리고 기타 등등이 동일하다.
* 모든 MySQL 커넥터(PHP, Perl, 파이썬, 자바, .NET, MyODBC, Ruby, MySQL C 코넥터 등)가 마리아 DB와 동일하게 작동한다.
* 마리아DB 커뮤니티는 MySQL과 비교해 애플리케이션 부분 속도가 약 4~5천배 정도 빠르며, MySQL이 가지고 있는 모든 제품의 기능을 완벽히 구현하면서도 성능 면에서는 최고 70%의 향상을 보이고 있다고 주장한다.

## MariaDB License

근본적인 차이점은 마리아DB는 GPL v2 라이선스를 따르는 순수한 오픈소스 프로젝트이기에 오라클로부터 자유롭다. 마리아DB의 모든 코드는 GPL, LGPL, LPGL, BSD의 라이선스로 만들어져 있다. 누구나 필요로 하면 커뮤니티를 통해 마리아DB를 내려받아 쓸 수 있다.
