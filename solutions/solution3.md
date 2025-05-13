```python
n = int(input())
arr = list(map(int, input().split()))
arr.sort(reverse=True)

used = set()
res = 0

for num in arr:
    current = num
    while current > 0 and current in used:
        current = current // 2
    if current not in used:
        used.add(current)
        res += 1

print(res)
```
