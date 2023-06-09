## Богданов 3 июня

**27**  
В файле задана последовательность из N натуральных чисел. Найти максимальную сумму пары чисел некратных D, между которыми ровно T чисел кратных D. 

<a href="/kompege/bogdanov/03.06/27_A.txt" download>Файл A</a>

<a href="/kompege/bogdanov/03.06/27_B.txt" download>Файл B</a>

Входные данные: В первой строке три числа N, D и T. Далее N строк по одному числу на строку.

Пример:  
11 2 3  
1  
2  
3  
2  
5  
2  
7  
2  
9  
2  
11  
Пары отвечающие условию: (1 7) (3 9) (5 11). Ответ 16

```python
f = open('27B.txt')
n, d, t = map(int, f.readline().split())
queue = [0] * (t + 1)
count = maxS = 0
for i in range(n):
    number = int(f.readline())
    if number % d != 0:
        left = queue[-1]
        maxS = max(maxS, left + number)
        queue[0] = max(queue[0], number)
    else:
        if count == t:
            count -= 1
        else:
            count += 1
        queue.insert(0, 0)
        queue.pop()
print(maxS)
```
