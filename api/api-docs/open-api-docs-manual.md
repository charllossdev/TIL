# 오픈 API 및 문서화 방안


## 오픈 API 문서화의 중요성
http://opensourcesurvey.org/2017/

## API 문서 내용

내용 구성

* 무엇을 할 수 있는지
* 설치 환경, 실행 환경 등 전제 조건은 무엇인지
* 각 기능 별 사용하는 방법 및 실행 결과

정확성

* 문서 대로 했을 경우 그 대로 수행이 되어야함
* 사용자의 환경을 고려하여 작성 필요
* 가능한 내용 / 불가능한 내용이 명확해야 함

최신성

* 문서 작성 일자 및 버전 관리 중요

가독성

* 웹상으로 읽기 편리해야 하며
* 목차, 내용 탐색이 용이해야 함

예: https://github.com/naver/devcenter-open-project-migration


## 문서화 수단이슈
정확성 보장

* 개발 따로 문서 따로 가게되면 문서가 부정확해지는 문제가 있음
* 문서 작성 후 테스트 매우 중요 (문서 대로 했을 경우 그 대로 수행이 되어야함)

문서 작성 수단

* 개발하면서 문서를 지속 업데이트하는 것이 바람직
* 다양한 문서화 솔루션이 있지만, 소스코드와 밀접한 툴이 추천
* 가독성, 표현력이 적합한 수단 Markdown 확장

문서 배포

* 웹으로 배포가 되고, 가독성이 뛰어 나야 함
* 배포는 수시로, 자동화 되어야 함

예시: https://github.com/naver/naver-openapi-guide

## API 문서화

API스펙 (설계, 정확성)

* Html:다양한 표현이 가능하지만, html/css 코드를 수정해야 함
* Markdown:간단한 텍스트로 구조적인 표현이 가능, html 보다는 표현력이 낮으나, 이미지, 도표
표시가 가능
* Swagger:yaml 또는 json으로 API를 설계 단계 부터 스펙을 정의 해야 함, 실제 코드와 연계되어
스펙 작동
SDK문서 (자동화)
* SDK의 각 코드 내에 넣은 주석으로 부터 문서를 자동으로 뽑아 내지 않으면 작성 및 관리가 매우
어려움
* 플랫폼별로 적당한 툴 적용
  - JS: JS docs
  - Java:Javadocs
  - iOS:Jazzy

튜토리얼 (구조화)

* 단계별로 쉽게 설명할 수 있도록 문서를 쉽게 구조화 할 수 있어야 함
* 3 detph 정도까지 트리 구조로 구성해 문서 탐색이 용이해야 함

## API 문서 배포
Github readme

* Github 소스 코드 저장소의 markdown파일
* 작성은 쉬우나, 가독성이 떨어짐

Github page

* Github 저장소가 있으면, github page생성이 가능
* 저장소의 특정 폴더에 배포된 내용을 html로 자동 변환하여 배포 가능
  - http://naver.github.io/naverspeech-sdk-android/ (JS: JS docs)
  - https://navermaps.github.io/maps.js/docs/ (Java:Javadocs)
  - http://naver.github.io/naverspeech-sdk-ios/ (iOS:Jazzy)

Gitbook

* Github page의 장점과 readme 장점을 결합하여, 가이드 북형태로 배포할 수 있음
* Github page를 활용할 수도 있으며, 독립된 페이지로도 배포할 수 있음
  - https://github.com/naver/naver-openapi-guide
  - https://developers.naver.com/docs/common/openapiguide/
  - https://okgosu.gitbooks.io/naveropenapi/content/apilist.html
