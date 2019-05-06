C++常用技术点/Users/sheng/Desktop ：

1.string转为char*格式
  str = "abc"
  char* p = (char*)str.c_str();

2.sprintf 把数字打印到string中，只需要理解就好

3.sizeof,strlen,前者返回数组所占总空间的字节数，后者返回字符串占字节数

4.strcpy	char* strcpy(char *dest,const char*src);

5.C++建立二维数组 int* a = new int[100];

6.pair的用法：pair<int,float>

7.memset的用法

8.有构造函数的时候，用构造函数进行赋值

9.char *p = 'hello'
  char*p = p.c_str()

10.to_string

11.数组给vector赋值

12.vector在头部插入一个节点0

13.C++ map容器的用法，map<string,int>
	map::iterator iter;
	map.find()!map.end() 这是其中的一个重要的操作

14.
