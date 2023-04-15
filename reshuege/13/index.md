## Решу ЕГЭ 13-й вариант

**27**  
На вход программы поступает последовательность из n целых положительных чисел. Рассматриваются все пары элементов последовательности a<sub>i</sub> и a<sub>j</sub>, такие что i < j и a<sub>i</sub> > a<sub>j</sub> (первый элемент пары больше второго; i и j  — порядковые номера чисел в последовательности входных данных). Среди пар, удовлетворяющих этому условию, необходимо найти и напечатать пару с максимальной суммой элементов, которая делится на m  =  120. Если среди найденных пар максимальную сумму имеют несколько, то можно напечатать любую из них.

<a href="/reshuege/13/27_A.txt" download>Файл A</a>

<a href="/reshuege/13/27_B.txt" download>Файл B</a>

В первой строке входных данных задаётся количество чисел n (2 ≤ n ≤ 12 000).  
В каждой из последующих n строк записано одно целое положительное число, не превышающее 10 000.  
В качестве результата программа должна напечатать элементы искомой пары. Если таких пар несколько, можно вывести любую из них. Гарантируется, что хотя бы одна такая пара в последовательности есть.

В ответе укажите четыре числа: сначала искомую пару чисел для файла А (два числа через пробел), затем для файла B (два числа через пробел).

```python
f = open('27_B.txt')
n = int(f.readline())
remainders = []
for i in range(120):
    remainders.append([])
array = []
for i in range(n):
    array.append(int(f.readline()))
    remainders[array[i] % 120].append(i)
pair = []
for i in range(n // 2 + 1):
    for j in remainders[(120 - array[i] % 120) % 120]:
        if i < j and array[i] > array[j] and (array[i] + array[j]) > sum(pair):
            pair = [array[i], array[j]]
print(pair)
```

```python
f = open('27_B.txt')
n = int(f.readline())
remainders = [0] * 120
pair = []
for i in range(n):
    right = (int(f.readline()))
    left = remainders[(120 - right % 120) % 120]
    if left > right and left + right > sum(pair):
        pair = [left, right]
    remainders[right % 120] = max(remainders[right % 120], right)
print(pair)
```
