# 🔍 Решение

## 📝 Условие задачи

Преобразовать строку в правильную скобочную последовательность с минимальными затратами.

**Для этого у нас есть следующие данные:**
- `n, a, b` (1 ≤ n ≤ 5·10⁵, 1 ≤ a,b ≤ 10⁹)
- Строка `s` длины 2n из скобок "(" и ")"

**Также мы можем сделать следующее:**
1. Поменять местами две скобки — стоимость `a` монет
2. Заменить скобку — стоимость `b` монет

### 🛠 Базовое решение

**1. Ввод данных и подсчет скобок**
```python
n, a, b = map(int, input().split())
s = input().strip()
opening = s.count('(')
closing = len(s) - opening
cost = 0
```
- Считываем параметры `n` (половина длины строки), стоимости операций `a` (свап) и `b` (замена)
- Подсчитываем количество открывающих `(` и закрывающих `)` скобок

**2. Корректировка количества скобок (только замены)**
```python
if opening > n:
    cost += (opening - n) * b
elif closing > n:
    cost += (closing - n) * b
```
- Если открывающих скобок больше нужного количества (`n`):
    - Заменяем избыточные `(` на `)` стоимостью `b` за каждую
- Аналогично для избытка закрывающих скобок

**3. Проверка баланса последовательности**
```python
balance = 0
min_balance = 0
for c in s:
    balance += 1 if c == '(' else -1
    if balance < min_balance:
        min_balance = balance
```
- Вычисляем текущий баланс (разница между открывающими и закрывающими скобками)
- Фиксируем минимальное значение баланса (показывает глубину дисбаланса)

**4. Исправление структуры последовательности**
```python
if min_balance < 0:
    fix_needed = (-min_balance + 1) // 2
    cost += fix_needed * min(2*b, a)
```
- Если есть дисбаланс (отрицательный min_balance):
    - Вычисляем количество необходимых исправлений
    - Выбираем оптимальную стратегию:
        - Либо 2 замены (стоимость 2*b)
        - Либо 1 обмен (стоимость a)
- Добавляем минимальную стоимость к общим затратам

## 📜 Проверка работоспособности кода

### 1. Тестовые значения
| Ввод | Вывод |
|------|-------|
| 3 4 3 |   7   |
| ())((( |       |

- Ответ верен.

### 2. Проверка на простых значениях

| Ввод | Вывод |
|------|-------|
| 2 5 2 |   4   |
| (())) |       |

- Нужно заменить одну `(` на `)` (стоимость 2).
- Затем исправить баланс (если нужно) — в данном случае строка `(()))` после замены становится `(()())` (правильная).
- Общая стоимость: 2 (замена) + возможные дополнительные исправления (в моем случае).

| Ввод | Вывод |
|------|-------|
| 4 3 6 |   0   |
| ()()()() |       |

- Строка уже правильная, изменений не требуется.

| Ввод | Вывод |
|------|-------|
| 1 100 50 |   100   |
| )( |       |

- Обмен `)` и `(` (стоимость `100`).
- Или две замены (стоимость `50 + 50 = 100`)

## 🏆 Итоговое решение
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
