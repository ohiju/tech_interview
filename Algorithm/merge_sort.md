# 병합 정렬

- 합병 정렬이라고도 부른다.

- 분할 정복 개념과 재귀 알고리즘을 이용

**시간 복잡도**
|평균|최선|최악|
|------|---|---|
|Θ(nlogn)|Ω(nlogn)|O(nlogn)|


*분할 정복이란?*

- 주어진 배열을 원소가 하나 밖에 남지 않을 때까지 계속해서 둘로 쪼갠 후 다시 크기 순으로 재배열하면서 원래 크기의 배열로 합치는 것(merge)

![merge_sort](./img1.gif)

- 분할 단계와 병합 단계로 나눌 수 있음
- 전반적인 반복의 수는 점점 절반으로 줄어들 기 때문에 O(logN) 시간이 필요하며, 각 패스에서 병합할 때 모든 값들을 비교해야 하므로 O(N) 시간이 소모. 따라서 총 시간 복잡도는 O(NlogN).

```python
# 예제 코드
def merge_sort(arr):
    if len(arr) < 2:
        return arr

    mid = len(arr) // 2
    low_arr = merge_sort(arr[:mid])
    high_arr = merge_sort(arr[mid:])

    merged_arr = []
    l = h = 0
    while l < len(low_arr) and h < len(high_arr):
        if low_arr[l] < high_arr[h]:
            merged_arr.append(low_arr[l])
            l += 1
        else:
            merged_arr.append(high_arr[h])
            h += 1
    merged_arr += low_arr[l:]
    merged_arr += high_arr[h:]
    return merged_arr
```