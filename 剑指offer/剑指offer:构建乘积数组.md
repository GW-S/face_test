剑指offer:构建乘积数组
---
在这道题中，我的主要失误是没有认真考虑两个方向的问题，细节没有考虑到，为什么不考虑整个细节再写？

```python
class Solution:
    def multiply(self, A):
        # write code here
    # 我感到疲惫，深深的疲惫，就像是被榨干
    # 那是一种生不如死的感觉，就像好好睡了一觉，直到天亮
        if len(A) == 0:
            return []

        mat_left = []
        mat_right = []

        all_left = 1
        all_right = 1

        for index, each in enumerate(A):  # enumerate
            all_left = each * all_left
            mat_left.append(all_left)

        print(mat_left)


        for index in range(len(A))[::-1]:
            all_right = A[index] * all_right
            mat_right.insert(0,all_right)

        print(mat_right)
        mat_B = []
        mat_B.append(mat_right[1])
        # 第一个值该怎么搞，left和right都是和值，我到底该怎么办？
        for index in range(len(A))[1:-1]:
            mat_B.append(mat_left[index - 1] * mat_right[index + 1])
        mat_B.append(mat_left[-2])

        return mat_B
```
