# 개념정리
## 정렬(sorting) 알고리즘
> **정렬**은 `데이터를 특정한 기준에 따라서 순서대로 나열`하는 것을 말한다.<br>
상황에 적절하지 못한 정렬 알고리즘을 이용하면 프로그램이 비효율적으로 동작하기 때문에 정렬알고리즘을 공부하다보면 자연스럽게 알고리즘 효율의 중요성을 깨닫게 된다.

## 선택 정렬(Selection Sort)
> **선택 정렬**이란 데이터가 무작위로 여러 개가 있을 때, `이 중에서 가장 작은 데이터를 선택하여 맨 앞에 있는 데이터와 바꾸고, 그다음 작은 데이터를 선택하여 앞에서 두 번째 데이터와 바꾸는 과정`을 의미한다.<br>
이 과정을 반복해서 수행하다 보면, 전체 데이터의 정렬이 이루어진다.

--- 

# 문제 풀이

---
## <이것이 코딩 테스트다.>
### 예제 6-1
```
array = [7, 5, 9, 0, 3, 1, 6, 2, 4, 8]

for i in range(len(array)):
    min_index = i
    for j in range(i + 1, len(array)):
        if array[min_index] > array[j]:
            min_index = j
    array[i], array[min_index] = array[min_index], array[i] # 스와프

print(array)
```

> 예제 6-1은 선택 정렬로 오름차순 정렬한 소스코드이다.<br>
이 부분에선 `array[i], array[min_index] = array[min_index], array[i] # 스와프` 여기가 좀 이해가 안갔는데 `스와프`는 특정 리스트가 주어졌을 때 두 변수의 위치를 변경하는 작업을 의미한다.

---
---

## 삽입 정렬(Insertion Sort)
> 선택 정렬에 비해 난이도가 높은 편이지만 그만큼 실행 시간 측면에서 더 효율적이다.<br>
선택 정렬은 현재 데이터의 상태와 상관없이 무조건 모든 원소를 비교하고 교체하는 반면 삽입 정렬은 그렇지 않다.<br>
삽입 정렬은 특정한 데이터를 적절한 위치에 '삽입'한다는 의미에서 **삽입 정렬**이라고 부른다.<br>

---

# 문제 풀이

---
## <이것이 코딩 테스트다.>
### 예제 6-3
```
array = [7,5,9,0,3,1,6,2,4,8]

for i in range(1, len(array)):
    for j in range(i, 0, -1):
        if array[j] < array[j-1]: 
            array[j], array[j-1] = array[j-1], array[j]
        else:
            break
print(array)
```

> range의 세 번째 매개 변수는 `step`으로 -1이면 `start`부터 `end+1`인덱스까지 1씩 감소하여 진행하는 것이다.

---
---

## 퀵 정렬(Quick Sort)
> 퀵 정렬은 정렬 알고리즘 중에 제일 많이 사용되는 알고리즘이다.<br>
퀵 정렬과 비교할 만큼 빠른 알고리즘으로 **병합 정렬**도 있다.<br>

---

# 문제 풀이

---
## <이것이 코딩 테스트다.>
### 예제 6-5
```
array = [5,7,9,0,3,1,6,2,4,8]

def quick_sort(array):
    if len(array) <= 1:
        return array
    pivot = array[0] # 피벗은 첫번째 원소
    no_pivot_arr = array[1:] # 피벗을 제외한 배열 생성

    left_side = [x for x in no_pivot_arr if x <= pivot] # 피벗보다 작은 수들 왼쪽으로 분할
    right_side = [x for x in no_pivot_arr if x > pivot] # 피벗보다 큰 수들 오른쪽으로 분할

    return quick_sort(left_side) + [pivot] + quick_sort(right_side)

print(quick_sort(array))
```

---
---

## 계수 정렬(Count sort)
> 계수 정렬은 **특정한 조건이 부합할 때만 사용할 수 있 지만 매우 빠른 정렬 알고리즘**이다.<br>
모든 데이터가 양의 정수일 때, 데이터의 개수가 N, 데이터 중 최대값이 K일 때, 계수 정렬은 최악의 경우에도 수행 시간 O(N+K)를 보장한다.<br>
하지만 계수 정렬은 데이터의 크기 범위가 제한되어 정수 형태로 표현할 수 있을 때만 사용이 가능하다.<br>
계수 정렬은 앞서 다룬 3가지 정렬 알고리즘처럼 직접 데이터의 값을 비교한 뒤에 위치를 변경하며 정렬하는 방식이 아니다.<br>

---

# 문제 풀이

---
## <이것이 코딩 테스트다.>
### 예제 6-6
```
array = [7,5,9,0,3,1,6,2,9,1,4,8,0,5,2]

count = [0] * (max(array)+1) # 길이가 인덱스의 최댓값보다 1큰 0으로 이루어진 배열

for i in range(len(array)):
    count[array[i]] += 1

print(count)

for i in range(len(count)):
    for j in range(count[i]):
        print(i, end=" ")
```

