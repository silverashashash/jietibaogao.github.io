## Middle of a linked list

### Description

Find the middle node of a linked list.

### Example

**Example 1:**

```
Input:  1->2->3
Output: 2	
Explanation: return the value of the middle node.

```

**Example 2:**

```
Input:  1->2
Output: 1	
Explanation: If the length of list is  even return the value of center left one.	

```

  




这里使用快慢指针的方法来寻找终点。  
可以确保时间复杂度是 O\(n/2\)

快指针每次两步，慢指针每次一步。  
快指针到尾的时候，慢指针就是中点。

