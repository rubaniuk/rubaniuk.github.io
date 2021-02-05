---
# id: 72
title: 'Interview question: in-order traversal of a binary tree'
date: 2013-03-23T09:00:49-07:00
author: andrei
layout: post
# guid: http://www.rubaniuk.com/?p=72
# permalink: /?p=72
categories:
  - C++
  - Programming Interview
---
{% highlight cpp %}
typedef struct _TreeNode
{
	struct _TreeNode* pLeft;
	struct _TreeNode* pRight;
	int data;
} TreeNode, *PTreeNode;

void BinaryTreeInorderTraversal(PTreeNode root)
{
	static int max;

	if(!root)
	{
		return;
	}

	BinaryTreeInorderTraversal(root->pLeft);
	printf("%d\t", root->data);
	BinaryTreeInorderTraversal(root->pRight);
}
{% endhighlight %}