# 정렬

[정렬 참고 사이트_나무위키](https://namu.wiki/w/%EC%A0%95%EB%A0%AC%20%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98#s-4.2.3)

실제 응용에서는 상황에 따라 두 가지 이상의 정렬 방법을 사용하는 경우가 많다.

#### **✅ 예시**

- **퀵 정렬**

정렬 대상이 특정 크기 이하로 단편화 될 때까지 사용

- **삽입정렬**

특정 크기 이하가 됐을 때에는 작은 규모에서 강점을 보인다

- **힙정렬**

특정 횟수 이상 재귀호출이 발생하면 **O(n lon n)**이 보장된다.



## 시간 복잡도 : 연산 횟수에 비한 동작시간

‘**입력 값의 변화에 따라** 연산을 실행할 때, **연산 횟수에 비해 시간**이 얼마만큼 걸리는가?’라는 말이다.



#### **🔻 효율적인 알고리즘은? (입력 값(양) vs 연산시간)**

입력 값(양)이 커짐에 따라 **증가하는 시간의 비율을 최소화**한 알고리즘



#### **🔷 시간 복잡도를 표기하는 방법**

- **Big-O(빅-오) ⇒** 상한 점근 : **최악**
- **Big-Ω(빅-오메가) ⇒** 하한 점근 : **최선**
- **Big-θ(빅-세타) ⇒** 그 둘의 평균 : **중간(평균)**



### **🔳 Big-O 표기법**

**최악의 경우를 고려**하므로, 프로그램이 실행되는 과정에서 소요되는 **최악의 시간까지 고려**할 수 있다.

#### **🔹 표기법의 종류**

1. **O(1)** : 상수(constant)
2. **O(log n)** : 로그
3. **O(n)** : 선형
4. **O(n log n)** : 선형 로그
5. **O(n^2)** : 다차(Polynomial)
6. **O(2^n)** : 지수(Exponetial)
7. **O(n!)** : 팩토리얼(factorial)

**📍 <u>여기서 log의 지수는 항상 2다.</u>**

<img src="https://images.velog.io/images/youngblue/post/3335929a-aa03-4da7-b272-43adbba9b751/big-o.png" style="zoom:67%;" />

<img src="https://t1.daumcdn.net/cfile/tistory/99EF1E395C7EB4B601" alt="Untitled" style="zoom:67%;" />

#### **🔸 특징**

1. **상수항을 무시 : O(N+5) → O(N)**
2. **계수도 무시 : O(3N) → O(N)**
3. **최고차항만 표기 : O(3N^3+2N^2+…) → O(N^3)**



## 버블정렬(bubble sort) : O(N^2)

계산 시간이 정렬할 자료의 수의 제곱에 비례해서 늘어난다.  → **최악의 정렬**이라고 볼 수 있다..

즉, 1만 개를 1초에 정렬하면 10만 개를 정렬하는 데에는 100초 정도가 필요하다.



#### **🔸 정렬방법**

- 서로 인접한 두 원소를 검사하여 크기가 순서대로 있지 않으면 **서로 교환**한다. (**시행마다 가장 큰 자료가 맨 뒤로 이동**)
  
    → 첫 번째와 두 번째, 두 번째와 세 번째 자료를 … $N-1$과  $N$자료를 비교하여 교환한다.
    
    → ✅ **최대 연산 횟수**: $_NC_2 = N(N-1)/2$ 번의 시행을 한다.
    
- 1회전을 수행하고 나면 **가장 큰 자료가 맨 뒤로 이동**하므로 2회전에는 맨 끝의 자료는 정렬에서 제외한다.
  
    →한 번 돌 때마다 **마지막 하나가 정렬**되므로 원소들이 거품이 올라오는 것처럼 보여 버블정렬이다.
    

<img src="https://blog.kakaocdn.net/dn/bShmWc/btq0iAVbeB4/QmmStNtB3LkMPXV2KYr6x0/img.png" alt="Untitled" style="zoom: 67%;" />



#### **✅ 파이썬 구문 예시**

```python
def bubble_sort(lst, size):                 # lst : 리스트, size: 자료의 수 = (len(lst))
    for i in range(size-1, 0, -1):          # N-1 에서 0의 범위가 -1씩 작아진다.
        for j in range(i):
            if (lst[j] > lst[j+1]):         # 앞의 숫자가 더 크다면
                lst[j], lst[j+1] = lst[j+1], lst[j]
```

##### **🔻 최적화(정렬 됐는지 확인하는 factor 추가)**

```python
def bubble_sort(lst, size):                 # lst : 리스트, size: 자료의 수 = (len(lst))
    for i in range(size-1, 0, -1):          # N-1 에서 0의 범위가 -1씩 작아진다.
        swapped = False                     # 종료 조건
        for j in range(i):
            if (lst[j] > lst[j+1]):         # 앞의 숫자가 더 크다면
                lst[j], lst[j+1] = lst[j+1], lst[j]
        if not swapped:                     # 자료의 교환이 이루어지지 않은 경우(정렬됨)
            break
```



#### **✅ 백준 버블 정렬 문제**

[https://www.acmicpc.net/problem/5531](https://www.acmicpc.net/problem/5531)(버블 정렬 문제) (ctrl + 클릭)

**응용으로 풀어보는 것을 추천!**