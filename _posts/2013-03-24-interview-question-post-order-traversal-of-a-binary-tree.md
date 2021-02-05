---
# id: 79
title: 'Interview question: post-order traversal of a binary tree'
date: 2013-03-24T09:00:36-07:00
author: andrei
layout: post
# guid: http://www.rubaniuk.com/?p=79
# permalink: /?p=79
categories:
  - C++
  - Programming Interview
---
{% highlight cpp %}typedef struct _TreeNode
{
	struct _TreeNode* pLeft;
	struct _TreeNode* pRight;
	int data;
} TreeNode, *PTreeNode;

void BinaryTreePostorderTraversal(PTreeNode root)
{
	static int max;

	if(!root)
	{
		return;
	}

	BinaryTreePostorderTraversal(root->pLeft);
	BinaryTreePostorderTraversal(root->pRight);
	printf("%d\t", root->data);
}{% endhighlight %}