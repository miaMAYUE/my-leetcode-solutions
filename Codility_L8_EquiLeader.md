https://app.codility.com/programmers/lessons/8-leader/equi_leader/

求 最小的 A中未出现的 正整数

```python
def solution_hashing(A: list[int]) -> int:
    n = len(A)
    # 将负数和0替换成一个不会影响后续逻辑的值
    for i in range(n):
        if A[i] <= 0:
            A[i] = n + 1
    # 用负号标记出现过的数字
    for i in range(n):
        val = abs(A[i])
        if 1 <= val <= n:
            # 防重复标记
            if A[val - 1] > 0:
                A[val - 1] *= -1
    # 找第一个未被标记的位置
    for i in range(n):
        if A[i] > 0:
            return i + 1
    # 如果1到n都出现过，那么答案是 n+1
    return n + 1
```