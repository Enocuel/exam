# 🔍 Задание 6

В одной из игр всех сотрудников расставили в ряд, у каждого сотрудника известен рост, и у i-го работника он равен a<sub>i</sub>. В некоторые моменты игры два человека, которые стоят рядом, знакомились и выходили из ряда. После этого левая и правая половина ряда сдвигались, чтобы не было пустоты между ними. Такое общение происходило до тех пор, пока в ряду есть хотя бы два сотрудника.

Авторы игры решили, что чем больше разница между людьми, которые знакомятся, тем веселее. Поэтому они захотели найти такой способ знакомства, чтобы суммарная разница роста людей, которые знакомятся, была как можно больше.

Так как они не программисты, а всего лишь авторы игр, то не знают, как найти лучший порядок. Помогите им решить эту задачу.

## 📌 Условие задачи
**Формат входных данных:** 
- В первой строке входных данных дано число n— количество сотрудников (2 <= n <= 3*10<sup>5</sup>).
- Во второй строке дан массив целых чисел a<sub>1</sub>, a<sub>2</sub>,...,a<sub>n</sub> (1 ≤ а<sub>i</sub> ≤ 10<sup>9</sup>).

**Формат выходных данных:** 
- Выведите наибольшую суммарную разницу в росте сотрудников, которые познакомятся.

**Замечание:**
В первом примере могут познакомиться сотрудники с ростом 2 и 4, затем сотрудники с ростом 1 и 3, тогда суммарная разница будет |2 - 4| + |1 - 3| = 4.

## 🧠 Пример данных:

| Ввод | Вывод |
|------|-------|
| 3 4 3 |   7    |
| ())((( |       |
