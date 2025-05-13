```python
n, a, b = map(int, input().split())
s = input().strip()

# 1. Подсчет скобок
opening = s.count('(')
closing = len(s) - opening
cost = 0

# 2. Корректировка количества (только замены)
if opening > n:
    cost += (opening - n) * b
elif closing > n:
    cost += (closing - n) * b

# 3. Проверка баланса
balance = 0
min_balance = 0
for c in s:
    balance += 1 if c == '(' else -1
    if balance < min_balance:
        min_balance = balance

# 4. Исправление баланса
if min_balance < 0:
    fix_needed = (-min_balance + 1) // 2
    cost += fix_needed * min(2*b, a)

print(cost)
```
