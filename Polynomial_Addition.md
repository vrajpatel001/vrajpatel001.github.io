---
plugins:
  - jekyll-relative-links
relative_links:
  enabled: true
  collections: true
theme: jekyll-theme-cayman
layout: post
title: "Polynomial Addition"
description: "Using Linked List"
---

### [Polynomial Addition](https://practice.geeksforgeeks.org/problems/polynomial-addition/1)

### Given two polynomial numbers represented by a linked list. The task is to complete the function addPolynomial() that adds these lists meaning adds the coefficients who have the same variable powers.
#### Note:  Given polynomials are sorted in decreasing order of power.

#### Example 1:
```
Input:
LinkedList1:  (1,x2) 
LinkedList2:  (1,x3)
Output:
1x^3 + 1x^2
Explanation: Since, x2 and x3 both have different powers as 2 and 3. So, their coefficient can't be added up.
```

#### Example 2:
```
Input:
LinkedList1:  (1,x3) -> (2,x2)
LinkedList2:  (3,x3) -> (4,x2)
Output:
4x^3 + 6x^2
Explanation: Since, x3 has two different coefficients as 3 and 1. Adding them up will lead to 4x3. Also, x2 has two coefficients as 4 and 2. So, adding them up will give 6x2.
```

```
Expected Time Complexity: O(N+M)
Expected Auxiliary Space: O(1)
Constraints:
    1 <= N, M <= 105
    1 <= x, y <= 106
```

### C++ Implementation
```c++
/* Link list Node */
struct Node
{
    int coeff;
    int pow;
    struct Node* next;
    
    Node(int c, int p){
        coeff = c;
        pow = p;
        next = NULL;
    }
    
};

class Solution{
  public:
    Node* addPolynomial(Node *p1, Node *p2)
    {
        if(p1->pow < p2->pow) swap(p1, p2);
        Node *ans = p1;
        while(p1) {
            Node *v = p1;
            while(p1 and p2 and p1->pow >= p2->pow) {
                if(p1->pow == p2->pow){
                    p1->coeff += p2->coeff;
                    p2 = p2->next;
                }
                v = p1;
                p1 = p1->next;
            }
            v->next = p2;
            swap(p1, p2);
        }
        return ans;
    }
};
```

#### Python Implementation

```python
# Node Class    
class node:
    def __init__(self, coeff, pwr):
        self.coef = coeff
        self.next = None
        self.power = pwr

class Solution:
    def addPolynomial(self, p1, p2):
        # Code here
        if p1.power<p2.power: p1,p2=p2,p1
        ans = p1
        while p1:
            v = p1
            while p1 and p2 and p1.power>=p2.power:
                if p1.power==p2.power:
                    p1.coef+=p2.coef
                    p2=p2.next
                v = p1
                p1 = p1.next
            v.next = p2
            p1,p2=p2,p1
        return ans
```