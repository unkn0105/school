# Euclidean algorithm (유클리드 호제법)
---
-`유클리드 호제법이란?`

숫자 a, b가 있을 때 (단, a<b), a를 b로 나눈 나머지와 b 의 최대 공약수는 a 와 b 의 최대 공약수가 같다는 것을 의미한다.

또한 __"최소공배수 × 최대공약수 = 두 수의 곱"__ 이라는 공식을 이용해 효율적인 알고리즘을 만들 수 있다.

-`코드`(유클리드 호제법 사용)
```python
def gcd(a, b):
    while b != 0:
        a, b = b, a % b
    return a

def lcm(a, b):
    return (a * b) // gcd(a, b)

a, b = map(int, input("두 수를 입력하세요: ").split())
if a < b:
    a, b = b, a

g = gcd(a, b)
l = lcm(a, b)

print(f"최대공약수: {g}")
print(f"최소공배수: {l}")
```
-`코드`(유클리드 호제법 미사용)
```python
a, b = map(int, input("두 수를 입력하세요: ").split())
if a < b:
    a, b = b, a

factors_a = set()
for i in range(1, a+1):
    if a % i == 0:
        factors_a.add(i)

factors_b = set()
for i in range(1, b+1):
    if b % i == 0:
        factors_b.add(i)

common_factors = factors_a.intersection(factors_b)
g = max(common_factors)

l = (a * b) // g

print(f"최대공약수: {g}")
print(f"최소공배수: {l}")
```

코드의 길이만 보아도 시간의 차이가 있어보이는 두 코드이다. (사용:0.000003sec 미사용:0.000018sec)실제로도 큰 시간 차이가 난다.

이를 통해 난 새로운 알고리즘을 발견했고 이를 통해 정수론과 수학 그리고  컴퓨터과학의 합체를 기대한다.
