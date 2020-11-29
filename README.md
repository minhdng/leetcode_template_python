# CATpy - Common Algorithm Templates for Python

## Authors

spicythis

## Table of Content

To be added

## Data Structure and Patterns

### Hashmap

```python
dictionary = {}
for index, element in enumerate(List):
    if element in dictionary:
        return element, index                           #
    else:
        dictionary[ process_logic(element) ] = index    #
```

Examples:
- [1] https://leetcode.com/problems/two-sum/


## Algorithms

### BFS
```python
def bfs(graph, start):
    explored = []           # track visited nodes
    queue = [start]         # track nodes to be checked
 
    while queue:
        # pop shallowest node (first node) from queue
        node = queue.pop(0)
        if node not in explored:
            # add node to list of checked nodes
            explored.append(node)
            neighbours = graph[node]
 
            # add neighbours of node to queue
            for neighbour in neighbours:
                queue.append(neighbour)
    return explored
```

### DFS
```python
def dfs(graph, start)
```

### Binary Search
*Parameters*: `condition`, `left, right` initial condition, and `return` output. 
```python
def binary_search(array) -> int:
    def condition(value) -> bool:
        pass
    left, right = 0, len(array)         #
    while left < right:
        mid = left + (right - left) // 2
        if condition(mid):              #
            right = mid
        else:
            left = mid + 1
    return left                         #
```

Examples:
- [4](H) https://leetcode.com/problems/median-of-two-sorted-arrays/


### Two Pointers
If nested loop is required, single loop may be used to reduce time complexity.

#### Slow vs Fast
```python
# slow & fast runner: slow-> fast->->
def slow_fast_runner(self, seq):
    # initialize slow runner
    slow = seq[0]   # for index: slow = 0
    # fast-runner grows each iteration generally
    for fast in range(seq):     # for index: range(len(seq))
        #slow-runner grows with some restrictions
        if self.slow_condition(slow):
            slow = slow.next    # for index: slow += 1
        # process logic before or after pointers movement
        self.process_logic(slow, fast)
```
Examples:
- [26] https://leetcode.com/problems/remove-duplicates-from-sorted-array/
- [19] https://leetcode.com/problems/remove-nth-node-from-end-of-list/

#### Old vs New
```python
# old & new state: old, new = new, cur_result
def old_new_state(self, seq):
    # initialize state
    old, new = default_val1, default_val2
    for element in seq:
        # process current element with old state
        old, new = new, self.process_logic(element, old)
```
Examples:
- [509] https://leetcode.com/problems/fibonacci-number/
- [198] https://leetcode.com/problems/house-robber/
- [21] https://leetcode.com/problems/merge-two-sorted-lists/
- [91] https://leetcode.com/problems/decode-ways/

#### Two Sequences
```python
# p1 & p2 from two sequences: p1-> p2->
def pointers_from_two_seq(self, seq1, seq2):
    # init pointers
    p1, p2 = 0, 0       # or seq1[0], seq2[0]
    # or other condition
    while p1 < len(seq1) and p2 < len(seq2):
        # p1 index moves when satisfy the condition
        if self.p1_condition(p1):
            p1 += 1         # or p1 = next(seq1)
        # p2 index move when satisfy the condition
        if self.p2_condition(p2):
            p2 += 1         # or p2 = next(seq2)
        # process logic before or after pointers movement
        self.process_logic(p1, p2)
```

Examples
- [244] https://leetcode.com/problems/shortest-word-distance-ii/

#### Left vs Right
```python
# left & right boundary: left-> <-right
def left_right_boundary(self, seq):
    left, right = 0, len(seq) - 1
    while left < right:
        # left index moves when satisfy the condition
        if self.left_condition(left):
            left += 1
        # right index move when satisfy the condition
        if self.right_condition(right):
            right -= 1
        # process logic before or after pointers movement
        self.process_logic(left, right)
```
Examples:
- Binary Search
- [167] https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/
- [18] https://leetcode.com/problems/4sum/
- [11] https://leetcode.com/problems/container-with-most-water/

#### Start vs End (Sliding Window)
```python
# start & end of sliding window: |start-> ... end->|
# short version of sliding window, focus on two pointers
def start_end_sliding_window(self, seq):
    start, end = 0, 0
    while end < len(seq):
        # end pointer grows in the outer loop
        end += 1
        
        # start pointer grows with some restrict
        while self.start_condition(start):
            # process logic before pointers movement
            self.process_logic1(start, end)
            # start grows in the inner loop
            start += 1
            
        # or process logic after pointers movement
        self.process_logic2(start, end)
```
Examples: 
- [76] https://leetcode.com/problems/minimum-window-substring/
- [3] https://leetcode.com/problems/longest-substring-without-repeating-characters/
- [904] https://leetcode.com/problems/fruit-into-baskets/
- [30] https://leetcode.com/problems/substring-with-concatenation-of-all-words/

#### Three pointers
Classic example: 
```python
# [75] https://leetcode.com/problems/sort-colors/
def sortColors(nums):
    red, white, blue = 0, 0, len(nums) - 1

    while white <= blue:
        if nums[white] == 0:
            nums[red], nums[white] = nums[white], nums[red]
            white += 1
            red += 1
        elif nums[white] == 1:
            white += 1
        else:
            nums[white], nums[blue] = nums[blue], nums[white]
            blue -= 1
```

### Dynamic Programming

#### Top Down Recursion

#### Top Down Recursion with Memoization (Backtracking)

#### Bottom Up

### Greedy Algorithm

## References
https://github.com/recnac-itna/Algorithm_Templates