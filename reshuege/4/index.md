## Решу ЕГЭ 4-й вариант

27.   На вход программы поступает последовательность из целых положительных чисел. Необходимо выбрать такую подпоследовательность подряд идущих чисел, чтобы их сумма была максимальной и делилась на 89, а также её длину. Если таких подпоследовательностей несколько, выбрать такую, у которой длина меньше.

      <a href="/reshuege/4/27_A.txt" download>Файл A</a>

      <a href="/reshuege/4/27_B.txt" download>Файл B</a>

      Даны два входных файла (файл A и файл B), каждый из которых содержит в первой строке количество чисел N (2 ≤ N ≤ 68000). В каждой из последующих N строк записано одно целое положительное число, не превышающее 10000. Программа должна вывести длину найденной последовательности.

      ```python
      f = open('27_B.txt')
      a = [int(x) for x in f]
      n = a[0]
      del a[0]
      
      prefixsum = [0] * (n+1)
      for i in range(1, n+1):
          prefixsum[i] = prefixsum[i-1] + a[i-1]
      
      remainders = {}
      for i in range(n, -1, -1):
          remainders[prefixsum[i]%89] = i
      
      maxsum = 0
      maxlength = 0
      for i in range(n, -1, -1):
          j = remainders[prefixsum[i]%89]
          if prefixsum[i] - prefixsum[j] > maxsum:
              maxsum = prefixsum[i] - prefixsum[j]
              maxlength = i - j
          if prefixsum[i] - prefixsum[j] == maxsum and i - j < maxlength:
              maxlength = i - j
      print(maxlength)
      ```
