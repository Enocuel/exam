# 🔍 Решение

## 📝 Что нужно сделать в задаче?
Нам даны `n` сотрудников, стоящих в ряд, с известными ростами. В процессе игры соседние сотрудники знакомятся и выходят из ряда, после чего оставшиеся части ряда сдвигаются, чтобы заполнить пустоту. Этот процесс продолжается, пока в ряду не останется менее двух сотрудников. Цель — максимизировать сумму абсолютных разниц ростов всех пар знакомящихся сотрудников.

### 🛠 Базовое решение
**1. Инициализация**
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
```
- Создаем max-кучу, используя отрицательные значения разниц (так как Python heapq реализует min-кучу).
- Инициализируем массивы left и right, которые хранят индексы предыдущего и следующего активных соседей для каждого элемента.
- Массив active отслеживает, какие элементы еще не были удалены.

**2. Обработка пар**
```python
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
```
- Извлекаем пару с максимальной разницей.
- Если оба элемента пары активны, добавляем их разницу к общей сумме и помечаем их как неактивные.
- Обновляем соседние отношения: теперь соседями становятся элементы, которые были соседями удаленных элементов.
- Добавляем новую пару в кучу, если такие соседи существуют.

**3. Выводи результат**
```python
n = int(input())
a = list(map(int, input().split()))

print(max_total_difference(n, a))
```
- После обработки всех возможных пар возвращаем накопленную сумму разниц.

## 📜 Проверка работоспособности кода

### 1. Тестовые значения 

| Ввод | Вывод |
|------|-------|
|  4   |   4   |
| 1 2 4 3 |       |

| Ввод | Вывод |
|------|-------|
|  5   |   6   |
| 2 1 4 5 2 |       |

Все отрабатывает корректно

## 🏆 Итоговое решение
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

