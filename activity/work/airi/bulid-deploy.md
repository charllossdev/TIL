# Build & Deploy

1. Version Check
   * 새로운 버전을 배포한다면, pom.xml에서 버전 정보 수정(2가지)
     + Root Parent pom.xml
     + Rest Api pom.xml
2. 배포 Branch 생성
   * ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b114206a-362c-43d5-bcb6-3e308d527717/BranchStrategy.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b114206a-362c-43d5-bcb6-3e308d527717/BranchStrategy.png)
   * `Master` 브랜치 기준으로 브랜치 생성 
   * `Realeas_version` 형식으로 배포 브런치 생성 및 푸쉬
   * 
3. Jenkins 빌드 배포
   * 빌드 후 -> 배포 이미지 생성(Harbor) -> 배포
   * 배포 버전 확인 및 Rest 선택 (배포 이미지 확인)
   * 191
   * 61 `Dev` 서버 빌드 및 배포 
   * `stage` 배포는 배포 이미지 생성 -> 배포(보안실 서버)
4. 도커 확인
   * 도커로 배포된 서버 버전 확인 및 서버 구동 확인
   * 도커로 로그 확인 명령어
  




---

생각
* Jenkins 계정
* 




