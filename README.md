# HeapSort-AND-Kruskal-Algorithms
### Overview
####This repository contains C# implementations of
    #####1. Heap-Sort: A sorting algorithm that uses a heap to arrange elements in order.
    #####2. Kruskal's Algorithm: A method to find the Minimum Spanning Tree (MST) of a graph.

## Heap-Sort Algorithm

### Overview
This assignment demonstrates the use of the Heap-Sort algorithm to sort a sequence of numbers and provides an analysis of the algorithm's efficiency. The implementation is done in C# and adheres to best practices for algorithmic problem-solving.

### Required Algorithms for Heap-Sort

#### 1. HEAPIFY
Ensures the Max-Heap property for a subtree rooted at a specific index.

**Pseudocode:**
```plaintext
HEAPIFY(A, n, i):
    largest = i                // Assume i is the largest
    left = 2 * i + 1           // Left child index
    right = 2 * i + 2          // Right child index

    if left < n AND A[left] > A[largest]:
        largest = left

    if right < n AND A[right] > A[largest]:
        largest = right

    if largest != i:
        SWAP(A[i], A[largest])
        HEAPIFY(A, n, largest)
```

#### 2. BUILD_MAX_HEAP
Converts an unordered array into a Max-Heap.

**Pseudocode:**
```plaintext
BUILD_MAX_HEAP(A, n):
    for i = (n / 2) - 1 down to 0:
        HEAPIFY(A, n, i)
```

#### 3. HEAP_SORT
Sorts the array by repeatedly extracting the maximum element.

**Pseudocode:**
```plaintext
HEAP_SORT(A):
    n = length(A)
    BUILD_MAX_HEAP(A, n)

    for i = n - 1 down to 1:
        SWAP(A[0], A[i])
        HEAPIFY(A, i, 0)
```

### Analysis of Heap-Sort
1. **HEAPIFY**:
   - Time Complexity: \( O(\log n) \)
   - Space Complexity: \( O(1) \)

2. **BUILD_MAX_HEAP**:
   - Time Complexity: \( O(n) \)

3. **HEAP_SORT**:
   - Time Complexity: \( O(n \log n) \)
   - Space Complexity: \( O(1) \)

---

## Kruskal's Algorithm

### Overview
This assignment demonstrates the implementation of Kruskal's algorithm to find the Minimum Spanning Tree (MST) of a network. The solution involves the Union-Find data structure for cycle detection and edge selection.

### Required Algorithms for Kruskal’s Algorithm

#### 1. Union-Find Data Structure
Efficiently manages disjoint sets and supports cycle detection.

**Pseudocode:**
```plaintext
FIND(Parent, u):
    if Parent[u] != u:
        Parent[u] = FIND(Parent, Parent[u])
    return Parent[u]

UNION(Parent, Rank, u, v):
    rootU = FIND(Parent, u)
    rootV = FIND(Parent, v)

    if rootU != rootV:
        if Rank[rootU] > Rank[rootV]:
            Parent[rootV] = rootU
        else if Rank[rootU] < Rank[rootV]:
            Parent[rootU] = rootV
        else:
            Parent[rootV] = rootU
            Rank[rootU] += 1
```

#### 2. KRUSKAL_MST
Finds the MST by iteratively adding the smallest edge that does not form a cycle.

**Pseudocode:**
```plaintext
KRUSKAL_MST(G):
    Initialize Parent[] and Rank[]
    MST = []
    Sort edges in G by weight

    for each edge (u, v, weight):
        if FIND(Parent, u) != FIND(Parent, v):
            MST.add((u, v, weight))
            UNION(Parent, Rank, u, v)

    return MST
```

### Analysis of Kruskal’s Algorithm
1. **Sorting Edges**:
   - Time Complexity: \( O(E \log E) \)

2. **Union-Find Operations**:
   - Time Complexity: \( O(E \alpha(V)) \), where \( \alpha(V) \) is the inverse Ackermann function.

3. **Overall Complexity**:
   - Time Complexity: \( O(E \log E) \)
   - Space Complexity: \( O(V + E) \)
