## Решу ЕГЭ 11-й вариант

**27**  
Дана последовательность натуральных чисел. Необходимо найти максимально возможную сумму её непрерывной подпоследовательности, в которой количество нечётных элементов кратно k  =  10.

<a href="/reshuege/11/27_A.txt" download>Файл A</a>

<a href="/reshuege/11/27_B.txt" download>Файл B</a>

Первая строка входного файла содержит целое число N  — общее количество чисел в наборе. Каждая из следующих N строк содержит одно число. Гарантируется, что общая сумма всех чисел не превышает 2 · 10<sup>9</sup>.

```python
f = open('27_B.txt')
n = int(f.readline())
prefixsum = [0] * (n + 1)
odd = []
for i in range(n):
    num = int(f.readline())
    prefixsum[i + 1] = prefixsum[i] + num
    if num & 1:
        odd.append(i)
maxLen = len(odd) // 10 * 10
if len(odd) % 10:
    maxSum = prefixsum[odd[maxLen]]
else:
    maxSum = prefixsum[-1]
for i in range(len(odd) - maxLen + 1):
    maxSum = max(maxSum, prefixsum[odd[maxLen + i - 1]] - prefixsum[odd[i]])
print(maxSum)
```
