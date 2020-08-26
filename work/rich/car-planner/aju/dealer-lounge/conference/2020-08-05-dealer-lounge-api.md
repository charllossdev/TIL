# 회의 내용 정리

# API 관련

1. 파라메터 관련 정의

    * 기존 API 정의 변경
    * 이슈: 딜러라운지 - 카플래너 회원 간의 데이터 종속성을 위해 양측 시퀀스를 저장하여 관리하기 위한 추가 요청
      * 요청: 딜러라운지 회원 정보 및 회원 Seq
    ```perl
    {
      P_DEALER_SEQ    : [string(??)]    // [Required]: 아주 딜러라운지 회원 seq
      P_UID           : [integer(11)],  // [Null or Required]: 카플래너 회원 seq
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
      * 응답: 카플래너 회원 Seq(신규 발급 or 저장된 카플래너 회원 seq)
    ```perl
    {
      P_UID           : [integer(11)],  // [Required]: 카플래너 회원 seq
    }
    ```

2. 아주캐피털 측에 카플래너 API 서버 IP/PORT 전달 (2020.08.06 예정)

상기 이미지와 같이 개발 - 카플래너 앱에 항목을 추가했습니다. (금일 오후 or 내일 오전)에 확인 가능합니다.


# Native Bridge

1. 금일 중으로 브릿지 인터페이스 문서 전달
