剑指offer:数组中的重复数字

随意就手撸出来的简单的一道题，主要考虑的是map的使用方式，然后考研指针的使用方式。

bool duplicate(int numbers[], int length, int* duplication) {
        
         // {2,3,1,0,2,5,3}
         map<int,int> m;// 底层是一个树，那就用树来做这件事。
         map<int,int>::iterator iter;
         // 
         
         if(length<2)return false;
        
         for(int i=0;i<length;i++)
         {
             if(m.find(numbers[i])==m.end())
             {
                 // 找不到的话，该怎么办?
                 m[numbers[i]] = 0;
             }
             else{
                 iter = m.find(numbers[i]);// 继续进行
                 *duplication = iter->first;
                 return true;
             }
             
         }
        
         return false;         
}
