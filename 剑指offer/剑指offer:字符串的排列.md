剑指offer:字符串的排列
这道题的思想没问题，问题在于我又多谢了一个等于号，导致了目前的错误。


#include<iostream>
#include<vector>
#include<stack>
#include<deque>
#include<queue>
#include<map>
#include<set>

using namespace std;



vector<string> v;

void dfs(string dp,int i,string str,string now)
{

    if(str.size()==now.size()){
        v.push_back(now);
        return;}

    if(dp[i]=='#')return;

    char temp = dp[i];
    string  now_temp = now;
    dp[i] = '#';

    now = now + str[i];
    cout<<i<<" "<<str[i]<<endl;
    for(int i=0;i<str.length();i++)
    {
        dfs(dp,i,str,now);
    }
    dp[i] = temp;
    now = now_temp;
    return;
}


vector<string> Permutation(string str) {

    vector<string> ans;

    if(str.length()==0) return ans;

    string dp = str;

    for(int i=0;i<str.length();i++)
    {
        string now = "";
        dfs(dp,i,str,now);
    }

    set<string> s;
    s.insert(v.begin(),v.end());
    ans.assign(s.begin(),s.end());

    return ans;
    // 根据map的大小，建立数组，数组表示哪里不能去，邻接表，和二维数组，二维数组通常表示大小，而邻接表，直接表示能不能去
    // 一维数组表示是否走过，如果没走过，就可以走了

    // 针对map定义一个一维数组
}

int main(){
    vector<string> ans = Permutation("abc");

    for(auto each:ans){cout<<each<<endl;}
}
