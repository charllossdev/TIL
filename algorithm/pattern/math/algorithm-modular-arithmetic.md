# Modular Arithmetic

* 컴퓨터의 정수는 저장할 수 있는 범위가 저장되어 있기 때문에, 답을 M으로 나눈 나머지를 출력하는 문제가 등장
  * `(A + B)mod M` = `((A mod M) + (B mod M)) mod M`
  * `(A * B)mod M` = `((A mod M) * (B mod M)) mod M`
  * `(A - B)mod M` = `((A mod M) - (B mod M) + M) mod M`
  * 뺄셈의 경우 먼저 mod  연산을 한 결과가 음수가 나올 수 있기 때문에 위아 같이 해야한다.
* 나누기의 경우 성립하지 않는다.
