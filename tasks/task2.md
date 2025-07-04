# 🔍 Задание 2

Егор с друзьями гуляли по городу N и нашли карту метро. В этом городе целых n веток метро, у каждой ветки свое расписание. Изучив расписание, они обнаружили, что по ветке i поезд начинает ходить в a<sub>i</sub> секунду с начала дня, и каждый новый поезд начинает маршрут после предыдущего спустя b<sub>i</sub> секунд. Теперь им захотелось научиться в некоторые моменты времени для ветки и времени определять, когда они увидят поезд после прихода на станцию.

## 📌 Условие задачи
**Формат входных данных:** 
- В единственной строке входных данных дается строка из четырех латинских символов.
- В следующих n строках даны числа a<sub>i</sub>, b<sub>i</sub> — первый момент, когда поезд с i-й ветки приезжает на станцию, и промежуток между поездами (0 ≤ a<sub>i</sub> < b<sub>i</sub> ≤ 10<sup>9</sup>).
- В следующей строке дано число q — количество запросов (1 ≤ q ≤ 100).
- В следующих q строках даны числа t<sub>i</sub>, d<sub>i</sub> — номер ветки и момент времени, когда друзья придут на станцию (1 ≤ t<sub>i</sub> ≤ n, 1 ≤ d<sub>i</sub> ≤ 10<sup>9</sup>)

**Формат выходных данных:** 
- Для каждого запроса выведите в отдельной строке ответ на задачу.

## 🧠 Примеры данных:

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
