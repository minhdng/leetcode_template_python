# Two Pointer Problems

## Sliding Window
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