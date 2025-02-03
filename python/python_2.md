# Python 타입의 동작과 특징

## 1. Python 데이터 타입 개요
Python의 데이터 타입을 이해하면 코드의 **효율성과 안정성**을 높일 수 있음.  
주요 개념:
- **Mutable(변경 가능)** vs **Immutable(변경 불가능)** 타입
- **깊은 복사(Deep Copy)** vs **얕은 복사(Shallow Copy)**
- **문자열이 불변(Immutable)인 이유**

---

## 2. Mutable과 Immutable 타입

### (1) Mutable vs Immutable
| 타입 | 변경 가능 여부 | 예시 |
|------|--------------|------|
| **Immutable** | 변경 불가능 | `int`, `float`, `bool`, `str`, `tuple` |
| **Mutable** | 변경 가능 | `list`, `dict`, `set` |

### (2) Immutable 예제
- Immutable 타입은 값을 변경하면 새로운 객체가 생성됨.
```python
x = 10
print(id(x))  # 메모리 주소 출력

x = x + 5
print(id(x))  # 새로운 객체가 생성됨 (주소 변경)
```
### (3) Mutable 예제
- Mutable 타입은 객체를 직접 변경 가능.
```python
lst = [1, 2, 3]
print(id(lst))  # 초기 리스트의 메모리 주소

lst.append(4)
print(id(lst))  # 동일한 메모리 주소 (객체가 변경됨)
```
## 3. 깊은 복사(Deep Copy)와 얕은 복사(Shallow Copy)
### (1) 얕은 복사(Shallow Copy)
- "=" 연산자를 사용하면 같은 객체를 참조하는 얕은 복사가 발생.
```python
a = [1, 2, 3]
b = a  # 같은 객체를 참조

b.append(4)
print(a)  # 결과: [1, 2, 3, 4] → 원본도 변경됨
```
### (2) 깊은 복사(Deep Copy)
- copy.deepcopy()를 사용하면 원본과 독립적인 복사본을 생성.
```python
import copy

a = [1, 2, [3, 4]]
b = copy.deepcopy(a)  # 깊은 복사

b[2].append(5)
print(a)  # 결과: [1, 2, [3, 4]] (원본 변경 없음)
print(b)  # 결과: [1, 2, [3, 4, 5]] (복사본만 변경됨)
```
### (3) 얕은 복사가 문제가 될 수 있는 경우
- 리스트 안에 리스트가 있는 경우, 얕은 복사는 내부 리스트를 참조하는 형태가 되어 원본까지 변경될 수 있음.
```python
a = [[1, 2], [3, 4]]
b = a[:]  # 얕은 복사

b[0].append(5)
print(a)  # 결과: [[1, 2, 5], [3, 4]] → 원본도 변경됨
```
**해결 방법**: 중첩 리스트가 포함된 경우 copy.deepcopy() 사용.
## 4. Python 문자열이 불변(Immutable)인 이유
### (1) 문자열이 불변한 이유
- 메모리 효율성
동일한 문자열을 여러 곳에서 사용할 때 중복 저장을 방지하여 메모리 절약.
interning(문자열 캐싱) 기법을 사용.
- 안전성
여러 곳에서 참조할 때 값이 변하지 않아 버그 방지.
해시 가능(hashable)하여 dict의 키로 사용 가능.
### (2) 문자열 변경 시 객체가 새로 생성되는 예제
```python
s = "hello"
print(id(s))  # 문자열의 메모리 주소

s = s + " world"
print(id(s))  # 새로운 문자열이 생성됨 (주소 변경)
```
### (3) 문자열을 수정하는 방법
 문자열은 불변이므로 직접 수정할 수 없고, 새로운 문자열을 생성해야 함.
```python
s = "Python"
s = s.replace("P", "J")  # 새로운 문자열 생성
print(s)  # "Jython"
```
### (4) 리스트는 가변(Mutable)
리스트는 가변이므로 직접 수정 가능.
```python
lst = ["P", "y", "t", "h", "o", "n"]
lst[0] = "J"
print("".join(lst))  # "Jython"
```
