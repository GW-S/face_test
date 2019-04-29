请实现一个函数用来找出字符流中第一个只出现一次的字符。例如，当从字符流中只读出前两个字符"go"时，第一个只出现一次的字符是"g"。当从该字符流中读出前六个字符“google"时，第一个只出现一次的字符是"l"。

#include<vector>
#include<map>
class Solution
{
    
public:
    vector<char> v;
    map<char,int> m;
  //Insert one char from stringstream
    void Insert(char ch)
    {
          m[ch]++;
          v.push_back(ch);
    }
  //return the first appearence once char in current stringstream
    char FirstAppearingOnce()
    {
         for(char a:v)
         {
             if(m[a]==1){return a;}
             
         }         
        return '#';
    }
};
