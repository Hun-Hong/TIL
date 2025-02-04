# Python 숫자형(Numeric Type)과 부동소수점 연산

## 1. Python 숫자형 타입
Python에서 제공하는 주요 숫자형 데이터 타입:

| 타입 | 설명 | 예시 |
|------|------|------|
| **int** | 정수형 | `10`, `-5`, `1000` |
| **float** | 실수형 | `3.14`, `-2.5`, `1.0` |
| **complex** | 복소수형 | `2+3j`, `-1j` |

---

## 2. 정수형 (int)
Python의 `int` 타입은 크기 제한 없이 자동으로 메모리를 확장.
```python
num = 123456789012345678901234567890
print(num)  # 정상 출력
```
## 3. 실수형 (float)
소수점이 포함된 숫자를 표현.
```python
pi = 3.14159
print(pi)
```
## 4. 복소수형 (complex)
j를 사용하여 허수를 표현.
```python
z = 2 + 3j
print(z.real)  # 실수부 출력
print(z.imag)  # 허수부 출력
```
## 5. 소수점 표현 방식 (Floating Point Representation)
컴퓨터는 실수를 2진수(부동소수점) 형식으로 저장하기 때문에 일부 숫자는 정확히 표현되지 않음.

### 10진수와 2진수 변환
10진수 0.1을 2진수로 변환하면 0.00011001100110011... (무한반복).
따라서, 일부 소수는 2진수로 정확히 저장되지 않음.

```python
print(0.1 + 0.2)  # 예상: 0.3, 실제: 0.30000000000000004
```
부동소수점 오류 해결: decimal 모듈 활용
decimal을 사용하면 보다 정확한 실수 연산 가능.
```python
from decimal import Decimal

a = Decimal('0.1')
b = Decimal('0.2')
print(a + b)  # 정확하게 0.3 출력
```
## 6. 부동소수점 오류 (Floating Point Error)
```python
print(0.1 + 0.2 == 0.3)  # False
```
0.1과 0.2가 2진수로 정확히 표현되지 않기 때문.

**해결**: math.isclose() 활용
부동소수점 비교 시 절대 ==을 사용하지 않고, math.isclose() 활용.
```python
import math

print(math.isclose(0.1 + 0.2, 0.3))  # True
math.isclose(a, b, rel_tol=1e-9): a와 b가 상대 오차 10⁻⁹ 이내이면 True.
```
## 7. 소수점 반올림 (Rounding)
### round() 함수 사용

```python
print(round(3.14159, 2))  # 결과: 3.14
```
**round(값, 소수점 자리수)**: 지정된 자리수까지 반올림.

### decimal 모듈을 활용한 정밀 반올림

**ROUND_HALF_UP**: 가장 가까운 값으로 반올림.
```python
from decimal import Decimal, ROUND_HALF_UP

num = Decimal('3.145')
rounded = num.quantize(Decimal('0.01'), rounding=ROUND_HALF_UP)
print(rounded)  # 결과: 3.15
```
