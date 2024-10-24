19. Remove Nth Node From End of List
```
class Solution {
    int getSize(ListNode* head)
    {
        int size = 0;
        while(head)
        {
            size++;
            head = head->next;
        }
        return size;
    }
public:
    ListNode* removeNthFromEnd(ListNode* head, int n)
    {
        ListNode tempHead;
        ListNode* curr = &tempHead;
        curr->next = head;
        int listCount = getSize(&tempHead);
        for(int i = 0; i < listCount - n - 1; i++)
        {
            curr = curr->next;
        }
        curr->next = curr->next->next;
        return tempHead.next;
    }
};
```
```
class Solution {
public:
    ListNode* removeNthFromEnd(ListNode* head, int n)
    {
        ListNode tempHead;
        tempHead.next = head;
        ListNode* slow = &tempHead;
        ListNode* fast = &tempHead;
        for(int i = 0; i < n; i++)
            fast = fast->next;
        while(fast->next)
        {
            fast = fast->next;
            slow = slow->next;
        }
        slow->next = slow->next->next;
        return tempHead.next;
    }
};
```

Given the head of a linked list, remove the nth node from the end of the list and return its head.

Examples:
Example 1:
Input: head = [1,2,3,4,5], n = 2
Output: [1,2,3,5]

Example 2:
Input: head = [1], n = 1
Output: []

Example 3:
Input: head = [1,2], n = 1
Output: [1]
 
Constraints:
The number of nodes in the list is sz.
1 <= sz <= 30
0 <= Node.val <= 100
1 <= n <= sz
