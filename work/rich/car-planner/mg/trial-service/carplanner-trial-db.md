# MG 시승보험 개발

# Table
DB 관련 쿼리 정리
## 2020.07.16
전면적인 테이블 설계 및 테이블 변경

```sql
-- member_add_info 사업자 등록 번호 컬럼 추가
ALTER TABLE member_add_info
ADD COLUMN biz_no CHAR(10) NULL DEFAULT NULL COMMENT "사업자 등록 번호" AFTER planner_flag;

-- app_menu_info 어플 메뉴 정보 테이블 생성
CREATE TABLE app_menu_info (
  menu_group varchar(10) NOT NULL COMMENT "메뉴그룹코드",
  menu_code varchar(10) NOT NULL COMMENT "메뉴코드",
  main_name varchar(10) NOT NULL COMMENT "메인 메뉴명",
  sub_name varchar(10) NOT NULL COMMENT "서브 메뉴명",
  level tinyint(1) DEFAULT NULL COMMENT "메뉴레벨",
  icon varchar(20) DEFAULT NULL COMMENT "노출icon",
  uri varchar(100) DEFAULT NULL COMMENT "uri",
  use_yn char(1) DEFAULT "Y" COMMENT "사용여부",
  sort smallint(4) DEFAULT NULL COMMENT "정렬순서",
  reg_id varchar(16) DEFAULT NULL COMMENT "등록자",
  reg_date datetime DEFAULT NULL COMMENT "등록일",
  mod_id varchar(16) DEFAULT NULL COMMENT "수정자",
  mod_date datetime DEFAULT NULL COMMENT "수정일",
  PRIMARY KEY (menu_group,menu_code)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

-- app_menu_info 메뉴 정보 Insert
INSERT INTO app_menu_info (menu_group, menu_code, main_name, sub_name, level, uri, use_yn, sort, reg_id, reg_date) VALUES ("AMM001", "AM001", "다이렉트", "자동차 보험", "1", "/directcar/main", "Y", "1", "charlloss", NOW());
INSERT INTO app_menu_info (menu_group, menu_code, main_name, sub_name, level, uri, use_yn, sort, reg_id, reg_date) VALUES ("AMM002", "AM002", "중고차", "캐피탈", "1", "/capital/main", "Y", "2", "charlloss", NOW());
INSERT INTO app_menu_info (menu_group, menu_code, main_name, sub_name, level, uri, use_yn, sort, reg_id, reg_date) VALUES ("AMM003", "AM003", "중고차", "의무보험", "1", "/trial/main", "Y", "3", "charlloss", NOW());


-- app_menu_grant 어플 메뉴 접근 권한 테이블 생성
CREATE TABLE app_menu_grant (
  uid int(11) NOT NULL COMMENT "회원UUID",
  amm001 char(1) NOT NULL DEFAULT "Y",
  amm002 char(1) NOT NULL DEFAULT "Y",
  amm003 char(1) NOT NULL DEFAULT "N",
  reg_id varchar(16) DEFAULT NULL COMMENT "등록자",
  reg_date datetime DEFAULT NULL COMMENT "등록일",
  mod_id varchar(16) DEFAULT NULL COMMENT "수정자",
  mod_date datetime DEFAULT NULL COMMENT "수정일",
  PRIMARY KEY (uid)
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COMMENT="어플 메뉴 접근 권한";

-- app_menu_grant 권한 정보 Insert
INSERT INTO app_menu_grant (uid, amm001, amm002, amm003, reg_id, reg_date) SELECT uid, "Y", "Y", "Y", user_id, NOW() FROM view_member;



-- carplanner.inicis_pg_payment definition
CREATE TABLE `inicis_pg_payment` (
  `p_seq` int(23) NOT NULL COMMENT '결제 seq',
  `p_srvc` varchar(10) NOT NULL COMMENT '결제 서비스 타겟',
  `p_cid` varchar(40) DEFAULT NULL COMMENT '결제 인증 ID',
  `p_tid` varchar(40) DEFAULT NULL COMMENT '결제 거래 ID',
  `p_mid` varchar(10) NOT NULL COMMENT '결제 상점 ID',
  `p_oid` varchar(40) DEFAULT NULL COMMENT '상품 주문 번호',
  `p_amt` varchar(8) NOT NULL COMMENT '결제 금액',
  `p_status` varchar(10) DEFAULT NULL COMMENT '인증, 결제 결과',
  `p_ini_payment` varchar(10) NOT NULL COMMENT '결제 타입(카드,휴대폰,가상,계좌)',
  `p_noti` varchar(100) DEFAULT NULL COMMENT '결제 정보 필드',
  `p_msg` varchar(30) DEFAULT NULL COMMENT '인증 결과 MSG',
  `p_reg_dt` datetime DEFAULT NULL COMMENT '거래 등록 시간',
  `p_auth_dt` datetime DEFAULT NULL COMMENT '결제 승인 일자',
  `p_cxl_dt` datetime DEFAULT NULL COMMENT '결제 취소 일자',
  `uid` int(11) NOT NULL COMMENT '회원 UUID',
  `status_cd` char(2) NOT NULL COMMENT '결제상태코드(결제시도, 성공, 실패)',
  `p_cxl_admin` varchar(30) DEFAULT NULL COMMENT '결제 취소 admin id',
  PRIMARY KEY (`p_seq`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COMMENT='INICIS PG 결제';

-- carplanner.trial_car_mg_info definition
CREATE TABLE `trial_car_mg_info` (
  `trial_seq` varchar(25) NOT NULL COMMENT '시승보험 시퀀스',
  `telmsgno` int(11) NOT NULL COMMENT 'MG손보 전문번호',
  `uid` int(11) NOT NULL COMMENT '회원UUID',
  `resultcd` char(4) DEFAULT NULL COMMENT '조회 결과 코드',
  `proctype` char(2) NOT NULL COMMENT '시승 보험 상태',
  `vcnohnglnm` varchar(10) DEFAULT NULL COMMENT '차량번호',
  `carbno` char(17) DEFAULT NULL COMMENT '차대번호',
  `vnm` varchar(30) DEFAULT NULL COMMENT '조회 차량명',
  `insprddays` char(1) NOT NULL COMMENT '보험 기간 일수',
  `fstipremsum` varchar(10) DEFAULT NULL COMMENT '조회 보험료',
  `apcdocurl` varchar(255) DEFAULT NULL COMMENT '청약 문서 다운로드 URL',
  `plcydocurl` varchar(255) DEFAULT NULL COMMENT '증권 다운로드 URL',
  `p_seq` int(20) DEFAULT NULL COMMENT '결제 seq',
  `insbgdt` date NOT NULL COMMENT '보험 시작 일자',
  `insendt` date NOT NULL COMMENT '보험 종료 일자',
  `inscldt` datetime DEFAULT NULL COMMENT '보험 취소 시간',
  `reg_date` datetime NOT NULL COMMENT '등록 시간',
  `mod_date` datetime DEFAULT NULL COMMENT '수정 시간',
  PRIMARY KEY (`trial_seq`,`telmsgno`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COMMENT='MG시승보험';

```


# Query

```sql
select *
from trial_car_mg_info tcmi
where proctype = '05'
and inscldt is null

update trial_car_mg_info
set inscldt = mod_date
where proctype = '05'
and inscldt is null

select *
from inicis_pg_payment ipp
where p_oid in ( '2918', '2958')

select *
from trial_car_mg_info tcmi
left join inicis_pg_payment ipp on tcmi.p_seq = ipp.p_seq
where proctype in ('02' , '05', '50', '59')
and ipp.status_cd is null


update trial_car_mg_info t
set t.p_seq = (select p_seq from inicis_pg_payment i where i.p_oid = t.telmsgno and i.status_cd IN ('10','30', '49'))
where t.proctype in ('02', '05', '50', '59')


select *
from trial_car_mg_info tcmi where reg_date is null or insbgdt is null or insendt is null

select *
from inicis_pg_payment ipp where p_auth_dt is null and status_cd in ('10', '30' ,'49')
```
