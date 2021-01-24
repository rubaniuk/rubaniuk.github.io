---
# id: 66
title: 'Interview question: pre-order traversal of a binary tree'
date: 2013-03-22T09:00:20-07:00
author: andrei
layout: post
# guid: http://www.rubaniuk.com/?p=66
# permalink: /?p=66
categories:
  - C++
  - Programming Interview
---
<pre class="brush: cpp; gutter: true">typedef struct _TreeNode
{
	struct _TreeNode* pLeft;
	struct _TreeNode* pRight;
	int data;
} TreeNode, *PTreeNode; 

void BinaryTreePreorderTraversal(PTreeNode root)
{
	static int max;

	if(!root)
	{
		return;
	}

	printf("%d\t", root-&gt;data);
	BinaryTreePreorderTraversal(root-&gt;pLeft);
	BinaryTreePreorderTraversal(root-&gt;pRight);
}</pre>