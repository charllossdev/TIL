# Work

# 2020-08-25
```sql
CREATE TABLE carplanner.member_ptn_join_hist (
  hist_seq INT(11) NOT NULL,
  uid INT(11) NOT NULL,
  partner_code CHAR(2) NOT NULL,
  os_ver VARCHAR(20) NULL,
  reg_date DATETIME NULL,
  PRIMARY KEY (hist_seq))
ENGINE = InnoDB
DEFAULT CHARACTER SET = utf8
COLLATE = utf8_bin
COMMENT = '회원 제휴 가입 이력';

ALTER TABLE carplanner.member_add_info
ADD COLUMN partner_group2 VARCHAR(20) NULL DEFAULT 'CA' COMMENT '제휴사 코드 그룹'  AFTER partner_flag
```

딜러라운지 유입 테이블 생성

```sql
-- carplanner.dealer_lounge_inout_hist definition

CREATE TABLE `dealer_lounge_inout_hist` (
  `hist_seq` int(11) NOT NULL AUTO_INCREMENT COMMENT '유입 seq',
  `uid` int(11) DEFAULT NULL COMMENT '카플레너 회원 uid',
  `name` varchar(20) DEFAULT NULL COMMENT '회원명',
  `mobile` varchar(11) DEFAULT NULL COMMENT '휴대폰번호',
  `dealer_area` varchar(10) DEFAULT NULL COMMENT '딜러지역(광역시/도)',
  `dealer_region` varchar(10) DEFAULT NULL COMMENT '딜러지역(구/군)',
  `dealer_code` varchar(16) DEFAULT NULL COMMENT '종사원증 번호',
  `dealer_seq` varchar(20) DEFAULT NULL COMMENT '딜러라운지 회원 seq',
  `co_area` varchar(20) DEFAULT NULL COMMENT '매매단지명',
  `co_company` varchar(20) DEFAULT NULL COMMENT '매매상사명',
  `biz_no` varchar(10) DEFAULT NULL COMMENT '매매상사 사업자번호',
  `msg` varchar(50) NOT NULL COMMENT '결과 메세지',
  `success` char(1) NOT NULL COMMENT '통신 성공 여부(Y/N)',
  `reg_date` datetime NOT NULL COMMENT '등록일자',
  PRIMARY KEY (`hist_seq`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COMMENT='딜러라운지 다이렉트카 접근 기록';
```



# 2020-06-18
**COMMIT**
'#'7311 MG API 연동

# 2020-06-10
**COMMIT**
PG_PAYMENT_ORDER PG결제 테이블 Mybatis generator 생성

# 2020-06-08
**COMMIT**

PG결제 최종 완료 화면 UI 테스트

# 2020-06-04
**COMMIT**
`#`7311 PG결제 네이티브 새창 테스트

# 2020-06-03
**COMMIT**
`#`7311 네이티브 헤더 URL 콜백 테스트


# 2020-06-01
**COMMIT**
카플래너 결제 승인, 취소, Native Header 테스트


# 2020-05-27
**COMMIT**
카플래너 시승 보험 기능 추가

* MG 손해보험 API(미연동)
* PG 결제 연동(이니시스)


# 2020-05-21
PG결제 모듈 연동
* KEY : CmiX6SJFxQzLrBT4
* IV  : 6eKjCNuaYyi861==

PG결제 테스트 모듈
* KEY : ItEQKi3rY7uvDS8l
* IV  : HYb3yQ4f65QL89==



# 2020-05-15
**COMMIT**
카플래너 웹 회원가입 서비스 개발
* 웹 회원가입 타일즈 추가
* 웹 회원가입 프론트 추가
---
