
**Dealer Lounge Directcar Api Request**
----

* **URL**

  - Real: `/dl/directcar/`

* **Protocol**

  `TCP`

* **PORT**

  `443 (https)`

* **Method**

  `POST`

* **Accept Charset**

  `UTF-8`

* **Data Params**

  **Required:**
  ```perl
  {
    P_DEALER_SEQ    : [string(??)]    // [Required]: 아주 딜러라운지 회원 seq
    P_UID           : [string(11)],   // [With or without]카플래너 회원 seq
    P_NAME          : [string(10)],   // [Required]: 이름
    P_MOBILE        : [string(11)],   // [Required]: 휴대폰번호  
    P_DEALER_AREA   : [string(10)],   // [Required]: 지역(광역시/도)
    P_DEALER_REGION : [string(10)],   // [Required]: 지역 (구/군)
    P_DEALER_CODE   : [string(16)],   // [Required]: 종사원증 번호
    P_CO_AREA       : [string(20)],   // [Required]: 매매단지명
    P_CO_COMPANY    : [string(20)],   // [Required]: 매매상사명
    P_BIZ_NO        : [string(10)],   // [Required]: 매매상사 사업자코드
  }
  ```

* **Response**

  P_STATUS

  * $01$ : 신규 가입 회원
  * $02$ : 기존 카플래너 가입한 회원이거나, 신규가입을 시도했지만 약관동의를 하지 않은 회원
    + next step: $/dl/directcar/agree$
  * $03$ : 이미 가입한 회원
    + next step: $/dl/directcar/main$

  >*  P_STATUS 상태가 $01$, $02$ 인 회원은 약관동의를 먼저 선행되어야 회원가입이 완료된다.<br>
  >*  P_STATUS 상태가 $03$ 인 회원은 바로 다이렉트카 서비스를 이용 가능하다.

  **Success**

  ```perl
  {
    "result": {
      "P_UID"     : 329,      // 카플래너 회원 seq
      "P_STATUS"  : "02",     // 카플래너 회원 상태
      "P_SUCCESS" : true,     // 성공 여부 (true/false)
      "P_MSG"     : "정상"    // 결과 메세지
    }
  }
  ```


  **Fail**

  ```perl
  {
    "result": {
      "P_SUCCESS": false      // 성공 여부 (true/false)
      "P_MSG": "P_DEALER_REGION, P_CO_COMPANY, P_DEALER_SEQ 파라메터가가 누락됬습니다.",
    }
  }
  ```
