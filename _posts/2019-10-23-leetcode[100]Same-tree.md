---
layout: post
title:  "刷题记录Leetcode100.Same tree"
date:   2019-10-23 15:21
categories: leetcode
---
leetcode第100题原题说明：

#### Description

Given two binary trees, write a function to check if they are the same or not.

Two binary trees are considered the same if they are structurally identical and the nodes have the same value.

----

#### Example 1:

	Input:     	  1         1

			  / \       / \

			 2   3     2   3

			[1,2,3],   [1,2,3]

	Output: true

----

#### Example 2:

	Input:     	  1         1

			  /           \

			 2             2

			[1,2],     [1,null,2]

	Output: false

----

#### Example 3:

	Input:     	  1         1

			  / \       / \

			 2   1     1   2

			[1,2,1],   [1,1,2]

	Output: false

----

题目中给定两个最最简单的二叉树，判断两个二叉树是否为相同的二叉树。这个题目所给的树深度最多为1,所以可以用很简单的方法就能做出来这个题。思路如下：

1.两棵树是否均为空树，若是则返回true;

2.若只有一个空树，返回false;

3.若树均不空且两棵树根不同，返回false;

4.若两棵树的根相同则比较左右子树是否均相等，是则true，否则false

C++代码如下：

{% highlight cpp linenos %}
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    bool isSameTree(TreeNode* p, TreeNode* q) {
        if(p == nullptr && q == nullptr) return true;
        if(p == nullptr || q == nullptr) return false;
        if(p->val != q->val) return false;
        return isSameTree(p->left, q->left) && isSameTree(p->right, q->right);
    }
};
{% endhighlight %}

