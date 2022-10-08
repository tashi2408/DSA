## 142. Linked List Cycle II

##### Medium | C++ Code Solution Explanation | Linked List

[Link to the Problem](https://leetcode.com/problems/linked-list-cycle-ii/)

#### Problem

Given the head of a linked list, return the node where the cycle begins. If there is no cycle, return null.

There is a cycle in a linked list if there is some node in the list that can be reached again by continuously following the next pointer. Internally, pos is used to denote the index of the node that tail's next pointer is connected to (0-indexed). It is -1 if there is no cycle. Note that pos is not passed as a parameter.

Do not modify the linked list.

#### Solution

- With floyd cycle method we can reach to either head or tail of the loop.
- We then start from begining and move slow pointer till both meet.
- It is the tail of the linked list containing a loop.

#### Code

```
ListNode *detectCycle(ListNode *head) {
        ListNode *slow_p = head, *fast_p = head;

    while (slow_p && fast_p && fast_p->next) {
        slow_p = slow_p->next;
        fast_p = fast_p->next->next;
        if (slow_p == fast_p) {
            cout<<slow_p->val;
            fast_p= head;
            while(slow_p!=fast_p){
                fast_p=fast_p->next;
                slow_p=slow_p->next;
            }
            return slow_p;
        }
    }
    return nullptr;
    }
```

#### Complexity

Time Complexity: O(N)

Reason: We can take overall iterations and club them to O(N)

Space Complexity: O(1)

Reason: No extra data structure is used.
