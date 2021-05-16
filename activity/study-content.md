
# Study


## 영상 리스트
도커 소개 https://www.youtube.com/watch?v=hWPv9LMlme8


# 대용량 트래픽 처리
최소한의 아키텍처 구성
API-Server 2개
실제 비즈니스 로직 처리
Load Balancer
Request를 연결된 서버들에게 나누어줌
장애 발생시 해당 LB에게 할당된 IP를 다른 LB에게 넘겨줌
DBMS 2개
primary(실제 서비스)

secondary(데이터 복사)

두대를 두고 primary의 데이터를 secondary로 계속 Replication을 통해 복제한다.

primary에서 장애 발생시 secondary가 primary로 되고, 장애가 해결되도 primary는 secondary 역할을 하게 된다.

마스터, 슬레이브

Object Storage Service (File-Server)
파일을 저장할 서버를 둘 경우 총 3개의 File-server가 필요하다.
3개를 사용할 시 Data Loss : 99.999%가 보장된다.
AWS S3, AZURE Blob, Gcp Google Storage에서 서비스를 제공한다.
하지만 데이터가 많아질 수록 DBMS의 TPS 한계가 온다.

TPS(Transaction Per Second)
초당 몇개의 명령을 처리할 수 있는가
ex) MAX 1000 TPS = 1초에 1000개의 명령을 처리
CPU, 메모리, 디스크 등 하드웨어 적인 부분이 속도에 영향을 미친다.
너무 많은 경우 오래걸리거나 장비가 고장날 수 있다.
대규모 서비스의 특성
Elastic

트래픽이나 상황에 따라서 서버의 추가/제거가 쉬워야 한다.

Resiliency

특정 장비의 장애 등은 자동으로 복구가 되어야 한다.

​ 서버가 복구되는 건 아님

​ 해당 장비의 장애로 인해 다른 쪽이 영향을 받으면 안됨

Scale UP

장비의 성능을 UP

Scale Out

장비의 수를 늘려 성능을 UP

SPOF (Single Point Of Failure)

장애 발생시 서비스 전체를 마비시키는 병목지점

API 서버에 부하가 물리는 작업은 ?

파일 IO가 많은 정적 파일

웹 스크래핑과 같은 디비 작업 자체보다 다른 작업이 많은 작업

독립적인 작입이 가능하지만, CPU나 다른 작업이 많이 필요한 작업 (ex lol, 배그 같은 게임서버)

이미지, 영상 인식, 전처리 작업

DB 서버에 부하가 물리는 작업은 ?

카톡방 대화, 페이스북 댓글, 대부분의 작업

Stateless - API 서버는 비즈니스 로직만 가짐

장점

추가/삭제가 간단 - 주소만 추가/제거로 가능

단점

결국 데이터의 저장이 필요해 뒤로 책임을 떠 넘기는 구조

DB의 경우 일반적인 서버의 부하
800 reads/s , 200 writes/s => Read > Write
읽기의 분배 - Query Off 필요 (Master, Slave 개념)
Slave 장비를 추가해도 한계가 발생 => Database Partitioning
Database Partitioning
Vervical Partitioning
Horizontal Partioning
Sarding Horizontal Partitioning
특정 key를 저장하는 방법, 특정 Key를 찾는 방법

Consistent Hashing - 해쉬 값이 자기보다 크거나 같은 서버들 중 가장 가까운 서버로 KEY가 할당됨
Key만 보고 어떤 서버에서 찾아야 할지 알 수 있나 ?

Unique 해야함
Key만 보고 시간 순을 알 수 있나 ?

UUID (Universally Unique Identifier)
128 bit
36 characters
ex) 123e4567-e89b-12d3-a456-426655440000
UUID의 단점

128 bit는 너무 용량이 큼, 그래서 보통 Shard Id가 들어간다.
shard

자신의 메일 리스트를 저장한 서버 번호

Shard Id와 실제 서버의 매핑
시간 정보가 들어가면 ID 만으로 시간 정렬이 가능
변화하지 않을 특별한 정보를 넣으면 좋음
{TimeStamp}-{ShardId}-{Type}-{seq}
ex) Twitter의 ID : timestamp + datacenter ID + worker ID + sequence

​ instagram의 ID : timestamp + logical shard ID + auto increment

데이터의 Scale Out
Range - 특정 범위대역으로 나누기
Modular - 서버 대수로 나누기 (서버가 추가될 때마다 데이터의 이동이 심해지는 단점)
Indexed - 특정 데이터의 위치를 가리키는 서버가 존재
대용량 서비스 설계 방법
SPOF 제거
오브젝트 스토어
데이터 샤딩
같은 테이블 스키마를 가진 데이터를 다수의 데이터베이스에 분산하여 저장하는 방법을 의미
코디네이터
Circuit Breaker
블루/그린 배포, 카나리 배포
Feature Flag(Switch)
참고

https://12bme.tistory.com/100

https://www.slideshare.net/charsyam2/webservice-scaling-for-newbie
