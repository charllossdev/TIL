# MG 손해보험 보험 장애 분석

## 일시 : 2020년 07월 30일  18시 14분 36초

## 분석
* MG손해보험 시승보험 API 서버 Timeout Setting : 60초
* MG손해보험 시승보험 API 서버로 보험 승인 요청시간 : 2020년07월30일  18시 14분 36초
* MG손해보험 시승보험 API 서버로 보험 승인 요청타임 아웃 : 2020년07월30일  18시 15분 36초

## 결론
* MG손해보험으로 시승보험 신청 요청을 보냈지만, 1분 동안 요청에 대한 응답이 오지 않는 장애 발생
    * 자세한 사항은 로그 확인

# 로그

```perl
// MG 요청 시작 2020.07.30 18:14:36.033
18:14:36.033 [Executor-7] INFO  jdbc.connection.connectionOpened - 4549. Connection opened  org.springframework.jdbc.datasource.DataSourceTransactionManager.doBegin(DataSourceTransactionManager.java:262)
18:14:36.033 [Executor-7] DEBUG jdbc.connection.connectionOpened - open connections:  4549 (1)
18:14:36.034 [Executor-7] INFO  c.r.groom.base.aop.LoggingAspect.beforeService - noLoggingMethod :null
18:14:36.034 [Executor-7] INFO  c.r.groom.base.aop.LoggingAspect.beforeService - noLoggingClass :null
18:14:36.034 [Executor-7] INFO  c.r.groom.base.aop.LoggingAspect.beforeService - controllerName.getClass() :class com.richncar.groom.web.trial.service.TrialServiceImpl
18:14:36.034 [Executor-7] WARN  c.r.groom.base.aop.LoggingAspect.beforeService - ======== Service S: Service Logging ========
18:14:36.034 [Executor-7] WARN  c.r.groom.base.aop.LoggingAspect.beforeService - service    : TrialServiceImpl
18:14:36.035 [Executor-7] WARN  c.r.groom.base.aop.LoggingAspect.beforeService - method     : apiMgTrialCarCall
18:14:36.035 [Executor-7] WARN  c.r.groom.base.aop.LoggingAspect.beforeService - parameter  : [{"param":"{\"P_STATUS\":\"00\",\"P_TID\":\"INIMX_AUTHrichncoin020200730181408815692\",\"P_REQ_URL\":\"https:\/\/ksmobile.inicis.com\/smart\/payReq.ini\",\"P_NOTI\":\"137\",\"P_MNAME\":\"\",\"procType\":\"02\",\"memberUid\":548,\"memberSms\":\"01064788997\",\"telmsgNo\":43974}"}]
18:14:36.035 [Executor-7] WARN  c.r.groom.base.aop.LoggingAspect.beforeService - ======== Service E: Service Logging ========
18:14:36.035 [Executor-7] DEBUG c.r.g.g.d.G.selectByPrimaryKey.debug - ==>  Preparing: select uid, marketing_flag, dealer_area_code, dealer_region_code, co_area, co_company, last_login_date, passwd_chage_date, drop_date, auth_mobile_flag, bank_code, drop_reason, passwd_init_flag, dealer_code, user_tend, tend_memo, greeting, pr_url, inflow_route_code, inflow_route_text, inflow_route_chnl, ref_uid, planner_flag, biz_no, reg_date, mod_date, mod_admin_date, mod_admin_id from member_add_info where uid = ?
18:14:36.035 [Executor-7] DEBUG c.r.g.g.d.G.selectByPrimaryKey.debug - ==> Parameters: 548(Integer)
18:14:36.035 [Executor-7] INFO  jdbc.sqlonly.sqlOccured - SQL:::select

// MG 요청 세션 장애 2020.07.30 18:15:36.316
18:15:36.316 [Executor-7] DEBUG c.richncar.groom.api.external.mg.Mg.apiMgTrialCarCallRequest - @@@@ MG API FAIL @@@@ : org.springframework.web.client.ResourceAccessException: I/O error on POST request for "https://hmp.mggeneralins.com:443/CONTBIZCARDR.form": Read timed out; nested exception is java.net.SocketTimeoutException: Read timed out
18:15:36.316 [Executor-7] DEBUG c.r.g.w.t.d.T.updateTelmsgno.debug - ==>  Preparing: UPDATE trial_car_mg_info SET proctype = ?, mod_date = ? WHERE telmsgno = ?
18:15:36.316 [Executor-7] DEBUG c.r.g.w.t.d.T.updateTelmsgno.debug - ==> Parameters: 20(String), 2020-07-30 18:15:36.316(Timestamp), 43974(Integer)
18:15:36.317 [Executor-7] INFO  jdbc.sqlonly.sqlOccured - SQL:::UPDATE trial_car_mg_info
	     SET proctype = '20',
```
