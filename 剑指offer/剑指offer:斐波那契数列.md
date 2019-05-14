剑指offer:斐波那契数列
```python
def Fibonacci(self, n):
        # write code here
        
        # 0 ,1,1,2,3,5
        
        
        if(n==0):
            return 0
        if(n==1):
            return 1
        if(n==2):
            return 1
        if(n>2):
            # 对于大于2的数字，我该怎么办？
            first = 1
            second = 1
            i= 3
            while i<=n:
                ans = first + second
                first = second
                second = ans
                i+=1
            return ans
```
