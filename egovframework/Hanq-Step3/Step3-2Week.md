# 2week

## DB 구조

1 : N 관계 (t_dp_bnnr_mng 테이블 : 전시 디테일 테이블)
디테일 테이블

## 배너등록

이슈 : 뒤로가기 버튼을 고려해야하는 상황인가(뒤로가기를 고려해서 Get방식)

* 날자입력 : 날자입력은 달력을 넣는 방법이 바람직하다.(DataPicker 도입 추진)
    * date.picker
    ```javascript
    <td scope="row" colspan="3">
               <div class="cal-wrap">
                   <input type="text" name="dpStrtDt" class="ui-ipt" data-date="start" readonly>
                       <button type="button" class="btn-cal"><span class="ico-cal-01"></span></button>
                   </div>
                   <div class="cal-wrap">
                   <input type="text" name="dpEndDt" class="ui-ipt" data-date="end" readonly>
                   <button type="button" class="btn-cal"><span class="ico-cal-01"></span></button>
               </div>
       </td>
       ```
    *



렉시컬스코프  기준으로 this

렉시컬스코프를 동적스코프로(호출되는 기준으로 생각하는 기준)으로 변경하고 싶을때, this의 컨텍스트를 동적으로 변경할 수 있기 때문에 사용한다.


```javascript
var a = [1,2,3,4]
Math.max(a) // NaN
```


> NaM : Not a Number



## F
 Math.max.apply(null, idsArr); // apply 사용: 배열을 이용해 결과를 얻고 싶을 때, 사용

 apply에 대해 정리하기


 # 숙제
코드 해석 및 날자 제한 관련 더 훌륭한 로직 내기
