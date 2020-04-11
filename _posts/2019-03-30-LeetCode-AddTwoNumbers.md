---
layout : post
title : LeetCode AddTwoNumbers
categories: [LeetCode, Algorithm]
tags: [LeetCode, Algorithm]

---

## Example
<p class="message">
Input: (2 -> 4 -> 3) + (5 -> 6 -> 4) <br>
Output: 7 -> 0 -> 8 <br>
Explanation: 342 + 465 = 807.
</p>

## Solution
Runtime: 68 ms, faster than 84.09% of Python online submissions for Add Two Numbers.
Memory Usage: 11.8 MB, less than 5.16% Python online submissions for Add Two Numbers.

純粹把ListNode裡面的值用string記錄起來再一次轉換成Integer
在慢慢把他切成一個一個數字，在塞回ListNode裡

## Code
{% highlight python %}
class ListNode(object):
	def __init__(self,x):
		self.val = x
		self.next = None

class Solution(object) :
	def addTwoNumbers(self,l1,l2):
		l1_str = '' 
		l2_str = ''
		while True:
			if l1.next is None:
				l1_str = l1_str + str(l1.val)
				break
			else : 
				l1_str = l1_str + str(l1.val)
				l1 = l1.next
		l1_num = int(l1_str[::-1])

		while True :
			if l2.next is None:
				l2_str = l2_str + str(l2.val)
				break
			else:
				l2_str = l2_str + str(l2.val)
				l2 = l2.next
		l2_num = int(l2_str[::-1])
		ans = str(l1_num + l2_num)
		head = ListNode( int(ans[len(ans)-1: ]))
		cur = head
		for i in range(len(ans) - 1):
			cur.next = ListNode( ans[len(ans) - i -2 : len(ans) -i  -1] )
			cur = cur.next

		return head
{% endhighlight %}
