知识点总结：

1.reverse(v.begin(),v.end());
  vector容器实现反转。

2.deque 双向队列
  d.front();
  d.back();  // 后方的序列

  d.push_back();
  d.push_front();

  d.pop_back();
  d.pop_front();// 这是在前方和后方插入数据；

2.queue
  q.push();
  q.pop();
  q.front();
  q.back();
  q.empty()

3.二叉树的前序，后序，中序，层次等遍历方法

4.求find_element();其实还不如自己写个遍历。

5.map的遍历：map<int,int>::iterator

6.iter = m.find(key); if(iter!=m.end())

7.make_heap(),push_heap(),pop_heap().sort_heap()
 要点，在使用这些的时候，greater()和less()每次都要加，还不如用priority_heap()
 很好的一篇博客
 https://elloop.github.io/c++/2016-11-29/learning-using-stl-72-make-heap


8.set()用insert进行插入
  然后可以用迭代器进行迭代 
9.greater()才能真正定义一个小顶堆。

10.priority_queue<int> p; 这是一个很有问题的东西。
   push,top等文件

11.ambiguous 模棱两可，含糊不清

12.归并排序的理解：先拆分成小段，然后再用一种搜索的方式进行排序
13.最大堆的创建方式？

14.面积并：https://www.cnblogs.com/fenshen371/p/3214092.html
  leetcode 223. Rectangle Area
15.365. Water and Jug Problem

   C++的auto表达式

16.max和min的C++应用范围
17.https://leetcode.com/problems/water-and-jug-problem/ water和jug问题的待处理

18. Frog Jump leetcode403
   https://zhuanlan.zhihu.com/p/24569755

