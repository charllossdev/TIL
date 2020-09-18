# 2020.09.16
다이렉트 관련 컬럼 추가

```SQL
alter table customer_db_master add status_code char(2) DEFAULT '02' NOT null after site_group_code
```
