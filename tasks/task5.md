# 🔍 Задание 5

В ВУЗе Никите задали домашнее задание по программированию, которое он никак не мог решить, поэтому он попросил вас решить следующую задачу.

Дана строка s длины 2n, состоящая из"(" и ")". Со строкой можно проделывать две операции:
- Выбрать пару (i, j) такую, что 1 ≤ i < j ≤ 2n и поменять символы s<sub>i</sub> и s<sub>j</sub> местами за a монет.
- Заменить произвольный символ строки на "(" или ")" за b монет.

Требуется сделать строку s правильной скобочной последовательностью за минимальное количество монет.

Строка является правильной скобочной последовательностью, если выполнено одно из трех условий:
- Строка пустая.
- Строку можно представить в виде (S), где S — правильная скобочная последовательность.
- Строку можно представить в виде S<sub>1</sub>, S<sub>2</sub>, где S<sub>1</sub>, S<sub>2</sub> — правильные скобочные последовательности.

## 📌 Условие задачи
**Формат входных данных:** 
- В первой строке входных данных дано три числа n, a, b (1 ≤ n ≤ 5*10<sup>5</sup>, 1 ≤ a,b ≤ 10<sup>9</sup>).
- Во второй строке дана строка s длины 2n, состоящая из символов "(" и ")".

**Формат выходных данных:** 
- В первой строке входных данных дано три числа n, a, b (1 ≤ n ≤ 5*10<sup>5</sup>, 1 ≤ a,b ≤ 10<sup>9</sup>).
- Во второй строке дана строка s длины 2n, состоящая из символов "(" и ")".

**Замечание:**
В примере можно поменять 3-ий и 4-ый символы местами за 4 монеты и 6-ой символ на ")" за 3 монеты.

## 🧠 Пример данных:

| Ввод | Вывод |
|------|-------|
| 3 4 3 |   7    |
| ())((( |       |
