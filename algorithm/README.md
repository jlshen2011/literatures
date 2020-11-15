# Data Structures and Algorithms Study Notes

## Time Complexity
### Master Theorem

<img src="https://i.stack.imgur.com/SLVoZ.png" alt="what I know about the master theorem">

### Big-O
https://www.bigocheatsheet.com/


## Arrays and Strings
### Practice Problems
* 3 Longest Substring Without Repeating Characters
* 28 Implement strStr()
* 43 Multiply Strings
* 26 Remove Duplicates from Sorted Array


## Linked Lists
### Linked Lists Class and APIs
```python
class Node:
    def __init__(self, data, next=None):
        self.data = data
        self.next = next

class LinkedList: 
    def __init__(self): 
        self.head = None
  
    # Function to insert a new node at the beginning 
    def push(self, new_data): 
        new_node = Node(new_data, self.head) 
        self.head = new_node         
                
    def print_list(self):
        node = self.head
        while node:
            print(node.data, end=" ")
            node = node.next
```

### Practice Problems
* 19 Remove Nth Node From End of List
* 21 Merge Two Sorted Lists
* 24 Swap Nodes in Pairs
* 25 Reverse Nodes in k-Group
* 83 Remove Duplicates from Sorted List
* 141 Linked List Cycle
* 142 Linked List Cycle II
* 206 Reverse Linked List
* 237 Delete Node in a Linked List



## Stacks and Queues
### Practice Problems
* 20 Valid Parentheses
* 84 Largest Rectangle in Histogram
* 225 Implement Stack using Queues
* 232 Implement Queue using Stacks
* 239 Sliding Window Maximum
* 739 Daily Temperatures
* 844 Backspace String Compare

## Heaps and Priority Queues
Implemented by:
* Heap
* Binary search tree

### Practice Problems
* 23 Merge k Sorted Lists
* 253 Meeting Rooms II
* 295 Find Median from Data Stream
* 347 Top K Frequent Elements
* 703 Kth Largest Element in a Stream
* Sort a K-sorted Array
```python
def sort_k_sorted_array(self, nums, k):
    min_heap, res = [], []
    for num in nums[:k]:
        heapq.heappush(min_heap, num)
    for num in nums[k:]:
        smallest = heapq.heappushpop(min_heap, num)
        res.append(smallest)
    while min_heap:
        smallest = heapq.heappop(min_heap)
        res.append(smallest)
    return res
```




## Maps and Sets
HashMap vs TreeMap
HashSet vs TreeSet
Hashtable vs binary search tree

### Practice Problems
* 1 Two Sum
* 15 3Sum
* 242 Valid Anagram
* 336 Palindrome Pairs
* 340 Longest Substring with At Most K Distinct Characters



## Trees 
### Binary Search Tree
### Segment Tree
### Fenwick Tree/Binary Indexed Tree
### Tree Traversals
```python
def preorder(self, root):
    if root:
        self.path.append(root.val)
        self.preorder(root.left)
        self.preorder(root.right)
        
def inorder(self, root):
    if root:
        self.preorder(root.left)
        self.path.append(root.val)        
        self.preorder(root.right)

def postorder(self, root):
    if root:
        self.preorder(root.left)
        self.preorder(root.right)
        self.path.append(root.val)
```

### Practice Problems
* 94 Binary Tree Inorder Traversal (Without Recursion)
* 98 Validate Binary Search Tree
* 101 Symmetric Tree
* 104 Maximum Depth of Binary Tree
* 110 Balanced Binary Tree
* 111 Minimum Depth of Binary Tree
* 112 Path Sum
* 129 Sum Root to Leaf Numbers
* 144 Binary Tree Preorder Traversaln (Without Recursion)
* 199 Binary Tree Right Side View
* 230 Kth Smallest Element in a BST
* 230 Kth Smallest Element in a BST
* 235 Lowest Common Ancestor of a Binary Search Tree
* 236 Lowest Common Ancestor of a Binary Tree
* 285 Inorder Successor in BST


## Graphs
### Depth-First-Search
### Breadth-First-Search
### Topological Sort
### Union Find
### Dijkstra Algorithm
### Bellman-Ford Algorithm

### Practice Problems
* 200 Number of Islands
* 269 Alien Dictionary
* 308 Range Sum Query 2D - Mutable
* 407 Trapping Rain Water II
* 315 Count of Smaller Numbers After Self
* 785 Is Graph Bipartite?
* Solve Maze
```python
## recursion
def dfs(maze, x, y):
    If x == B[0] and y == B[1]:
        Return True
    Maze[x][y] = -1
    For d in directions:
        I, j = x + d[0], y + d[1]
        If isSafe(maze, I, j) and dfs(maze, I, j):
            Return True
    Return False

## stack
def dfs(maze, x, y):
    Stack = [[x, y]]
    Maze[x][y] = -1 
    While stack:
        X, y = stack.pop()
        If x == B[0] and y == B[1]:
            Return True
        For d in directions:
            I, j = x + d[0], y + d[1]
            If isSafe(maze, I, j):
                Stack.push([I, j])
                Maze[i][j] = -1
    Return False
    
## bfs
def bfs(maze, x, y):
    Q = [[x, y]]
    While q:
        X, y = queue.pop(0)
        For d in directions:
            I, j = x + d[0], y + d[1]
            If isSafe(maze, I, j):
                Maze[i][j] = maze[x][y] + 1
                Queue.append([I, j])
            If I == B[0] and j == B[1]:
                Return 
```


## Prune
### Practice Problems
* 36 Valid Sudoku
* 37 Sudoku Solver
* 51 N-Queens
* 52 N-Queens II


## Trie
### Implementation
```python
class TrieNode:
    def __init__(self):
	self.children = [None] * ALPHABET_SIZE
	# isEndOfWrod is True if node represent the end of the word
	self.isEndOfWord = False
```

### Practice Problems
* 208 Implement Trie (Prefix Tree)
* 212 Word Search II


## Bit Manipulation
### XOR
### Common Tricks
```python
x & 1 == 1 # same as x % 2 == 1
x & (x - 1) # remove last 1
x & -x # obtain last 1
```
### Practice Problems
* 52 N-Queens II
* 191 Number of 1 Bits
* 231 Power of Two
* 338 Counting Bits


## Search 
### Binary Search
```python
def binary_search(nums, target):
    left, right = 0, len(nums) - 1
    while left < right:
        mid = (left + right) // 2
        if nums[mid] < target:
            left = mid + 1
        elif nums[mid] > target:
            right = mid - 1
        else:
	    return mid
    return
```

### Practice Problems
* 4. Median of Two Sorted Arrays
* 33 Search in Rotated Sorted Array
* 34 Find First and Last Position of Element in Sorted Array
* 69 Sqrt(x)
* 74 Search a 2D Matrix
* 215 Kth Largest Element in an Array
* 268 Missing Number
* 287 Find the Duplicate Number
* Find Min and Max Simultaneously
```python
def min_max(nums):
    min_nums, max_nums = [], []
    i, j = 0, len(nums) - 1
    while i <= j:
        if i == j:
            min_nums.append(nums[i])
            max_nums.append(nums[j])            
        if nums[i] < nums[j]:
            min_nums.append(nums[i])
            max_nums.append(nums[j])
        else:
            min_nums.append(nums[j])
            max_nums.append(nums[i])            
        i += 1
        j -= 1
    return min(min_nums), max(max_nums)
```


## Sort
### Count Sort
```python
def count_sort(nums):
    res, count = [], defaultdict(int)
    for num in nums:
        count[num] += 1
    for num in range(min(count), max(count) + 1):
        res.extend([num] * count[num])
    return res
```

### Merge Sort
```python
def merge_sort(nums):
    if len(nums) < 2:
        return nums
    mid = len(nums) // 2
    left = merge_sort(nums[:mid]) if nums[:mid] else None
    right = merge_sort(nums[mid:]) if nums[mid:] else None
    return merge_sorted(left, right)

def merge_sorted(left, right):
    res, i, j = [], 0, 0
    while i < len(left) and j < len(right):
        if left[i] < right[j]:
            res.append(left[i])
            i += 1
        else:
            res.append(right[j])
            j += 1
    if i < len(left):
        res.extend(left[i:])
    if j < len(right):
        res.extend(right[j:])
    return res
```

### Quick Sort
```python
left, right = 0, len(nums) - 1
quick_sort_helper(nums, left, right)
    
def quick_sort_helper(nums, left, right):
    if left < right:
        split_index = partition(nums, left, right)
        quick_sort_helper(nums, left, split_index - 1)
        quick_sort_helper(nums, split_index + 1, right)
        
def partition(nums, left, right):
```

### Practice Problems
* 88 Merge Sorted Array
* 349 Intersection of Two Arrays
* Partitioning and Sorting Arrays with Many Repeated Entries
```python
```


## Recursion and Backtracking
### Recursion Template
```python
def fn:
    If input/state is invalid:
	    Return 
    If match some condition:
	    Return some value
    Result1 = fn(n1)
    Result2 = fn(n2)
    Return combine(result1, result2)
```
### Backtracking Template
```python
def fn:
	If input/state is invalid:
		Return
	If match some condition:
		Return some value
	For all possible cases:
		Solution.push(case)
		Result = fn(m)
		Solution.pop(case)
```

### Practice Problems
* 22 Generate Parentheses
* 39 Combination Sum
* 52 N-Queens II
* 46 Permutations
* 50 Pow(x, n)
* 77 Combinations
* 78 Subsets
* 91 Decode Ways
* 247 Strobogrammatic Number II
* 772 Basic Calculator III

## Dynamic Programming

### Practice Problems
* 10 Regular Expression Matching
* 53 Maximum Subarray
* 62 Unique Paths
* 70 Climbing Stairs    
* 72 Edit Distance
* 85 Maximal Rectangle
* 120 Triangle
* 121 Best Time to Buy and Sell Stock
* 123 Best Time to Buy and Sell Stock III
* 198 House Robber
* 300 Longest Increasing Subsequence
* 516 Longest Palindromic Subsequence
* 674 Longest Continuous Increasing Subsequence
* Binomial coefficients
```python
```
* The Kanpsack Problem
```python
```
* Pick Up Coins for Maximum Gain
```python
```


## Greedy Algorithms
### Practice Problems
* 11 Container With Most Water
* 55 Jump Game
* 84 Largest Rectangle in Histogram
* 134 Gas Station
* 435 Non-overlapping Intervals
* 621 Task Scheduler
* Minimum number of intervals to cover the target interval
```python
```


## Math
* 509 Fibonacci Number
* Simulate Unfair Coin of Abitrary Probability
```python
```
* Reservoir Sampling
```python
def sample_offline(nums, k):
    for i in range(k):
        r = random.randint(i, len(nums) - 1)
        nums[i], nums[r] = nums[r], nums[i]
    return nums[:k]
```
