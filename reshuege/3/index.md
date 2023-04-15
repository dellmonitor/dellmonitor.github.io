## Решу ЕГЭ 3-й вариант

**17**  
В файле содержится последовательность из 10 000 целых положительных чисел. Каждое число не превышает 10 000. Определите и запишите в ответе сначала количество пар элементов последовательности, у которых сумма нечётна, а произведение делится на 5, затем максимальную из сумм элементов таких пар. В данной задаче под парой подразумевается два различных элемента последовательности. Порядок элементов в паре не важен.

<a href="/reshuege/3/17.txt" download>17.txt</a>

```python
f = open('17.txt')
a = [int(x) for x in f]
five = [x for x in a if x%10==5]
ten = [x for x in a if x%10==0]
odd = [x for x in a if x%2!=0]
even = [x for x in a if x%2==0]
num = len(five)*len(even) + len(ten)*len(odd) - len(ten)*len(five)
mf = max(five) + max(even)
mt = max(ten) + max(odd)

print(num, max(mf,mt))
```

<br>

**27**  
На вход программы поступает последовательность из N натуральных чисел. Рассматриваются все пары различных элементов последовательности, у которых различные остатки от деления на d  =  160 и хотя бы одно из чисел делится на p  =  7. Среди таких пар, необходимо найти и вывести пару с максимальной суммой элементов.

<a href="/reshuege/3/27_A.txt" download>Файл A</a> 

<a href="/reshuege/3/27_B.txt" download>Файл B</a>

В первой строке входных данных задаётся количество чисел N (1 ≤ N ≤ 1000). В каждой из последующих N строк записано одно натуральное число, не превышающее 10 000. В качестве результата программа должна напечатать элементы искомой пары. Если среди найденных пар максимальную сумму имеют несколько, то можно напечатать любую из них. Если таких пар нет, то вывести два нуля.

```python
f = open('27_B.txt')
a = [int(x) for x in f]
del a[0]
seven = [x for x in a if x % 7 == 0]
notseven = [x for x in a if x % 7 != 0]
maxsum = 0
answer = "0 0"
for i in range(0, len(seven)):
    for j in range(0, len(notseven)):
        if seven[i] % 160 != notseven[j] % 160:
            if maxsum < seven[i] + notseven[j]:
                maxsum = seven[i] + notseven[j]
                answer = str(seven[i]) + ' ' + str(notseven[j])
    for k in range(i+1, len(seven)):
        if seven[i] % 160 != seven[k] % 160:
            if maxsum < seven[i] + seven[k]:
                maxsum = seven[i] + seven[k]
                answer = str(seven[i]) + ' ' + str(seven[k])
print(answer)
```
