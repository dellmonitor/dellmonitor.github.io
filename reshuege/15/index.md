## Решу ЕГЭ 15-й вариант

**27**  
Набор данных состоит из пар натуральных чисел. Необходимо выбрать из каждой пары ровно одно число так, чтобы сумма всех выбранных чисел делилась на 3 и при этом была максимально возможной.

<a href="/reshuege/15/27_A.txt" download>Файл A</a>

<a href="/reshuege/15/27_B.txt" download>Файл B</a>

Первая строка входного файла содержит число N  — общее количество пар в наборе. Каждая из следующих N строк содержит два натуральных числа, не превышающих 10 000.

```python
f = open('27_A.txt')
n = int(f.readline())
diffMin1_1 = diffMin1_2 = diffMin2_1 = diffMin2_2 = 10001
s = 0
for i in range(n):
    a, b = map(int, f.readline().split())
    s += max(a, b)
    diff = abs(a - b)
    if diff % 3 == 1:
        if diffMin1_1 >= diff:
            diffMin1_2 = diffMin1_1
            diffMin1_1 = diff
        elif diffMin1_2 >= diff:
            diffMin1_2 = diff
    elif diff % 3 == 2:
        if diffMin2_1 >= diff:
            diffMin2_2 = diffMin2_1
            diffMin2_1 = diff
        elif diffMin2_2 >= diff:
            diffMin2_2 = diff
if s % 3 == 0:
    print(s)
elif s % 3 == 1:
    print(max(s - diffMin1_1, s - diffMin2_1 - diffMin2_2))
else:
    print(max(s - diffMin2_1, s - diffMin1_1 - diffMin1_2))
```
