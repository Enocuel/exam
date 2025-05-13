```python
s = input().strip()
found = False

for i in range(4):
    # Создаем подстроку без i-го символа
    sub = s[:i] + s[i+1:]
    if sub == sub[::-1]:
        found = True
        break

print("YES" if found else "NO")
```

```python
s = input().strip()

if len(s) != 4:
    print("NO")
else:
    found = False
    for i in range(4):
        # Создаем подстроку без i-го символа
        sub = s[:i] + s[i+1:]
        if sub[0] == sub[2]:  # Проверяем первый и последний символы
            found = True
            break
    print("YES" if found else "NO")
```

```python
s = input().strip()

if len(s) != 4:
    print("NO")
else:
    # Проверяем, является ли строка палиндромом (тогда ответ "YES")
    if s == s[::-1]:
        print("YES")
    else:
        # Проверяем все возможные подстроки после удаления одного символа
        for i in range(4):
            sub = s[:i] + s[i+1:]
            if sub[0] == sub[2]:
                print("YES")
                break
        else:
            print("NO")
```
