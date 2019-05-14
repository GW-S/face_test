剑指offer:正则表达式匹配

这道题的问题在于要将其想象成一个有限状态机。

要根据pattern的指针进行操作，其中char* 因为是指针可以很好的利用。

在能用递归的时候尽量用递归。然后再进行其他，最后再考虑用循环。

最好用递归思想的时候，统一用递归思想。

```C++

        bool matchCore(char* str, char* pattern)
{
    if(*str=='\0' && *pattern== '\0')return true;
    if(*str!='\0' && *pattern== '\0')return false;

    if(*(pattern+1)=='*')
    {
        if(*pattern==*str||(*pattern=='.' && *str!='\0'))
        {
            // 精华在这里。
            return matchCore(str+1,pattern+2)||matchCore(str+1,pattern)||matchCore(str,pattern+2) ;
        }
        else
        {
            return matchCore(str,pattern+2);
        }
    }
    if(*str==*pattern|| (*pattern=='.'&& *str!='\0'))return matchCore(str+1,pattern+1);
    return false;
        }

bool match(char* str, char* pattern)
{
    if(str==nullptr||pattern==nullptr)
    {
        return false;
    }
    return matchCore(str,pattern);
}

```
