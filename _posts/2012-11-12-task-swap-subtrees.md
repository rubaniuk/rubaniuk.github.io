---
# id: 19
title: 'Task: Swap Subtrees'
date: 2012-11-12T10:00:27-08:00
author: andrei
layout: post
# guid: http://www.rubaniuk.com/?p=19
# permalink: /?p=19
categories:
  - C++
  - Programming Interview
---

{% highlight cpp %}
// In a given binary tree swap right and left node,
// so that the tree will look like:
//          4                  4
//         / \                / \
//        2   5	    =>       5   2
//       / \                / \
//      1   3              3   1

typedef struct _TreeNode
{
	struct _TreeNode* pLeft;
	struct _TreeNode* pRight; //arbitrary
	int data;
} TreeNode, *PTreeNode; 

bool SwapSubtrees(PTreeNode root)
{
	if(!root)
	{
		return false;	
	}

	PTreeNode tmp = root->pRight;
	root->pRight = root->pLeft;
	root->pLeft = tmp;

	if(root->pRight)
	{
		SwapSubtrees(root->pRight);	
	}
	if(root->pLeft)
	{
		SwapSubtrees(root->pLeft);	
	}

	return true;
}
{% endhighlight %}