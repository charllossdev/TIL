
**Dealer Lounge Directcar Request**
----
  Returns Carplanner Directcar Main Page.

* **URL**

  - Real: `/dl/directcar/main`

* **PORT**

  `443 (https)`

* **Method**

  `POST`

* **Data Params**

  **Required:**
  ```perl
  {
    P_UID : [string(11)],   // [Required]: 카플래너 회원 seq
  }
  ```

* **Response**

  **Success**


  | 성공: 다이렉트카 신청 및 조회 화면 | 실패: 장애화면 출력 (미정 페이지) |
  |:--:|:--|
  |<img src=./assets/markdown-img-paste-20200827141743866.png width=200> | <img src=./assets/markdown-img-paste-20200827141620236.png width=200> |
