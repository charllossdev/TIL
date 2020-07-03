# Car Planner Admin Dev
카플래너 관리자 개발 히스토리 및 내용 기록



# MG 시승보험 개발
## Table

## SQL Data

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
