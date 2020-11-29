# CATpy - Common Algorithm Templates for Python

## Authors

spicythis

## Table of Content

To be added

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

### Sliding Window

If nested loop is required, single loop may be used to reduce time complexity.
 two 


### Two Pointers

https://www.pluralsight.com/guides/algorithm-templates:-two-pointers-part-1
https://www.pluralsight.com/guides/algorithm-templates:-two-pointers-part-2
https://www.pluralsight.com/guides/algorithm-templates:-two-pointers-part-3

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



#### Start vs End of Sliding Window
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

More detailed version:
```python
# more specific version of sliding window
# s - source sequence, p - pattern or restrict sequence
def sliding_window_template_with_examples(s, p):
    # initialize the hash map
    # counter is used to record current state, usually use Counter or defaultdict
    counter = Counter(p) 
    # two pointers, boundary of sliding window
    start, end = 0, 0
    # condition checker, update it when trigger some key changes
    # the initial value depend on your situation
    count = 0
    # result, return int (such as max or min) or list (such as all index)
    res = 0

    # loop the source sequence from begin to end
    while end < len(s):
        counter[s[end]] += 1
        # update count based on some condition
        if counter[s[end]] > 1:
            count += 1
        # end pointer grows in the outer loop    
        end += 1

        # count condition, the condition may be different
        while count > 0:
            '''
            update res here if finding minimum
            '''
            # increase start pointer to make it invalid or valid again
            counter[s[start]] -= 1
            # update count based on some condition
            if counter[s[start]] > 0:
                count -= 1
            # start pointer grows in the inner loop
            start += 1
        '''
        update res here if finding maximum
        '''
        # the result logic may be different
        res = max(res, end - start)
    return res
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

### Top Down Recursive

### Back Tracking

### Dynamic Programming



### System Design

https://github.com/donnemartin/system-design-primer

```
(1) FEATURE EXPECTATIONS [5 min]
        (1) Use cases
        (2) Scenarios that will not be covered
        (3) Who will use
        (4) How many will use
        (5) Usage patterns
(2) ESTIMATIONS [5 min]
        (1) Throughput (QPS for read and write queries)
        (2) Latency expected from the system (for read and write queries)
        (3) Read/Write ratio
        (4) Traffic estimates
                - Write (QPS, Volume of data)
                - Read  (QPS, Volume of data)
        (5) Storage estimates
        (6) Memory estimates
                - If we are using a cache, what is the kind of data we want to store in cache
                - How much RAM and how many machines do we need for us to achieve this ?
                - Amount of data you want to store in disk/ssd
(3) DESIGN GOALS [5 min]
        (1) Latency and Throughput requirements
        (2) Consistency vs Availability  [Weak/strong/eventual => consistency | Failover/replication => availability]
(4) HIGH LEVEL DESIGN [5-10 min]
        (1) APIs for Read/Write scenarios for crucial components
        (2) Database schema
        (3) Basic algorithm
        (4) High level design for Read/Write scenario
(5) DEEP DIVE [15-20 min]
        (1) Scaling the algorithm
        (2) Scaling individual components: 
                -> Availability, Consistency and Scale story for each component
                -> Consistency and availability patterns
        (3) Think about the following components, how they would fit in and how it would help
                a) DNS
                b) CDN [Push vs Pull]
                c) Load Balancers [Active-Passive, Active-Active, Layer 4, Layer 7]
                d) Reverse Proxy
                e) Application layer scaling [Microservices, Service Discovery]
                f) DB [RDBMS, NoSQL]
                        > RDBMS 
                            >> Master-slave, Master-master, Federation, Sharding, Denormalization, SQL Tuning
                        > NoSQL
                            >> Key-Value, Wide-Column, Graph, Document
                                Fast-lookups:
                                -------------
                                    >>> RAM  [Bounded size] => Redis, Memcached
                                    >>> AP [Unbounded size] => Cassandra, RIAK, Voldemort
                                    >>> CP [Unbounded size] => HBase, MongoDB, Couchbase, DynamoDB
                g) Caches
                        > Client caching, CDN caching, Webserver caching, Database caching, Application caching, Cache @Query level, Cache @Object level
                        > Eviction policies:
                                >> Cache aside
                                >> Write through
                                >> Write behind
                                >> Refresh ahead
                h) Asynchronism
                        > Message queues
                        > Task queues
                        > Back pressure
                i) Communication
                        > TCP
                        > UDP
                        > REST
                        > RPC
```