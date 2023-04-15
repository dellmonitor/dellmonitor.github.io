## Решу ЕГЭ 10-й вариант

**27**  
Дана последовательность N целых положительных чисел. Необходимо определить количество пар элементов этой последовательности, сумма которых делится на m  =  80 и при этом хотя бы один элемент из пары больше b  =  50.

<a href="/reshuege/10/27_A.txt" download>Файл A</a>

<a href="/reshuege/10/27_B.txt" download>Файл B</a>

В первой строке входных данных задаётся количество чисел N (2 ≤ N ≤ 10 000). В каждой из последующих N строк записано одно натуральное число, не превышающее 10 000.

```python
f = open('27_B.txt')
n = int(f.readline())
greaterThanB = []
remainders = [0] * 80
for i in range(n):
    num = int(f.readline())
    if num > 50:
        greaterThanB.append(num)
    remainders[num % 80] += 1
answer = 0
for i in range(len(greaterThanB)):
    answer += remainders[(80 - greaterThanB[i] % 80) % 80]
    if greaterThanB[i] % 80 == 40 or greaterThanB[i] % 80 == 0:
        answer -= 1
    remainders[greaterThanB[i] % 80] -= 1
print(answer)
```
