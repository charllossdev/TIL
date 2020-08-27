
**Dealer Lounge Directcar Agree View**
----
  딜러라운지 다이렉트 카 서비스 약관동의 화면 호출

* **URL**

  - Real: `/dl/directcar/agree`

* **PORT**

  `443 (https)`

* **Method**

  `POST`

* **Data Params**

  **Required:**
  ```py
  {
    P_UID : [string(11)]   // [Required]:카플래너 회원 seqp
  }
  ```

* **Response**

| 성공: 약관동의 화면 return | 실패: 장애화면 출력 (미정 페이지) |
|:--:|:--|
|<img src=./assets/markdown-img-paste-20200827141445313.png width=200> | <img src=./assets/markdown-img-paste-20200827141620236.png width=200> |
