```python
n = int(input())
branches = []
for j in range(n):
    a, b = map(int, input().split())
    branches.append((a, b))

q = int(input())
for j in range(q):
    t, d = map(int, input().split())
    a, b = branches[t - 1]
    if d <= a:
        print(a)
    else:
        k = (d - a + b - 1) // b
        print(a + k * b)
```
