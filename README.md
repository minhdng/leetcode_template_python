# Common Algorithm Templates \\ for Python

## Authors

spicythis

## Algorithms

### Binary search

*Parameters*: `condition`, `left, right` initial condition, and `return` output. 

```python
def binary_search(array) -> int:
    def condition(value) -> bool:
        pass
    left, right = 0, len(array)
    while left < right:
        mid = left + (right - left) // 2
        if condition(mid):
            right = mid
        else:
            left = mid + 1
    return left
```

### Sliding Window
