
---

**Dealer Lounge Directcar Request**
----
  Returns Carplanner Directcar Main Page.

* **URL**(Undefined)

  - Real: `https://app.richcarplanner.com/dl/directcar/`
  - Dev: `https://app-dev.richcarplanner.com/dl/directcar/`

* **Protocol**

  `TCP`

* **PORT**

  `443 (https)`

* **Method**

  `POST`

* **Accept Charset**

  `UTF-8`

*  **URL Params**

    None

* **Data Params**

  **Required:**
  ```perl
  {
    P_UID           : [integer(11)],  // [Null or Required]: 카플래너 회원 seq
    P_MOBILE        : [string(11)],   // [Required]: 딜러 휴대전화
    P_NAME          : [string(10)],   // [Required]: 딜러 회원명
    P_DEALER_AREA   : [string(10)],   // [Required]: 딜러 지역 코드
    P_DEALER_REGION : [string(10)],   // [Required]: 딜러 시/도/군/구 코드
    P_BIZ_NO        : [string(10)],   // [Required]: 딜러 사업자 번호
    P_CO_COMPANY    : [string(20)],   // [Required]: 딜러 회사명
    P_CO_AREA       : [string(20)],   // [Required]: 딜러 회사 지역
    //P_STATUS        : "00",         // 00: Success, 01: Fail
  }
  ```

* **Response**

  **Required**

  `P_UID : VALUE`

* **Sample Call:**

  ```html
  <form  name="directCar" id="directCar" method="post" action="https://TARGET_HOST/dl/directcar/">
    <input type='hidden' 	name='memberSeq'/>
  </form>

  $("#directCar").submit();
  ```
