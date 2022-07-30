---
title: "Kernighan Lin Algorithm"
description: "For Bipartition"
---

#### Description of the Algorithm
- Kernighan Lin is a method of partitioning a graph containing nodes and vertices into separate subsets that are connected together in an optimal manner, Since a graph can be used to represent an electrical network containing blocks, the Kernighan-Lin algorithm can be extended to partitioning circuits into sub-circuits.
- Used to find minimal numbers of connections between partitions to improve speed or decrease power consumption,
- It is an iterative algorithm meaning that the graph/circuit may already be partitioned, but application of Kernighan-Lin will try to improve or optimize the partition.
- Kernighan-Lin is a greedy algorithm meaning the algorithm will make changes if there is a benefit right away without consideration to other possible ways of obtaining an optimal solution. 
- One bisection or cut is made to the partition only, so partitioning using Kernighan-Lin will result in only two partitions. Partitions must be equal size.


#### Psuedocode of the Algorithm
- Algorithm: Kernighan-Lin(G)
- Input: G = (V, E), |V| = 2n.
- Output: Balanced bi-partition A and B with “small” cut cost.
```c++
begin
Bipartition G into A and B such that |VA| = |VB|, VA ∩ VB = ∅, and VA ∪ VB = V.
repeat
    Compute Dv, ∀ v ∈ V.
    for i =1 to n do
    Find a pair of unlocked vertices vai ∈ VA and vbi ∈ VB whose exchange makes the largest decrease or smallest increase in cut cost;
    Mark vai and vbi as locked, store the gain , and compute the new Dv, for all unlocked v ∈ V;
    Find k, such that Gk = is maximized;
    if Gk > 0 then
    Move va1, …, vak from VA to VB and vb1, …, vbk from VB to VA;
    Unlock v, ∀ v ∈ V.
until Gk ≤ 0;
end
```

#### Python implementation for swapping nodes during partition
```python
mark = []
partition = []
cut_s = []
while(len(mark) != pairs-1):
    r_best, ij, part = [], [], []
    r_old = cut_size(n1, n2)
    for i in range(len(n1)):
        for j in range(len(n2)):
            if ([n1[i],n2[j]] not in mark and ([n2[j],n1[i]] not in mark)):
                n11, n22 = n1.copy(), n2.copy()
                n11[i] = n2[j]
                n22[j] = n1[i]
                del_R = r_old - cut_size(n11, n22)
                r_best.append(del_R)
                part.append([n11, n22])
                ij.append([n11[i],n22[j]])
    a = np.argmax(r_best)
    c_part = part[a]
    partition.append(c_part)
    mark.append(ij[a])
    cut_s.append(cut_size(c_part[0], c_part[1]))
    n1, n2 = c_part[0], c_part[1]
return(cut_s[np.argmin(cut_s)], partition[np.argmin(cut_s)])
```