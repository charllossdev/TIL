# MG 시승보험 개발


# Table

* MG_TRIAL_CAR_INFO
```sql
-- carplanner.mg_trial_car_info definition

CREATE TABLE `mg_trial_car_info` (
  `telmsgno` varchar(40) NOT NULL COMMENT 'MG전문번호',
  `uid` int(11) NOT NULL COMMENT '회원UUID',
  `proctype` char(2) NOT NULL COMMENT '실행구분',
  `vcnohnglnm` varchar(10) DEFAULT NULL COMMENT '차량번호',
  `carbno` char(17) DEFAULT NULL COMMENT '차대번호',
  `vnm` varchar(100) DEFAULT NULL COMMENT '조회차량명',
  `insbgdt` date DEFAULT NULL COMMENT '보험시작일자',
  `insprddays` char(1) DEFAULT NULL COMMENT '보험기간일수',
  `fstipremsum` varchar(20) DEFAULT NULL COMMENT '조회보험료',
  `apcdocurl` varchar(500) DEFAULT NULL COMMENT '청약문서 다운로드 URL',
  `plcydocurl` varchar(500) DEFAULT NULL COMMENT '증권 다운로드 URL',
  `p_tid` varchar(100) DEFAULT NULL COMMENT 'PG결제 전문번호',
  `reg_date` datetime DEFAULT NULL COMMENT '등록시간',
  `mod_date` datetime DEFAULT NULL COMMENT '수정시간',
  `insendt` date DEFAULT NULL COMMENT '보험종료일자',
  PRIMARY KEY (`telmsgno`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COMMENT='MG손해보험 시승보험내역';
```

* PG_PAYMENT_ORDER
```SQL
-- carplanner.pg_payment_order definition

-- carplanner.pg_payment_order definition

CREATE TABLE `pg_payment_order` (
  `p_tid` varchar(40) NOT NULL COMMENT '결제 거래 번호',
  `p_type` varchar(10) NOT NULL COMMENT '결제 타입',
  `p_oid` varchar(40) DEFAULT NULL COMMENT '상점 주문 번호',
  `p_amt` varchar(8) NOT NULL COMMENT '결제 금액',
  `p_status` varchar(10) NOT NULL COMMENT '결제 거래 상태',
  `p_auth_dt` datetime NOT NULL COMMENT '결제 승인 일자',
  `p_cxl_dt` datetime DEFAULT NULL COMMENT '결제 취소 일자',
  `p_noti` varchar(100) DEFAULT NULL COMMENT '정보필드',
  `uid` int(11) NOT NULL COMMENT '회원UUID',
  `telmsgno` varchar(40) NOT NULL COMMENT 'MG전문번호',
  PRIMARY KEY (`p_tid`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COMMENT='PG결제 테이블';
```

# SQL Data

* Menu Info
```sql
INSERT INTO carplanner.sys_menu_info
(menu_group, menu_code, menu_name, `level`, icon, uri, use_yn, sort, reg_id, reg_date, mod_id, mod_date)
VALUES('TRI001', 'TRI001', '시승보험', 1, 'fa-car', '', 'Y', 1060, 'charlloss', '2020-07-02 14:31:30.0', NULL, NULL);
INSERT INTO carplanner.sys_menu_info
(menu_group, menu_code, menu_name, `level`, icon, uri, use_yn, sort, reg_id, reg_date, mod_id, mod_date)
VALUES('TRI001', 'TRIL001', 'MG손보 시승보험', 2, '', '/trial/main', 'Y', 1061, 'charlloss', '2020-07-02 14:32:32.0', NULL, NULL);

```

* Menu Mapper
```sql
INSERT INTO carplanner.sys_menu_mapper
(auth_seq, menu_group, menu_code, reg_id, reg_date, mod_id, mod_date)
VALUES(1, 'TRI001', 'TRI001', 'charlloss', '2020-07-02 14:37:36.0', NULL, NULL);
INSERT INTO carplanner.sys_menu_mapper
(auth_seq, menu_group, menu_code, reg_id, reg_date, mod_id, mod_date)
VALUES(1, 'TRI001', 'TRIL001', 'charlloss', '2020-07-02 14:37:35.0', NULL, NULL);
```

* System Common Code
```sql
INSERT INTO carplanner.sys_code_manager
(group_code, detail_code, expo_name, prnt_order, add_info, use_yn, disp_yn, reg_id, reg_date, mod_id, mod_date)
VALUES('MG_TYPE', '00', '가입 심사중', 1, 'MG시승보험 상태', 'Y', 'Y', 'charllossDev', '2020-06-25 14:29:14.0', NULL, NULL);
INSERT INTO carplanner.sys_code_manager
(group_code, detail_code, expo_name, prnt_order, add_info, use_yn, disp_yn, reg_id, reg_date, mod_id, mod_date)
VALUES('MG_TYPE', '01', '보험 조회', 2, 'MG시승보험 상태', 'Y', 'Y', 'charllossDev', '2020-06-25 14:29:14.0', NULL, NULL);
INSERT INTO carplanner.sys_code_manager
(group_code, detail_code, expo_name, prnt_order, add_info, use_yn, disp_yn, reg_id, reg_date, mod_id, mod_date)
VALUES('MG_TYPE', '02', '보험 가입', 3, 'MG시승보험 상태', 'Y', 'Y', 'charllossDev', '2020-06-25 14:29:14.0', NULL, NULL);
INSERT INTO carplanner.sys_code_manager
(group_code, detail_code, expo_name, prnt_order, add_info, use_yn, disp_yn, reg_id, reg_date, mod_id, mod_date)
VALUES('MG_TYPE', '05', '보험 취소', 4, 'MG시승보험 상태', 'Y', 'Y', 'charllossDev', '2020-06-25 14:29:14.0', NULL, NULL);
INSERT INTO carplanner.sys_code_manager
(group_code, detail_code, expo_name, prnt_order, add_info, use_yn, disp_yn, reg_id, reg_date, mod_id, mod_date)
VALUES('MG_TYPE', '10', 'MG 손보 미응답', 5, 'MG시승보험 상태', 'Y', 'Y', 'charllossDev', '2020-06-25 14:29:14.0', NULL, NULL);
INSERT INTO carplanner.sys_code_manager
(group_code, detail_code, expo_name, prnt_order, add_info, use_yn, disp_yn, reg_id, reg_date, mod_id, mod_date)
VALUES('MG_TYPE', '11', '보험 가입 실패', 6, 'MG시승보험 상태', 'Y', 'Y', 'charllossDev', '2020-06-25 14:29:14.0', NULL, NULL);
INSERT INTO carplanner.sys_code_manager
(group_code, detail_code, expo_name, prnt_order, add_info, use_yn, disp_yn, reg_id, reg_date, mod_id, mod_date)
VALUES('MG_TYPE', '19', '조회불가', 7, 'MG시승보험 상태', 'Y', 'Y', 'charllossDev', '2020-06-25 14:29:14.0', NULL, NULL);
INSERT INTO carplanner.sys_code_manager
(group_code, detail_code, expo_name, prnt_order, add_info, use_yn, disp_yn, reg_id, reg_date, mod_id, mod_date)
VALUES('MG_TYPE', '20', '결제취소', 8, 'MG시승보험 상태', 'Y', 'Y', 'charllossDev', '2020-06-25 14:29:14.0', NULL, NULL);
```
