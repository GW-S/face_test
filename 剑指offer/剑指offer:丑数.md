剑指offer:丑数

---
我感到压抑，很多事情做不来，做不到，就想离开

 int GetUglyNumber_Solution(int index) {
        // 其实蛮简单的，设置一个空间，值设置为1
        // 如果是你，会怎么处理呢？
        // 我该怎么办呢？
        // 怎么确定都是最小的呢，我无法理解
        
        // 对于前三个丑数来说，我要做的只是判断当前值运作到哪里了，选出三个中的最小值
        // 然后再创建新的空间，我该怎么办？
        
        if(index==0)return 0;
        if(index==1)return 1;
        
        int* store = new int[index+1];
        store[1] = 1;
        int point1 = 1;
        int point2 = 1;
        int point3 = 1;
        

        int now_pos = 2;
        
        while(now_pos<=index)
        {
            int now_1 = store[point1] * 2;
            int now_2 = store[point2] * 3;
            int now_3 = store[point3] * 5;

            if(now_1<=now_2&&now_1<=now_3)
            {
                store[now_pos]=now_1;
                point1 ++;
            }
            if(now_2<=now_1&&now_2<=now_3)
            {
                store[now_pos]=now_2;
                point2 ++;
            }
            if(now_3<=now_2&&now_3<=now_1)
            {
                store[now_pos]=now_3;
                point3 ++;
            }
            now_pos++;
        }

        return store[index];
    }
};


