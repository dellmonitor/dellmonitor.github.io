## Решу ЕГЭ 6-й вариант

**27**  
Набор данных состоит из нечётного количества пар натуральных чисел. Необходимо выбрать из каждой пары ровно одно число так, чтобы чётность суммы выбранных чисел совпадала с чётностью большинства выбранных чисел и при этом сумма выбранных чисел была как можно больше. Определите максимальную сумму, которую можно получить при таком выборе. Гарантируется, что удовлетворяющий условиям выбор возможен.

<a href="/reshuege/6/27_A.txt" download>Файл A</a>

<a href="/reshuege/6/27_B.txt" download>Файл B</a>

Первая строка входного файла содержит число N  — общее количество пар в наборе. Каждая из следующих N строк содержит два натуральных числа, не превышающих 10 000.

```python
def even(n):
    return not n % 2
def odd(n):
    return n % 2

f = open('27_B.txt')
n = int(f.readline())
countOdd = countEven = 0
removeOdd1 = removeEven1 = removeOdd2 = removeEven2 = 10001
s = 0
for i in range(n):
    a, b = map(int, f.readline().split())
    maxAB, minAB = max(a, b), min(a, b)
    if odd(maxAB):
        countOdd += 1
    else:
        countEven += 1
    s += maxAB
    diff = abs(a - b)
    if odd(maxAB) and even(minAB):
        if diff <= removeOdd1:
            removeOdd2 = removeOdd1
            removeOdd1 = diff
        elif diff <= removeOdd2:
            removeOdd2 = diff
    elif even(maxAB) and odd(minAB):
        if diff <= removeEven1:
            removeEven2 = removeEven1
            removeEven1 = diff
        elif diff <= removeEven2:
            removeEven2 = diff
if countOdd > countEven:
    if even(s):
        if countOdd - countEven == 1:
            s = max(s - removeOdd1 - removeOdd2, s - removeEven1)
        else:
            s = s - removeEven1
else:
    if odd(s):
        if countEven - countOdd == 1:
            s = max(s - removeEven1 - removeEven2, s - removeOdd1)
        else:
            s = s - removeOdd1
print(s)
```
