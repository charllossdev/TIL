# DB2 Content

DB2

# Categories

0. [DB2 유용한 쿼리](#db2-query)



## db2 query

DB2 의 유용한 쿼리

1. DB 에서 에러 발생하는 경우.
   DB2 QUERY 수행시 에러가 발생하면 SQLCODE 는 음수값을 가지게 되어있습니다.
   에러가 어떤 에러인지 확인하려면, 예를 들어 -803 에러가 났다면.
   SQL0803과 같이 음수를 빼고 4자리를 만들어 넣으면 확인이 가능합니다.

   - 참조) Data Not Found 는 에러가 아니죠? 데이터가 없을 경우 DBMS 는 100 이라는
		SQLCODE 를 반환합니다. 그래서, 정상적인 쿼리 일 경우
		(자바에서는 Exception 으로 처리하지만)
		음수가 아니고 100 이 아닌 경우 정상적으로 결과를 확인할 수 있습니다.



2. 처음 100건을 추출하려면..
   -  select * from ftb.tcod FETCH FIRST 100 ROWS ONLY
   이와같이 FETCH FIRST 100 ROWS ONLY 를 넣으면 됩니다.



3. FOR FETCH ONLY, FOR READ ONLY 이란..?
    - DB2 는 기본적으로 조회를 하면 READ LOCK 이라는 LOCK 을 걸게 됩니다.
   위의 옵션을 주면 LOCK 을 잡지 않고 조회를 합니다.
   이를테면, 명시적으로 DBMS 에게 cursor 가 READ ONLY 라는걸 알려주는거죠.
   자바 쪽 배치에는 현재 빠져있는 query 도 많을 거에요..
   only select 라면 틈틈이 추가해주는 것도 좋을 겁니다.
   이 두가지는 비슷한 거에요.



4. WITH UR 이란?
    - query 를 보다 보면 with UR 이 붙은 쿼리를 많이 볼 수 있을 것입니다.
   UR 이란 Isolation level 중 하나로서 Uncommitted Read 의 약어 입니다.
   기본적으로 내가 조회하고자 하는 table 의 다른 트랜잭션이 진행중일때
   대기하다가 커밋,롤백이 되는 경우에 조회할 수 있지요.
   그러나 WITH UR 이 옵션을 붙이면 대기하지 않고 실시간으로 변경중인 데이터를
   가져올 수 있습니다.
   단점은.. 커밋이 안된 데이터를 가져오므로 신뢰성 보장을 못한다.
   그러므로, 단순조회일 경우엔 넣고 꼭 신뢰성보장이 되어야 하는 경우 넣지 않는다.



5. table 속성 조회.
    - describe table ftb.tmbr show detail;



6. table index 조회
    - describe indexes for table ftb.tmbr show detail



7. EXISTS 를 사용하기.
    - 만약 BK1 이라는 회원이 2007년에 BC 카드를 사용하여 마일리지를 적립한 적이 있는가?
   라는 쿼리를 짜야한다고 생각해보죠.
   EXISTS 를 사용하면 생각보다 빠르게 처리할 수 있습니다.
   SELECT 1 FROM SYSIBM.SYSDUMMY1
   WHERE EXISTS (
     SELECT MBR_NO FROM FTB.TALNC_CARD_ACTL
     WHERE MBR_NO = 'BK1' AND ALNC_C = 'BC' AND
     ENTRY_D BETWEEN '2007-01-01' AND '2007-12-31') FOR READ ONLY WITH UR;
   이런식으로 쿼리를 만들게 되면 조건에 맞는 데이터 한 건이라도 나오면 바로 쿼리를 종료하게
   됩니다.
   반대는 NOT EXISTS 입니다. SYSIBM.SYSDUMMY1 는 DB2 의 dummy table 입니다.



8. 조회시 NULL 값 Handling. (VALUE)
    - SELECT MIN(USE_D) USE_D FROM FTB.TALNC_CARD_ACTL_EFF  WHERE MBR_NO = 'BK71461113';
    SELECT VALUE(MIN(USE_D),'0001-01-01') USE_D FROM FTB.TALNC_CARD_YR_SUMM  WHERE MBR_NO = 'BK00000011';



9. 분기 및 값 치환 (CASE WHEN ~ THEN ~ END)
    - Case When e1 is not null then e1 else e2 end  == Coalesce(e1,e2)
    Case When e1 is not null then e1 else Coalesce(e2,....,eN) end == Coalesce(e1,e2,....,eN)
