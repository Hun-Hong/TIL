# Python 데이터와 표현식 기초

## 1. 표현식(Expression)과 값(Value)

### 표현식
- Python에서 **표현식**은 값을 계산하거나 반환하는 코드 조각.
- 예시:
  ```python
  3 + 5  # 결과: 8
  "Hello" + " World"  # 결과: "Hello World"
  ```
### 값(Value)
값은 표현식의 결과로 반환되는 데이터.

값의 예시:
- 숫자형: 5, 3.14
- 문자열: "Python"
### 표현식의 종류
- 리터럴(Literal): 값 자체를 표현.
```python
42  # 숫자 리터럴
"Python"  # 문자열 리터럴
```
연산식: 연산자를 이용한 계산.
```python
7 * 8  # 곱셈
10 / 3  # 나눗셈
```
함수 호출: 내장 함수나 사용자 정의 함수를 호출.
```python
len("Python")  # 문자열 길이 반환
```

## 2. 타입(자료형)
### 기본형 타입
- 숫자형(Numeric):
```python
a = 10  # 정수형(int)
b = 3.14  # 실수형(float)
c = 2 + 3j  # 복소수(complex)
```
- 문자열(String):
```python
text = "Hello, Python!"
```
- 불리언(Boolean):
```python
is_ready = True
```
### 심화형 타입
- 리스트(List):
순서가 있는 데이터의 모음.
```python
fruits = ["apple", "banana", "cherry"]
```
- 튜플(Tuple):
순서가 있지만 불변(immutable).
```python
coordinates = (10, 20)
```
- 딕셔너리(Dictionary):
키-값 쌍으로 이루어진 데이터.
```python
person = {"name": "Alice", "age": 25}
```
- 집합(Set):
중복을 허용하지 않는 데이터 모음.
```python
unique_numbers = {1, 2, 3, 4}
```
## 3. 진수 표현
**진수 표현 방법**
- 2진수(Binary): 접두사 0b 사용.
```python
binary_number = 0b1010  # 결과: 10 (10진수로 변환)
```
- 8진수(Octal): 접두사 0o 사용.
```python
octal_number = 0o12  # 결과: 10 (10진수로 변환)
```
- 16진수(Hexadecimal): 접두사 0x 사용.
```python
hex_number = 0xA  # 결과: 10 (10진수로 변환)
```
진수 변환 함수
Python 내장 함수로 진수 변환 가능:
```python
num = 10

print(bin(num))  # 결과: '0b1010'
print(oct(num))  # 결과: '0o12'
print(hex(num))  # 결과: '0xa'
```
## 4. Python에서 타입 체크하기
**type() 함수로 데이터 타입 확인:**
```python
print(type(42))       # <class 'int'>
print(type(3.14))     # <class 'float'>
print(type("Python")) # <class 'str'>
```
