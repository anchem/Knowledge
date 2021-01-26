# 数据结构与算法

## 内容

### 常见数据结构

- 数组
- 链表：高频
- 栈：包括单调栈
- 队列：包括优先队列，双端队列
- 哈希表：高频
- 字符串
- 堆：高频
- 树：递归，层次遍历，前中后序遍历，二叉查找树，字典树
- 图：包括二分图，拓扑排序
- 线段树
- 并查集

### 常用算法

- 排序：快排和归并变体，循环排序
- 搜索
 - 深度优先搜索：高频，递归
 - 广度优先搜索：高频
- 二分法：背模板
- 分治法：常与二叉树一起出现
- 双指针：高频，变形多，快慢指针
- 滑动窗口
- 区间合并
- 贪心算法
- 动态规划：高频
- 拓扑排序：高频
- 位运算

## 数据结构

## 算法

### :point_right: Two points, 双指针类型

**【算法思想】**

双指针，指的是在遍历对象（数组、链表、字符串等）的过程中，不是普通的使用单个指针进行访问，而是使用两个相同方向（快慢指针）或者相反方向（对撞指针）的指针进行扫描，从而达到相应的目的。

相反方向的双指针，对撞指针，适用于数组，尤其是有序数组。

相同方向的双指针，快慢指针，两个指针步长不同；固定间距指针，两个指针间隔固定的距离，并且拥有相同的步长。适用于链表和数组。

#### 题目

[双指针标签](https://leetcode-cn.com/problemset/all/?topicSlugs=two-pointers)

### :point_right: Sliding window，滑动窗口类型

**【背景问题】**

滑动窗口主要用来解决一些**连续**的问题，比如满足一定条件的子串、子数组等。

主要应用的数据类型为**数组**或**字符串**等。

**【算法思想】**

滑动窗口算法有两个关键特点：

1. **滑动**：表示窗口是向着某一个方向移动的；
2. **窗口**：表示一个区间，这个区间可以是固定的，也可以是变化的，可以变大，也可以变小。

算法思想如下：

1. 我们在字符串 `S` 中使用双指针中的左右指针技巧，初始化 `left = right = 0`，把索引左闭右开区间 `[left, right)` 称为一个「窗口」。
2. 我们先不断地增加 `right` 指针扩大窗口 `[left, right)`，直到窗口中的字符串符合要求（比如包含了 `T` 中的所有字符）。
3. 此时，我们停止增加 `right`，转而不断增加 `left` 指针缩小窗口 `[left, right)`，直到窗口中的字符串不再符合要求（不包含 `T` 中的所有字符了）。同时，每次增加 `left`，我们都要更新一轮结果。
4. 重复第 2 和第 3 步，直到 `right` 到达字符串 `S` 的尽头。

其中，第 2 步相当于在寻找一个**可行解**，然后第 3 步在优化这个**可行解**，最终找到**最优解**。

**【算法框架】**

```java
/* 滑动窗口算法框架 */
void slidingWindow(String s, String t) {
    Map<char, int> need, window;
    for (char c : t) need[c]++;

    int left = 0, right = 0;
    int valid = 0; 
    while (right < s.length()) {
        // c 是将移入窗口的字符
        char c = s[right];
        // 右移窗口
        right++;
        // 进行窗口内数据的一系列更新
        ...

        /*** debug 输出的位置 ***/
        System.out.printf("window: [%d, %d)\n", left, right);
        /********************/

        // 判断左侧窗口是否要收缩
        while (window needs shrink) {
            // d 是将移出窗口的字符
            char d = s[left];
            // 左移窗口
            left++;
            // 进行窗口内数据的一系列更新
            ...
        }
    }
}
```

对于框架的使用，我们需要关心以下几个关键问题：

1. 当移动 right 扩大窗口，即加入字符时，应该更新哪些数据？
2. 什么条件下，窗口应该暂停扩大，开始移动 left 缩小窗口？
3. 当移动 left 缩小窗口，即移出字符时，应该更新哪些数据？
4. 我们要的结果应该在扩大窗口时还是缩小窗口时进行更新？

#### 题目

1. [滑动窗口的最大值](https://leetcode-cn.com/problems/hua-dong-chuang-kou-de-zui-da-zhi-lcof/)
2. [无重复字符的最长子串](https://leetcode-cn.com/problems/longest-substring-without-repeating-characters/)
3. [字符串的排列](https://leetcode-cn.com/problems/permutation-in-string/)
4. [找到字符串中所有字母异位词](https://leetcode-cn.com/problems/find-all-anagrams-in-a-string/)
5. [长度最小的子数组](https://leetcode-cn.com/problems/minimum-size-subarray-sum/)
6. [最大连续1的个数 III](https://leetcode-cn.com/problems/max-consecutive-ones-iii/)
7. [和相同的二元子数组](https://leetcode-cn.com/problems/binary-subarrays-with-sum/)
8. [水果成篮](https://leetcode-cn.com/problems/fruit-into-baskets/)
9. [尽可能使字符串相等](https://leetcode-cn.com/problems/get-equal-substrings-within-budget/)
10. [最小覆盖子串](https://leetcode-cn.com/problems/minimum-window-substring/)
11. [统计「优美子数组」](https://leetcode-cn.com/problems/count-number-of-nice-subarrays/)
12. [K 个不同整数的子数组](https://leetcode-cn.com/problems/subarrays-with-k-different-integers/)
13. [定长子串中元音的最大数目](https://leetcode-cn.com/problems/maximum-number-of-vowels-in-a-substring-of-given-length/)

## 资源

[信息学奥林匹克竞赛](https://oi-wiki.org/)
