# Car Planner Client Dev
카플래너 App Client 개발 히스토리 및 내용 기록



# MG 시승보험 개발
## Add Tables

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
  PRIMARY KEY (`p_tid`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COMMENT='PG결제 테이블';
```
