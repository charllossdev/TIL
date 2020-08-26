
---

**Dealer Lounge Directcar Request**
----
  Returns Carplanner Directcar Main Page.

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

  **Required**

  ```perl
  {
    P_UID           : [string(11)],  // [Required]: 카플래너 회원 seq
  }
  ```
