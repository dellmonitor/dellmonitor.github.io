## Решу ЕГЭ 7-й вариант

**27**  
В текстовом файле записан набор пар натуральных чисел, не превышающих 10 000. Необходимо выбрать из набора некоторые пары так, чтобы второе число в каждой выбранной паре было нечётным, сумма бо́льших чисел во всех выбранных парах была чётной, а сумма меньших  — нечётной. Какую наибольшую сумму чисел во всех выбранных парах можно при этом получить?

<a href="/reshuege/7/27_A.txt" download>Файл A</a>

<a href="/reshuege/7/27_B.txt" download>Файл B</a>

Первая строка входного файла содержит целое число N  — общее количество пар в наборе. Каждая из следующих N строк содержит пару чисел.

```python
def even(n):
    return not n % 2
def odd(n):
    return n % 2

f = open('27_B.txt')
n = int(f.readline())
oddGreat = oddSmall = oddGreatSmall = 20001
sumGreat = sumSmall = 0
for i in range(n):
    a, b = map(int, f.readline().split())
    if odd(b):
        maxAB = max(a, b)
        minAB = min(a, b)
        sumGreat += maxAB
        sumSmall += minAB
        if odd(maxAB) and even(minAB):
            oddGreat = min(oddGreat, a + b)
        elif even(maxAB) and odd(minAB):
            oddSmall = min(oddSmall, a + b)
        elif odd(maxAB) and odd(minAB):
            oddGreatSmall = min(oddGreatSmall, a + b)
s = sumGreat + sumSmall
if even(sumGreat) and odd(sumSmall):
    print(s)
elif even(sumGreat) and even(sumSmall):
    print(s - oddSmall)
elif odd(sumGreat) and odd(sumSmall):
    print(s - oddGreat)
else:
    print(max(s - oddGreatSmall, s - oddGreat - oddSmall))
```
