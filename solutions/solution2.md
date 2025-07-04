# 🔍 Решение

## 📝 Что нужно сделать в задаче?

- В первой строке число `n` — количество веток метро.
- Далее `n` строк с парами `a_i, b_i` (время первого поезда и интервал).
- Затем число `q` — количество запросов.
- Далее `q` строк с парами `t_i, d_i` (номер ветки и время прихода).
- Для каждого запроса вывести время следующего поезда.

### 🛠 Базовое решение

**1. Ввод данных о ветках метро**
```python
n = int(input())
branches = []
for j in range(n):
    a, b = map(int, input().split())
    branches.append((a, b))
```
Сначала считывается количество веток метро `n`.

Затем для каждой ветки вводятся два числа:
- `a` — время прибытия первого поезда.
- `b` — интервал между поездами.

Эти данные сохраняются в списке `branches` в виде кортежей `(a, b)`.

**2. Обработка запросов**
```python
n = int(input())
branches = []
for j in range(n):
    a, b = map(int, input().split())
    branches.append((a, b))
```
Считывается количество запросов `q`.

Для каждого запроса вводятся:
- `t` — номер ветки метро (нумерация с 1).
- `d` — время, когда человек пришёл на станцию.

Из списка `branches` извлекаются параметры ветки `(a, b)`.

**3. Вычисление времени следующего поезда**
```python
    if d <= a:
        print(a)
    else:
        k = (d - a + b - 1) // b
        print(a + k * b)
```
Если человек пришёл до первого поезда `(d <= a)`:
- Ответ — время первого поезда `a`.

Если человек пришёл после первого поезда (`d > a`):
- Вычисляется, сколько интервалов b прошло с момента a до d:
    - `k = (d - a + b - 1) // b` — это эквивалент округления вверх.
    - Время следующего поезда: `a + k * b`.

### 🏆 Итоговое решение
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

## 📜 Проверка работоспособности кода
Так как в этой задаче диапазон значений значительно больше, чем в предыдущих (до 10⁹), нам нужно тщательно проверить корректность работы кода.

### **1. Проверим на тестовых значениях из условия**
| Ввод | Вывод |
|------|-------|
| 3    |       |
| 0 1  |       |
| 2 3  |       |
| 1 4  |       |
| 5    |       |
| 1 2  | 2     |
| 2 6  | 8     |
| 3 6  | 9     |
| 2 5  | 5     |
| 3 8  | 9     |

**Результат:** Код выдаёт правильные ответы. Значит можно двигаться дальше.

### **2. Проверим простые случаи (возможно проверить ручным расчётом)**

| Ввод | Вывод |
|------|-------|
| 1    |       |
| 0 1  |       |
| 1    |       |
| 1 0  | 0     |

| Ввод | Вывод |
|------|-------|
| 1    |       |
| 5 5  |       |
| 1    |       |
| 1 5  | 5     |

**Результат:** Код правильно работает на простых примерах минимального значения и когда поезд приходит ровно в момент прихода.

### **3. Проверим более сложные случаи**

| Ввод | Вывод |
|------|-------|
| 2    |       |
| 1000000000 1000000000  |       |
| 999999999 1  |       |
| 3  |       |
| 2 2000000000  | 2000000000     |
| 2 1000000000  | 1000000000     |
| 2 999999998  | 999999999     |

| Ввод | Вывод |
|------|-------|
| 1    |       |
| 10 3 |       |
| 1 9  |  10     |
| 1 10  | 10     |
| 1 11  | 13     |
| 1 13  | 13     |

| Ввод | Вывод |
|------|-------|
| 3    |       |
| 0 5 |       |
| 1 2 |       |
| 4 10 |       |
| 5   |       |
| 1 3 |    5   |
| 2 3 |   3    |
| 3 3 |   4    |
| 1 6 |   10    |
| 3 15 |   24    |

**Результат:** Код корректно обрабатывает большие числа и граничные случаи.

## 🔥 Доработки после окончания экзамена
```python
print("Введите количество веток метро (n):")
n = int(input())
branches = []

print(f"Введите параметры для каждой из {n} веток (a b через пробел):")
for i in range(n):
    while True:
        print(f"Ветка {i+1}:", end=" ")
        try:
            a, b = map(int, input().split())
            branches.append((a, b))
            break
        except ValueError:
            print("Ошибка! Нужно ввести два числа через пробел. Попробуйте еще раз.")

print("\nВведите количество запросов (q):")
q = int(input())

print(f"\nВведите {q} запросов (номер ветки и время через пробел):")
for i in range(q):
    while True:
        print(f"Запрос {i+1}:", end=" ")
        try:
            ti, di = map(int, input().split())
            a, b = branches[ti - 1]
            
            if di <= a:
                print(f"Ответ: {a}")
            else:
                k = (di - a + b - 1) // b
                next_train = a + k * b
                print(f"Ответ: {next_train}")
            break
        except ValueError:
            print("Ошибка! Нужно ввести два числа через пробел. Попробуйте еще раз.")
        except IndexError:
            print(f"Ошибка! Ветки с номером {ti} не существует. Доступные ветки: 1-{len(branches)}. Попробуйте еще раз.")
```

⚠️ Не всегда выдает правильный ответ, попробывать раскопать бы из-за чего. С новым строением что-то пошло не так.
