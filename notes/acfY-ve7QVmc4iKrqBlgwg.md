






3. Birthday card collection
```
def hackerCards(collection, d):
    result = []
    for i in range(int(1e9)):
        cost = i + 1
        if cost not in collection:
            result.append(cost)
            if sum(result) > d:
                result.pop()
                break
        else:
            collection.remove(cost)
    return result
```


1.
```
def minSum(num, k):
    for _ in range(k):
        m = max(num)
        num.append(math.ceil(m / 2))
        num.remove(m)
    return sum(num)
```
or

```

def minSum(num,k):
    sorted_num = sorted(num, reverse=True)
    for _ in range(k):
        sorted_num[0] = math.ceil(sorted_num[0] / 2)
        if sorted_num[0] < sorted_num[1]:
            sorted_num = sorted(sorted_num, reverse=True)
    return sum(sorted_num)
```


stackoverflow ans:

```
def minSum(num, k):
    heap = num   # alias for consistency with other samples
    heapq._heapify_max(heap)

    for i in range(k):
        max_value = heap[0]
        if max_value == 1:  # exit early if there is no more work
            break
        new_val = (max_value >> 1) + (max_value & 1)  # same as, but much faster than math.ceil(max_value/2)
        heapreplace_max(heap, new_val)

    return sum(heap)
```