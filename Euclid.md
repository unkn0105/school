# Euclidean algorithm (유클리드 호제법)
---
-`유클리드 호제법이란?`

숫자 a, b가 있을 때 (단, a<b), a를 b로 나눈 나머지와 b 의 최대 공약수는 a 와 b 의 최대 공약수가 같다는 것을 의미한다.

또한 __"최소공배수 × 최대공약수 = 두 수의 곱"__ 이라는 공식을 이용해 효율적인 알고리즘을 만들 수 있다.

-`코드`
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
