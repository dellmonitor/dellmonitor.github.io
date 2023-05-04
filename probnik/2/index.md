## Пробник 3 мая 2-й вариант

**27**  
Дана последовательность N целых положительных чисел, не превышающих 100. Необходимо определить количество уникальных четверок элементов, два элемента в которых четные и два нечетные. Например, четверки (13 10 43 32) и (10 13 32 43) в рамках задачи считаются одной четверкой.

<a href="/probnik/2/27_A.txt" download>Файл A</a>

<a href="/probnik/2/27_B.txt" download>Файл B</a>

В первой строке записано натуральное число N (1 < N < 10 000) — количество чисел в последовательности. В следующих N строках записаны числа, входящие в последовательность, по одному в каждой строке.

Пример входных данных:  
6  
10  
11  
10  
12  
13  
10

Ответ в данном случае — 2

```python
def fact(n):
    if n == 0 or n == 1:
        return 1
    return fact(n - 1) * n
def combinations(n, a):
    return fact(n) / (fact(a) * fact(n - a))

f = open('27_B.txt')
n = int(f.readline())
uniqueOdd = uniqueEven = 0
duplicateOdd = duplicateEven = 0
table = [0] * 100
for i in range(n):
    number = int(f.readline())
    if not table[number - 1]:
        table[number - 1] = 1
        if number % 2 == 1:
            uniqueOdd += 1
        else:
            uniqueEven += 1
    elif table[number - 1] == 1:
        table[number - 1] += 1
        if number % 2 == 1:
            duplicateOdd += 1
        else:
            duplicateEven += 1

print((combinations(uniqueEven, 2) + duplicateEven) * (combinations(uniqueOdd, 2) + duplicateOdd))
```
