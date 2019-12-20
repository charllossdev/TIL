
# Stop watch

## 구현부

```javascript
startTimer = function(_time) {
  let _oriTime = _time;
  return function _timerFunc(_nextTime) {
    if (_oriTime === _time || _nextTime === -1) {
      _time = _time - 1 < 0 ? 0 : _time - 1;
      if (_time >= 1) {
        setTimeout(function() {
          _timerFunc(-1);
        }, 1);
        return _time + 1;
      }
      else {
        return 0;
      };
    }
    else {
      return _time;
    };
  };
};
```

위 함수는 어떻게 작성되었는지 하나하나 구분하여 알아보겠습니다. 일단 구현 프로세스를 나열하면 아래와 같습니다.

- 클로저(Closure)로 Private 함수를 생성
- 설정된 시간을 _oriTime이라는 변수에 따로 저장함
- 시간을 100ms 계속 감소시킴(재귀함수를 호출, 자기 함수를 호출, self-invoking function)
- 이때 남은 시간이 100ms 이하가 될 때 까지 계속



## 실행부

```javascript

var timer = startTimer(SET_TIME_MS); // MS 단위 시간 설정

timer(); // 타이머 시작
```

> 위 예제는 10초를 설정하였습니다. 이제 timer()를 실행하면 계속해서 남아있는 시간이 반환됩니다.
