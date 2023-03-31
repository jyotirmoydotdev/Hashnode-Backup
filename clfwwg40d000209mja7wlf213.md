---
title: "Merge Two Sorted Lists - LC 28"
datePublished: Fri Mar 31 2023 18:49:58 GMT+0000 (Coordinated Universal Time)
cuid: clfwwg40d000209mja7wlf213
slug: merge-two-sorted-lists-lc-28
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1680288529925/64cfcab7-3d69-4fc5-aae9-ae35341272d0.jpeg
tags: leetcode, linkedlists

---

# Question

You are given the heads of two sorted linked lists `list1` and `list2`.

Merge the two lists into a one-sorted list. The list should be made by splicing together the nodes of the first two lists.

Return *the head of the merged linked list*.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679433957436/f8e8aa3e-b086-4f71-93ac-e1c626803057.jpeg align="center")

```bash
Input: list1 = [1,2,4], list2 = [1,3,4]
Output: [1,1,2,3,4,4]
```

# Answer

Function `mergeTwoLists()` that takes two singly linked lists `list1` and `list2` as input, merges them into a single sorted linked list, and returns the head of the merged list.

The function creates a new linked list `ans` that will be used to store the merged list. It also creates a `curr` pointer that points to the last node of the `ans` list.

The function then enters a loop that continues until both `list1` and `list2` are empty. Within the loop, the function compares the values of the first nodes of `list1` and `list2`. If the value of the first node of `list1` is smaller than or equal to the value of the first node of `list2`, then the function appends the first node of `list1` to the `ans` list and moves the `list1` pointer to the next node. Otherwise, the function appends the first node of `list2` to the `ans` list and moves the `list2` pointer to the next node. In either case, the function also moves the `curr` pointer to the last node of the `ans` list.

After the loop, the function checks if either `list1` or `list2` is non-empty. If one of them is non-empty, then the function appends the remaining nodes of that list to the `ans` list.

Finally, the function returns the head of the `ans` list, which is the second node of the `ans` list (since the first node is a dummy node).

```cpp
class Solution {
public:
    ListNode* mergeTwoLists(ListNode* list1, ListNode* list2) {
        ListNode* ans=new ListNode();
        ListNode* curr=ans;
        while(list1 && list2){
            if(list1->val<=list2->val){
                curr->next=list1;
                list1=list1->next;
            }
            else{
                curr->next=list2;
                list2=list2->next;
            }
            curr=curr->next;
        }
        curr->next=list1?list1:list2;
        return ans->next;
    }
};
```