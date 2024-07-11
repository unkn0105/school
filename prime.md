# Prime number Algorithm
---
소수들을 구하는데 가장 효과적인 앋고리즘은 무엇이 있을까 탐구를 하다 직접 만들게 됨

소수를 구하는 데는 여러 가지 방법이 있을 것이다.

그중 가장 간단하게 생각할 수 있는 것은 2부터 그수 까지 모두 나누었을떄 나누어 떨어지는 숫자가 한개(자기자신)일때 이다. 


-`노가다.py`
```python
num = list(range(1, 101))

def prime(n):
    if n==1:
        return False
    for i in range(2,n):
        if n%i==0: return False
    return True

for i in range(len(num)):
    if prime(num[i]):
        print(num[i], end=" ")
    else: continue    
```
하지만 이것 말고도 오래전 에라토스테네스라는 수학자는 한가지 방안을 고안해낸다. 바로 배수들을 없애는 것이다. 
그럼 코드를 짜보자


-`에라토스테네스.py`
```python
numbers = list(range(1, 101))

for i in range(2, int(100 ** 0.5) + 1):
    if i in numbers:
        for j in range(i * 2, 101, i):
            if j in numbers:
                numbers.remove(j)

print(numbers)
```
타임 모듈을 이용해 코드 실행 시간을 측정해봤다. 노가다: 0.000077sec, 에라토스테네스의 체:0.000069sec
약 0.000008sec의 차이가 난다. 그 이유는 무엇일까?


시간복잡도의 차이이다. GPT에 따르면 에라토스테네스의 체의 시간복잡도는 O(n log log n)이며 노가다는 O(n * sqrt(n))라고 한다.


탐구결과: 원래의 노가다 방식에서 에라토스테네스의 방식으로 오자 시간이 단축됨이 보여진다.
또한 시간 복잡도를 이용해 코드를 효율적으로 분석해나가며 엘리스코딩에서 배운 ~~(실은 다른데서 배웠지만)~~ 시간복잡도를 사용할 수 있었다.
