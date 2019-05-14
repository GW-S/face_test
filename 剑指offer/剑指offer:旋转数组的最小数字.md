剑指offer:旋转数组的最小数字
---
这道题妨碍我的，竟然是python是没有{}的，恕我直言，python刷题真的爽

```python
def minNumberInRotateArray(self, rotateArray):
            right = len(rotateArray)
            if right== 0:
                return 0
            right = right -  1
            if right==0:
                return rotateArray[0]
            
            while( (rotateArray[right]>=rotateArray[right-1]) and right>1 ):
            
                right-=1
            
            
            if rotateArray[right]>=rotateArray[right-1]:
                return rotateArray[right-1]
            else:
                return rotateArray[right]
```
