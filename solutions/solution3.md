# 🔍 Решение

## 📝 Что нужно сделать в задаче?
- Определить максимальное количество различных чисел, которое можно получить, деля элементы массива на 2 (с округлением вниз) любое количество раз.

### 🛠 Базовое решение

**1. Ввод и подготовка данных**
```python
n = int(input())
arr = list(map(int, input().split()))
arr.sort(reverse=True)
```
- Считываем длину массива `n`
- Получаем сам массив чисел
- Сортируем массив по убыванию

**2. Инициализация структур данных**
```python
used = set()
res = 0
```
- `used` - множество для хранения уникальных значений
- `res` - счетчик уникальных элементов

**3. Обработка каждого элемента**
```python
for num in arr:
    current = num
    while current > 0 and current in used:
        current = current // 2
    if current not in used:
        used.add(current)
        res += 1
print(res)
```
Для каждого числа в отсортированном массиве:
1. Начинаем с исходного значения
2. Пока число > 0 и уже есть в множестве:
    - Делим число на 2 (целочисленно)
3. Если получили уникальное значение:
    - Добавляем в множество
    - Увеличиваем счетчик
4. Выводим результат

### 🏆 Итоговое решение
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
