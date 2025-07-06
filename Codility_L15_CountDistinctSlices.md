https://app.codility.com/programmers/lessons/15-caterpillar_method/count_distinct_slices/

求切片个数，要求切片内不含重复数字。

```python
def solution(M,A):
    n = len(A)
    front = 0
    back = 0
    distinct_slices = 0
    limit = 1_000_000_000
    seen = [False] * (M+1)
    while back < n:
        while front < n and not seen[A[front]]:
            seen[A[front]] = True
            distinct_slices += front - back + 1
            if distinct_slices >= limit:
                return limit
            front += 1
        if front == n:
            break
        while A[back] != A[front]:
            seen[A[back]] = False
            back += 1
        seen[A[back]] = False
        back += 1
    return distinct_slices
```