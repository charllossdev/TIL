
---

**Set User Info**
----
  Result Carplanner join memeber info and Update P_UID parameter Set

* **URL**

  Undefined

* **Method:**

  `POST`

* **Accept Charset**

  `UTF-8`

* **Data Params**(json)

  **Required:**

  * `memberSeq=[string] or [integer]` (Undefined),
  * `P_UID=[integer]` // Update Value

* **Success Response:**

  * **Code:** 200 <br />
    **Content:**
    ```py
    {
      P_STATUS  = "00",      // 00: Success, 01: Fail
      P_MSG     = "Success"  // MSG
    }`
    ```

* **Error Response:**

  * **Code:** 404 NOT FOUND <br />
    **Content:**
    ```py
    {
      P_STATUS  = "01",   // 00: Success, 01: Fail
      P_MSG     = "Fail"  // MSG
    }`
    ```

* **Sample Call:**

  ```javascript
    $.ajax({
      url     : "/Undefined",
      type    : "POST",
      dataType: "json",
      data    : {
                  'memberSeq' : memberSeq,
                  'P_UID'     : pUid}
      success : function(r) {
        console.log(r);
      }
    });
  ```
