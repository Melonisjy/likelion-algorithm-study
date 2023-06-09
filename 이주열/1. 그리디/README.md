# 개념정리
> 그리디 = 탐욕법<br>
여기서 탐욕적이란 `현재 상황에서 지금 좋은 것만 고르는 방법`을 의미한다.<br>
따라서 `최적의 해`를 구하지 못할수도 있다.<br>
그렇기 때문에 `정당성 분석`을 하는 것이 가장 중요하다.
또한 그리디 문제에서 `가장 큰 순서대로` 혹은, `가장 작은 순서대로`와 같은 키워드를 통해 힌트를 얻게 된다.<br><br>

--- 

# 문제 풀이

---
## <이것이 코딩 테스트다.>
### 예제 3-1
```
a = int(input())
count = 0

list = [500, 100, 50, 10]
for coin in list:
    count += a // coin # list의 인덱스 0인 500부터 a를 나눈 몫을 count에 + 함.
    a %= coin # a를 a와 coin으로 나눈 나머지로 초기화

print(count)
```

> 예제 3-1은 대표적인 `그리디 알고리즘` 문제로 최적의 해를 보장하는 문제이다.<br>
그 이유는 가지고 있는 동전 중 큰 단위의 동전이 항상 작은 단위 동전의 배수이기 때문에 다른 해가 나올 수 없기 때문이다.<br>

### <문제> 1이 될 때까지
```
n, k = map(int,input().split())
count = 0

while n >= k:
    while n % k != 0:
        n -= 1
        count += 1
    n = n // k
    count += 1

while n > 1:
    n -= 1
    count += 1

print(count)
```
---

## <프로그래머스>
### 체육복
```
def solution(n, lost, reserve):
    answer = 0
    set_lost = set(lost) - set(reserve)
    set_reserve = set(reserve) - set(lost)
    
    for i in set_reserve:
        if i-1 in set_lost:
            set_lost.remove(i-1)
        elif i+1 in set_lost:
            set_lost.remove(i+1)
            
    answer = n - len(set_lost)
            
    
    return answer
```
> 먼저 `set`함수를 사용하여 각 배열(lost, reserve)를 `집합 자료형`으로 만들어준다. (중복 제거를 위해서) <br>
그러고 난 다음 반복문을 통해 여벌 옷(set_reserve)의 +1, -1값이 분실한 옷(set_lost)에 있는지 확인한 후 있으면 제거한다. <br>
총 인원에서 마지막 분실한 인원을 빼서 답을 구한다.<br>

