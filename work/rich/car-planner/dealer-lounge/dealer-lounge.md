# 딜러라운지 작업

# SQL

다이렉트 유입 경로 컬럼 추가

```sql
ALTER TABLE customer_db_master ADD COLUMN route_type char(2) COMMENT '다이렉트 유입 경로' AFTER ip_address;
```
