
# 16Week 숙제 정리

1. default-nav.jsp & default-left.jsp
    * 레프트 클릭 시 nav 추가 및 하이라이트 처리
    * 탭 클릭 시 nav 역시 하이라이트 처리
    * 탭 클릭 시 레프트 1뎁스 및 2뎁스 하이트처리 로직 변경
    * 탭 삭제 시 nav 삭제
    * 코드 리펙토링

2. Javascript 배열 및 Prototype
    * 배열의 인덱스를 매개변수로 받아 삭제하는 함수 removeIndex 생성
    * 배열의 중복된 값을 모두 삭제하는 함수 remove 생성
    *  중복된 배열 관련 처리에 도움이 되는 Array 메서드 정리
        *  set:  unique 값만 저장할 수 있도록 하기 때문에 array에 넣게 되면,  중복값 제거.
        *  filter:  array 내의 각 element 에 조건을 주어, true 값을 return 한 element 만 모아서 새로운 array 생성
        *  reduce: array 의 각 요소를 줄여주는데 사용, 그리고 그것들을 모아 최종 array 로 결합
3. Jquery Remove()
    * default-left.jsp 코드 200 라인에 정리
    ```javascript
		$tabLi.remove(); // Li 테그 제거

		// remove() : $(dom)과 그 하위 요소를 전부 제거한다. 즉 요소 및 하위 요소들의 데이터, 이벤트는 전부 제거된다.
		// 그러나, 제거된 요소가 jQuery 데이터 형태로는 유지된다. jquery 로 접근하여 원하는 요소및 속성을 얻을 수 있다.
		console.log($tabLi);  // 출력
		console.log($tabLi.children()); // 출력
    ```


substr
substring 차이


// 배열관련 함수 // array 라는 클래스는 object
// slice(index1, index2), splice(index, count)
// 원본이 삭제되야하는 케이스와 보존되어야 하는 케이스


오브젝트는 2가지 타입
1. 호츨을 못하는 타입
2. 호출을 하는 타입


자바스크립트의 원시 타입 6개 중에 function이라는 타입은 없다.
function이라는 타입은 오브젝트의 하위 타입이고, 호출을 할 수 있는 타입이다.



# 메서드 체이닝

메서드 체이닝 이유는 모든 메서드가 자기자신(this)를 리턴하기 떄문이다.



팀숙제

자바스크립트 해석기



자바스크립트는 함수 스코프 단위로 실행

함수 스코프 단위로 실행한다는건, 함수 스코프 범위로 함수 유효범위 체인이 생기는 것이고

자바스크립트 해석기는 먼저 일ㄲ는 것
