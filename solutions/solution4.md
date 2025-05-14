# 🔍 Решение

## 📝 Что нужно сделать в задаче?

Найти количество подотрезков массива, в которых существуют три элемента (сохраняя порядок), образующие арифметическую прогрессию.

### 🛠 Базовое решение


```python
n = int(input())
a = list(map(int, input().split()))
total = n * (n + 1) // 2
bad = 0

for length in [1, 2, 3, 4]:
    for l in range(n - length + 1):
        r = l + length
        sub = a[l:r]
        found = False
        for i in range(len(sub)):
            for j in range(i + 1, len(sub)):
                for k in range(j + 1, len(sub)):
                    if 2 * sub[j] == sub[i] + sub[k]:
                        found = True
                        break
                if found:
                    break
            if found:
                break
        if not found:
            bad += 1

answer = total - bad
print(answer)
```
