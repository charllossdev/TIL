# Make Test Loop SP


```sql
SET CURRENT SCHEMA = PARK1;

SET CURRENT PATH = SYSIBM,SYSFUN,SYSPROC,SYSIBMADM,PARK1;

CREATE OR REPLACE PROCEDURE PARK1.SCJR_TEST_LOOP_SP (IN p_loop_end double )
  DYNAMIC RESULT SETS 1
  LANGUAGE SQL
  NOT DETERMINISTIC
  EXTERNAL ACTION
  MODIFIES SQL DATA
  CALLED ON NULL INPUT
  INHERIT SPECIAL REGISTERS
  OLD SAVEPOINT LEVEL
/******************************************************************************************
  *
  *   스케줄러 테스트 루프 SP
  *
  *   작성일      : 2019-08-01
  *
  *   Parameter : X
  *
  *   return    : X
  *
  ******************************************************************************************/
BEGIN

    DECLARE v_temp    double DEFAULT 0;
    DECLARE v_current double DEFAULT 0;
    DECLARE p_sum     double;

    WHILE (v_current <= p_loop_end) DO
        SET v_temp = v_temp + v_current;
        SET v_current = v_current + 1;
        select v_current into v_current from  sysibm.sysdummy1;
    END WHILE;

    SET p_sum = v_temp;

END;

 ```
