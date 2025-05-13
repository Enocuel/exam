```python
import heapq


def max_total_difference(n, a):
    if n == 2:
        return abs(a[0] - a[1])

    # Максимизируем разницу, поэтому используем max-heap. В Python heapq только min-heap, поэтому инвертируем значения.
    heap = []
    left = [i - 1 for i in range(n)]
    right = [i + 1 for i in range(n)]
    active = [True] * n

    # Инициализация кучи: все соседние пары
    for i in range(n - 1):
        diff = abs(a[i] - a[i + 1])
        heapq.heappush(heap, (-diff, i, i + 1))  # храним отрицание для max-heap

    total = 0

    while heap:
        neg_diff, u, v = heapq.heappop(heap)
        diff = -neg_diff

        if not active[u] or not active[v]:
            continue

        # Добавляем разницу к общей сумме
        total += diff

        # Помечаем узлы как неактивные
        active[u] = False
        active[v] = False

        # Обновляем соседей
        left_u = left[u]
        right_v = right[v]

        if left_u != -1:
            right[left_u] = right_v
        if right_v != n:
            left[right_v] = left_u

        # Если есть новые соседи, добавляем их в кучу
        if left_u != -1 and right_v != n:
            new_diff = abs(a[left_u] - a[right_v])
            heapq.heappush(heap, (-new_diff, left_u, right_v))

    return total


# Чтение входных данных
n = int(input())
a = list(map(int, input().split()))

print(max_total_difference(n, a))
```

```python
import heapq

def max_total_difference(n, a):
    if n == 2:
        return abs(a[0] - a[1])
    
    heap = []
    left = [i - 1 for i in range(n)]
    right = [i + 1 for i in range(n)]
    active = [True] * n
    
    for i in range(n - 1):
        diff = abs(a[i] - a[i + 1])
        heapq.heappush(heap, (-diff, i, i + 1))
    
    total = 0
    
    while heap:
        neg_diff, u, v = heapq.heappop(heap)
        if not active[u] or not active[v]:
            continue
        
        total += -neg_diff
        active[u] = active[v] = False
        
        left_u, right_v = left[u], right[v]
        if left_u != -1:
            right[left_u] = right_v
        if right_v != n:
            left[right_v] = left_u
        
        if left_u != -1 and right_v != n:
            new_diff = abs(a[left_u] - a[right_v])
            heapq.heappush(heap, (-new_diff, left_u, right_v))
    
    return total

n = int(input())
a = list(map(int, input().split()))
print(max_total_difference(n, a))
```
