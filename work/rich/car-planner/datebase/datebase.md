
# 2020.10.07
다이렉트 포인트 즉시 출금 서비스 개발 관련 DB

## 테이블 추가

* 즉시 출금 내역 저장 테이블 추가: INSTANT_WITHDRAW
  ```SQL
  -- carplanner.instant_withdraw definition
  CREATE TABLE `instant_withdraw` (
    `instant_seq` int(11) NOT NULL AUTO_INCREMENT COMMENT 'seqno',
    `acc_hist_seq` int(11) NOT NULL COMMENT 'acc_hist_seq',
    `uid` int(11) NOT NULL COMMENT 'uid',
    `ins_company` char(3) DEFAULT NULL COMMENT '보험사',
    `ins_charge` int(11) DEFAULT NULL COMMENT '보험료',
    `ad_payment` int(11) DEFAULT NULL COMMENT '지급 광고료',
    `insure_file_seqno` varchar(30) NOT NULL COMMENT '보험 증권 파일 enc seq',
    `instant_type` char(2) NOT NULL COMMENT '즉시 출금 구분',
    `instant_status` char(2) NOT NULL COMMENT '즉시 출금 상태',
    `reject_reason` varchar(100) DEFAULT NULL COMMENT '반려 사유',
    `mod_admin_id` varchar(30) DEFAULT NULL COMMENT '담당자',
    `reg_date` datetime NOT NULL COMMENT '등록일',
    `mod_date` datetime DEFAULT NULL COMMENT '수정일',
    `pay_date` datetime DEFAULT NULL COMMENT '지급일',
    PRIMARY KEY (`instant_seq`)
  ) ENGINE=InnoDB AUTO_INCREMENT=10 DEFAULT CHARSET=utf8 COMMENT='즉시 출금 테이블';
  ```

## 공통 코드 추가

* 즉시 출금 타입 추가 INS_TYPE
  ```SQL
  INSERT INTO sys_code_manager
  (group_code, detail_code, expo_name, prnt_order, add_info, use_yn, disp_yn, reg_id, reg_date, mod_id, mod_date)
  VALUES('INS_TYPE', '01', '다이렉트 자동차보험', 1, NULL, 'Y', 'Y', NULL, '2020-10-06 16:28:35.0', NULL, NULL);
  ```
* 즉시 출금 상태
  ```SQL
  INSERT INTO sys_code_manager
  (group_code, detail_code, expo_name, prnt_order, add_info, use_yn, disp_yn, reg_id, reg_date, mod_id, mod_date)
  VALUES('INS_STATUS', '01', '신청중', 1, NULL, 'Y', 'Y', NULL, '2020-10-06 16:29:14.0', NULL, NULL);
  INSERT INTO sys_code_manager
  (group_code, detail_code, expo_name, prnt_order, add_info, use_yn, disp_yn, reg_id, reg_date, mod_id, mod_date)
  VALUES('INS_STATUS', '02', '입금대기', 2, NULL, 'Y', 'Y', NULL, '2020-10-06 16:29:14.0', NULL, NULL);
  INSERT INTO sys_code_manager
  (group_code, detail_code, expo_name, prnt_order, add_info, use_yn, disp_yn, reg_id, reg_date, mod_id, mod_date)
  VALUES('INS_STATUS', '03', '반려', 3, NULL, 'Y', 'Y', NULL, '2020-10-06 16:29:14.0', NULL, NULL);
  INSERT INTO sys_code_manager
  (group_code, detail_code, expo_name, prnt_order, add_info, use_yn, disp_yn, reg_id, reg_date, mod_id, mod_date)
  VALUES('INS_STATUS', '04', '입금완료', 4, NULL, 'Y', 'Y', NULL, '2020-10-06 16:29:14.0', NULL, NULL);
  ```
* 이미지
  ```SQL
  INSERT INTO sys_code_manager
  (group_code, detail_code, expo_name, prnt_order, add_info, use_yn, disp_yn, reg_id, reg_date, mod_id, mod_date)
  VALUES('USER_IMAGE', 'INSURE', '보험증권', 4, NULL, 'Y', 'Y', NULL, '2019-04-22 10:00:04.0', NULL, NULL);
  ```
