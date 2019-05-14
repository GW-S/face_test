剑指offer:不用加减乘除做加法

---
我无法想象，这样一道题，我做了将近一个小时。
我感觉我的脑袋里面有屎，我很可能不适合做程序员

为什么会错，因为carry的终止条件是==0，有可能carry会carry到最前面的节点。


```C++
  int Add(int num1, int num2)
{
    int sum  = num1 ^ num2;// 不同的就是    2
    int carry= (num1 & num2)<<1;// 相同的就是    1
    while(carry!=0)
    {
        //cout<<bitset<36>(sum)<<endl; // 问题是为什么会有这么多的1
        //cout<<bitset<36>(carry)<<endl;
        // 该怎么办？你说该怎么办？
        num1 =   sum;
        num2 =   carry;
        sum  =   num1 ^ num2;
        carry = (num1 & num2)<<1;
    }
    return sum;
}
```
