
---

**Get User Info**
----
  Returns json data about a single user info.

* **URL**

  Undefined

* **Method:**

  `POST`

* **Accept Charset**

  `UTF-8`

* **Data Params**(json)

  **Required:**

  `memberSeq=[string] or [integer]` (Undefined)

* **Success Response:**

  * **Code:** 200 <br />
      - **Content:**
      ```perl
      {
        P_STATUS        : "00",           // 00: Success, 01: Fail
        P_UID           : [integer(11)],  // Null or Required (카플래너 회원 seq)
        P_MOBILE        : [string(11)],   // Required
        P_NAME          : [string(10)],   // Required
        P_DEALER_AREA   : [string(10)],   // Required
        P_DEALER_REGION : [string(10)],   // Required
        P_CO_AREA       : [string(20)],   // Required
        P_CO_COMPANY    : [string(20)],   // Required
        P_BIZ_NO        : [string(10)],   // Required
        P_MSG           : "Success"
      }
      ```

* **Error Response:**

  * **Code:** 404 NOT FOUND <br />
      - **Content:**
      ```perl
      {
        P_STATUS  : "01",                 // 00: Success, 01: Fail
        P_MSG     : "User doesn't exist"  // MSG
      }
      ```

* **Sample Call:**

  ```javascript
    $.ajax({
      url     : "/Undefined",
      type    : "POST",
      dataType: "json",
      data    : {'memberSeq': memberSeq}
      success : function(r) {
        console.log(r);
      }
    });
  ```
