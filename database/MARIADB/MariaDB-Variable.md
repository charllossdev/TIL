# MariaDB Variable

MariaDB 변수 선언 및 활용방법

```SQL
SELECT *
  FROM (
        SELECT A.*
             , FLOOR(A.RNUM - 1) / #{rows}) + 1  						AS PAGE_NUMBER
          FROM (
                SELECT BNNR_MNG_NO
                     , SUBJ
                     , BNNR_TP
                     , CONCAT(DP_STRT_DT, ' ~ ', DP_END_DT ) DP_GIGAN
                     , BG_IMG_ATTC_FILE
                     <![CDATA[
                     , CASE
                          WHEN NOW() BETWEEN DP_STRT_DT AND DATE_ADD(DP_END_DT, INTERVAL 1 DAY) THEN '진 행 중'
                          WHEN NOW() < DP_STRT_DT                                               THEN '대 기 중'
                          WHEN NOW() > DATE_ADD(DP_END_DT, INTERVAL 1 DAY)                      THEN '마 감'
                       END STATUS
                      ]]>
                     , DP_YN
                     , REGR
                     , DATE_FORMAT(DATE(REG_DT), '%Y. %m. %d') 					AS REG_DT
                     , @ROWNUM := @ROWNUM + 1									AS RNUM
                     , (SELECT COUNT(*) FROM T_DP_BNNR_MNG)						AS TOTAL_CNT
                     , (SELECT CEIL(COUNT(*) / #{rows}) FROM T_DP_BNNR_MNG)		AS TOTAL_PAGE
                  FROM t_dp_bnnr_mng
                     , (SELECT @ROWNUM := 0) R
          ) A
  ) B
 WHERE B.PAGE_NUMBER = #{page}
```


## 변수 선언

변수를 선언하는 방법은 FROM 절에서 한다.
* 초기값을 설정해주어야 한다.
* 반드시 별칭을 붙어주어야 한다.

```SQL

SELECT *
    FROM T_DP_BNNR_MNG
        , (SELECT @ROWNUM :=0) R
```
