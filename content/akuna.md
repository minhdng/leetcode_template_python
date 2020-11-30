## 3-Card Poker
https://www.hackerrank.com/contests/projecteuler/challenges/euler054
## Almost Equivalent Strings
## Angry Animals
## Ancestral Names
## Array Journey
## Ascending Binary Sort
## Autoscale Policy
## Biased Die Simulator
[1223] https://leetcode.com/problems/dice-roll-simulation/
## Bucket Fill
## Can You Make a PalinDrome
```python
def canMakePaliQueries(s, queries):
    N = 26
    S = len(s) + 1
    ints = list(map(lambda c: ord(c) - ord('a'), s))

    dp = [0] * S
    for i in range(1, S):
        dp[i] = dp[i-1] ^ (1 << ints[i-1])

    ones = lambda x: bin(x).count('1')
    return [
        ones(dp[r+1] ^ dp[l]) >> 1 <= k
        for l, r, k in queries
    ]
```
## Circular Array
## Coloring a Grid
## Connecting Computers
[1319] https://leetcode.com/problems/connecting-cities-with-minimum-cost/
## Dam Design
## Detect Colinearity
https://leetcode.com/problems/max-points-on-a-line/
## Dice Game Probability
## Distinct Digit Number
Variant: https://leetcode.com/problems/numbers-with-repeated-digits/
## Factor of 3 and 5
```python
# method 1: find range for x, then iterate
import math

def getIdealNum(low: int, high: int):
    xf = int(math.log(high, 3))
    count = 0
    for x in range(0, xf + 1):
        y = 0
        while (3**x) * (5**y) <= high:
            if low <= (3**x) * (5**y):
                count += 1  
            y += 1
    return count
```
## Fast Box Delivery
## Hashed Ports
## Identical Distributions
```python
# brute force
# maximum number of tray is M = max(snacks)
# O(M^2) time, O(M) memory
# can be improved to O(M log M) time
def minAdd(n, snacks):
    dMax = max(snacks) # number of tray max
    count = [dMax] * n
    res = float('inf')
    for d in range(2, dMax + 1):
        for i, s in enumerate(snacks):
            count[i] = (d - (s % d)) % d
        res = min(sum(count), res)
    return res
```
## Initial Public Offering
Use a priority queue that first sorts on the bidding price and then uses the timestamp as a tiebreaker.
## Lake Escape
## Minimum Processing Time
## Partitioning Array
```python
def partion_array(numbers, n, k):
    return n % k == 0 and all(val <= n // k for key, val in collections.Counter(numbers).items())

```
## Power Company
```python
# Greedy algorithm
import collections

def gen(n, arr):
    total_count = 0
        
    for index, count in enumerate(sorted(collections.Counter(arr).values(), reverse=True)):
        total_count += count

        if total_count >= len(arr) // 2:
            return index + 1
        
    return 0
```
## One-to-All Time Sparse Directional Graph
(Dijkstra)?
## Oscillating String
Translate pseudocode
## Rock 'n' Ribbon
## Selling Products
## Shipping Robot
https://leetcode.com/discuss/interview-question/867865/Akuna-Capital-Quant-Dynamics-Python
## Sorted Arrangement
https://leetcode.com/discuss/interview-question/371225/Sorted-Arrangements-or-Infosys-Specialist-Programmer-or-On-campus-hackerrank

Use binary tree to find position, then loop through input array.
## Split The Array
Greedy
## String Chains
https://blog.cancobanoglu.net/2016/09/18/interview-questions-string-chain/
https://leetcode.com/problems/longest-string-chain/
## Strokes to Paint
```python
def label(board):
    if not board:
        return 0
    m = len(board)
    n = len(board[0])
    res = 0
    
    for i in range(m):
        for j in range(n):
            if board[i][j] != '0':
                bfs(board, m, n, i, j)
                res += 1
    
    return res

def bfs(board, m, n, i, j):
    queue = [[i, j]]
    color = board[i][j]
    while queue:
        c = queue.pop(0)
        board[c[0]][c[1]] = '0'
        neighbors_idx = [ [c[0] + 1, c[1]], [c[0] - 1, c[1]], [c[0], c[1] + 1], [c[0], c[1] - 1] ]
        for idx in neighbors_idx:
            if idx[0] < 0 or idx[0] >= m or idx[1] < 0 or idx[1] >= n:
                continue
            if board[idx[0]][idx[1]] == color:
                queue.append(idx)
```
## Subarray MaxMin
Related to [239] Sliding Window Maximum

https://leetcode.com/problems/sliding-window-maximum/discuss/65901/9-lines-Ruby-11-lines-Python-O(n)
```python
def minSlidingWindow(nums, k):
    res = []
    bigger = deque()
    for i, n in enumerate(nums):
        # make sure the rightmost one is the largest
        while bigger and nums[bigger[-1]] >= n:
            bigger.pop()
​
        # add in
        bigger += [i]
​
        # make sure the leftmost one is in-bound
        if i - bigger[0] >= k:
            bigger.popleft()
​
        # if i + 1 < k, then we are initializing the bigger array
        if i + 1 >= k:
            res.append(nums[bigger[0]])
    return max(res)
```
## Task Queue
## Throtting Gateway
https://leetcode.com/discuss/interview-question/700965/throttling-gateway
```python
def droppedRequest(requestTime):

    dropped = 0
	# this is to keep track of any of the element that is already dropped due to any of 3 limit violation.
    already_dropped = {} 

    for i in range(len(requestTime)):
        if i > 2 and requestTime[i] == requestTime[i-3]:
            if requestTime[i] not in already_dropped or already_dropped[requestTime[i]] != i:
                already_dropped[requestTime[i]] = i
                dropped += 1
                print(i, requestTime[i])

        elif i > 19 and requestTime[i] - requestTime[i-20] < 10:
            if requestTime[i] not in already_dropped or already_dropped[requestTime[i]] != i:
                already_dropped[requestTime[i]] = i
                dropped += 1
                print(i, requestTime[i])

        elif i > 59 and requestTime[i] - requestTime[i-60] < 60:
            if requestTime[i] not in already_dropped or already_dropped[requestTime[i]] != i:
                already_dropped[requestTime[i]] = i
                dropped += 1
                print(i, requestTime[i])

    return dropped
```
## Turnstile
## Unusual Sort








