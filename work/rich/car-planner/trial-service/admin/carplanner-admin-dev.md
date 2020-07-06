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
