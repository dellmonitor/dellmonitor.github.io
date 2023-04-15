## Решу ЕГЭ 8-й вариант

**27**  
В текстовом файле записан набор натуральных чисел, не превышающих 10<sup>8</sup>. Гарантируется, что все числа различны. Из набора нужно выбрать три числа, сумма которых делится на 3. Какую наибольшую сумму можно при этом получить?

<a href="/reshuege/8/27_A.txt" download>Файл A</a>

<a href="/reshuege/8/27_B.txt" download>Файл B</a>

Первая строка входного файла содержит целое число N  — общее количество чисел в наборе. Каждая из следующих N строк содержит одно число.

```python
f = open('27_B.txt')
a = [int(x) for x in f]
del a[0]

zero = [x for x in a if x%3==0]
one = [x for x in a if x%3==1]
two = [x for x in a if x%3==2]

zero.sort()
one.sort()
two.sort()

case1 = sum(zero[-1:-4:-1])
case2 = sum(one[-1:-4:-1])
case3 = sum(two[-1:-4:-1])
case4 = zero[-1] + one[-1] + two[-1]
print(max(case1, case2, case3, case4))
```
