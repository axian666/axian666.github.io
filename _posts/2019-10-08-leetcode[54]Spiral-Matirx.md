---
layout: post
title:  "刷题记录Leetcode54.Spiral Matrix"
date:   2019-10-08 19:54
categories: leetcode
---
leetcode第54题原题说明：
# Description
Given a matrix of m x n elements (m rows, n columns), return all elements of the matrix in spiral order.
## Example 1:
{% highlight %}
Input:
[
 [ 1, 2, 3 ],
 [ 4, 5, 6 ],
 [ 7, 8, 9 ]
]
Output: \[1,2,3,6,9,8,7,4,5]
{% endhighlight %}
## Example 2:
{% hightlight %}
Input:
[
  [1, 2, 3, 4],
  [5, 6, 7, 8],
  [9,10,11,12]
]
Output: \[1,2,3,4,8,12,11,10,9,5,6,7]
{% endhighlight %}
    意思就是说给定一个m x n的整数矩阵，从左上角开始顺时针螺旋存入到一个一维数组中并输出。这道题的大致思路就是将给定的矩阵从外向里划分层次，第一层为最外层，第二层为次外层，依此类推直到最里层。
![img](~/axianBlog/_includes/54_spiralmatrix.png)
    如图，首先将最外层的左上角的坐标标记为(r1, c1),右下角坐标标记为(r2, c2),将每一层的四个边(最里层可能不是四个边)依次如图输出，这一层输出完毕之后进入下次层，代码如下：
{% highlight cpp %}
class Solution {
public:
    vector<int> spiralOrder(vector<vector<int>>& matrix) {
        if(matrix.empty())
            return {};
        vector<int> res;
		// 初始化坐标
        int r1 = 0, c1 = 0;
        int r2 = matrix.size() - 1, c2 = matrix[0].size() - 1;
		// 由外向里输出直到最里层
        while(r1 <= r2 && c1 <= c2){
			// 输出顶部
            for(int c = c1; c <= c2; c++)
                res.push_back(matrix[r1][c]);
			// 输出右面
            for(int r = r1 + 1; r <= r2; r++)
                res.push_back(matrix[r][c2]);
			// 如果这一层存在底部和左面则输出
            if(r1 < r2 && c1 < c2){
                for(int c = c2 - 1; c >= c1; c--)
                    res.push_back(matrix[r2][c]);
                for(int r = r2 - 1; r >= r1 + 1; r--)
                    res.push_back(matrix[r][c1]);
            }
			// 进入下一层
            r1++;c1++;
            r2--;c2--;
        }
        return res;
    }
};
{% endhighlight %}
