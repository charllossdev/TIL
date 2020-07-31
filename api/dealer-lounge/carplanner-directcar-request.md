
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

* **Method:**

  `POST`

* **Accept Charset**

  `UTF-8`

*  **URL Params**

    None

* **Data Params**

  **Required:**

  `memberSeq=[string] or [integer]` (Undefined)

* **Sample Call:**

  ```html
  <form  name="directCar" id="directCar" method="post" action="https://TARGET_HOST/dl/directcar/">
    <input type='hidden' 	name='memberSeq'/>
  </form>

  $("#directCar").submit();
  ```
