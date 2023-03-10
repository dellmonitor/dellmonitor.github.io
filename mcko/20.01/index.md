## МЦКО 20 января

### Вариант 1
<!--
1.   На рисунке схема дорог Н-ского района изображена в виде графа, в таблице содержатся сведения о протяжённости каждой из этих дорог (в километрах).

     ![1-е задание](/mcko/20.01/1.png)

     |    	| П1 	| П2 	| П3 	| П4 	| П5 	| П6 	| П7 	| П8 	|
     |----	|----	|----	|----	|----	|----	|----	|----	|----	|
     | П1 	| ■  	|    	|    	| 10 	| 15 	|    	|    	| 12 	|
     | П2 	|    	| ■  	| 20 	|    	|    	|    	| 23 	|    	|
     | П3 	|    	| 20 	| ■  	|    	|    	| 21 	|    	|    	|
     | П4 	| 10 	|    	|    	| ■  	|    	|    	| 8  	| 7  	|
     | П5 	| 15 	|    	|    	|    	| ■  	| 11 	|    	| 13 	|
     | П6 	|    	|    	| 21 	|    	| 11 	| ■  	| 9  	|    	|
     | П7 	|    	| 23 	|    	| 8  	|    	| 9  	| ■  	|    	|
     | П8 	| 12 	|    	|    	| 7  	| 13 	|    	|    	| ■  	|

     Так как таблицу и схему рисовали независимо друг от друга, то нумерация населённых пунктов в таблице никак не связана с буквенными обозначениями на графе. Определите, какова сумма протяжённостей дорог из пункта E в пункт C и из пункта F в пункт G.

     В ответе запишите целое число.

2.   Миша заполнял таблицу истинности логической функции F = w → ((x → z) → y), но успел заполнить лишь фрагмент из трёх различных её строк, даже не указав, какому столбцу таблицы соответствует каждая из переменных w, x, y, z.

     | ? | ? | ? | ? | F |
     |---|---|---|---|---|
     |   |   | 0 | 1 | 0 |
     |   | 0 | 1 |   | 0 | 
     |   |   |   | 0 | 0 | 

     В ответе напишите буквы w, x, y, z в том порядке, в котором идут соответствующие им столбцы (сначала буква, соответствующая первому столбцу; затем буква, соответствующая второму столбцу, и т.д.). Буквы в ответе пишите подряд, никаких разделителей между буквами ставить не нужно.
Пример. Функция задана выражением ¬x ∨ y, зависящим от двух переменных, а фрагмент таблицы имеет следующий вид.

     |   |   |¬x ∨ y|
     |---|---|---| 
     | 0 | 1 |   0  | 

     В этом случае первому столбцу соответствует переменная y, а второму столбцу – переменная x. В ответе следует написать yx.

4. По каналу связи передаются сообщения, содержащие только буквы из набора: А, Ф, О, Р. Для передачи используется двоичный код, удовлетворяющий условию Фано. Это условие обеспечивает возможность однозначной расшифровки закодированных сообщений. Кодовые слова для некоторых букв известны: А – 01, Ф – 1. Для двух оставшихся букв О и Р кодовые слова неизвестны. Какое количество двоичных знаков потребуется для кодирования слова ФОРА, если известно, что оно закодировано минимально возможным количеством двоичных знаков?
-->

5.   На вход алгоритма подаётся натуральное число N. Алгоритм строит по нему новое число R следующим образом:
        1. Строится шестнадцатеричная запись числа.
        2. Далее, эта запись обрабатывается по следующему правилу:
            * Если цифр B в ней чётное количество, то к этой записи слева дописывается 1.
            * Если цифр B в ней нечётное количество, то к этой записи справа дописывается 1.
     Полученная таким образом запись является шестнадцатеричной записью искомого числа R.

     Например, возьмём число 91. Строим шестнадцатеричную запись числа: 5B. Цифра B в нём одна – нечётное количество, значит, единицу дописываем справа. Итоговое число 5B1 переводим в десятичную систему – 1457. Число 1457 и является результатом работы алгоритма.

     Определите количество натуральных чисел N, для которых результатом выполнения алгоритма может стать двузначное число.

     ```python
     k=0
     for i in range(1,1000000):
         n = i
         d = hex(n)[2:]
         if d.count('b') % 2 == 0:
             s = '1' + d
         else:
             s = d + '1'
         r = int(s, base=16)
         if r>9 and r<100:
             k+=1
     print(k)
     ```

6.   Исполнитель Черепаха действует на плоскости с декартовой системой координат. В начальный момент Черепаха находится в начале координат, её голова направлена вдоль положительного направления оси ординат, хвост опущен. При опущенном хвосте Черепаха оставляет на поле след в виде линии. В каждый конкретный момент известно положение исполнителя и направление его движения. У исполнителя существует шесть команд:
     * Поднять хвост, означающая переход к перемещению без рисования;
     * Опустить хвост, означающая переход в режим рисования;
     * Вперёд n (где n – целое число), вызывающая передвижение Черепахи на n единиц в том направлении, куда указывает её голова;
     * Назад n (где n – целое число), вызывающая передвижение Черепахи на n единиц в направлении противоположном тому, куда указывает её голова;
     * Направо m (где m – целое число), вызывающая изменение направления движения на m градусов по часовой стрелке, и
     * Налево m (где m – целое число), вызывающая изменение направления движения на m градусов против часовой стрелки.

     Запись Повтори k [Команда1 Команда2 … КомандаS] означает, что последовательность из S команд повторится k раз.

     Черепахе был дан для исполнения следующий алгоритм:

     Повтори 6 [Вперёд 25 Направо 120]<br>
     Поднять хвост<br>
     Вперёд 20 Налево 90 Назад 5<br>
     Опустить хвост<br>
     Повтори 2 [Вперёд 20 Налево 90 Вперёд 10 Налево 90]

     Определите, сколько точек с целочисленными координатами будут находиться внутри пересечения фигур, ограниченных заданными алгоритмом линиями, включая точки на границах этого пересечения.

     ```python
     from turtle import *
     screensize(10000,10000)
     tracer(0)
     r=25

     for i in range(6):
         fd(25*r)
         rt(120)
     up()
     fd(20*r)
     lt(90)
     bk(5*r)
     down()
     for i in range(2):
         fd(20*r)
         lt(90)
         fd(10*r)
         lt(90)
     up()
     for x in range(-20,20):
         for y in range(-20,20):
             goto(x*r,y*r)
             dot(3,'blue')
     update()
     ```

8.   На шоколадной фабрике собирают новогодние подарки. В подарок могут попасть: печенье, конфеты, батончики. Т.к. фабрика хочет сэкономить, то было решено, что в каждом подарке количество конфет > количества печенья > количества батончиков и суммарно должно быть не более 15 сладостей. Сколько способов существует собрать новогодние подарки?
P.S. - необязательно использовать сладость каждого вида

     ```python
     c=0
     for b in range(15):
         for p in range(15):
             for k in range(15):
                 if b<p<k and b+p+k<=15:
                     c+=1
     print(c)
     ```

12.   Исполнитель Редактор получает на вход строку цифр и преобразовывает ее.

      НАЧАЛО<br>
      &nbsp;&nbsp;ПОКА нашлось (33333) ИЛИ нашлось (999)<br>
      &nbsp;&nbsp;&nbsp;&nbsp;ЕСЛИ нашлось (33333)<br>
      &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ТО заменить (33333, 99)<br>
      &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ИНАЧЕ заменить (999, 3)<br>
      &nbsp;&nbsp;&nbsp;&nbsp;КОНЕЦ ЕСЛИ<br>
      &nbsp;&nbsp;КОНЕЦ ПОКА<br>
      КОНЕЦ

      Какая строка получится в результате применения приведенной ниже программы к строке, состоящей из 84 идущих подря цифр 9? В ответе запишите полученную строку.

      ```python
      s = '9' * 84
      while '33333' in s or '999' in s:
          if '33333' in s:
              s = s.replace('33333', '99', 1)
          else:
              s = s.replace('999', '3', 1)
      print(s)
      ```

14.   Число 100 в системе счисления с основанием N имеет 3 значащих разряда. Найдите все системы счисления, для которых это утверждение справедливо. В качестве ответа запишите сумму оснований найденных систем счисления.

      ```python
      def vvv(n,a):
          d=0
          while n>0:
              d+=1
              n=n//a
          return d
      s=0
      for i in range(2,100):
          if vvv(100,i)==3:
              s+=i
      print(s)
      ```
15.   Обозначим через ДЕЛ(n, m) утверждение «натуральное число n делится без остатка на натуральное число m».
      Укажите наименьшее целое значение A, для которого формула

      (ДЕЛ(108, x)→ ¬ДЕЛ(x, y)) ∨ (x + y > 80) ∨ (A – y > x)

      тождественно истинна при любых натуральных значениях переменных x и y.

      ```python
      def f(x,y,a):
          return ((108 % x == 0)<=(not(x%y==0))) or ((x+y)>80 or (a-y)>x)

      for a in range(1,1000):
          if all(f(x,y,a)==1 for x in range(1,1000) for y in range(1,1000)):
              print(a)
              break
      ```

17.   Файл содержит последовательность целых чисел, по модулю не превышающих 10 000. Назовём парой два идущих подряд элемента последовательности. Определите количество таких пар, в которых запись меньшего элемента заканчивается цифрой 3, а сумма квадратов элементов пары меньше, чем квадрат наименьшего из элементов последовательности, запись которых заканчивается цифрой 3. В ответе запишите два числа: сначала количество найденных пар, затем максимальную сумму квадратов элементов этих пар.

      <a href="/mcko/20.01/17.txt" download>17.txt</a>

      ```python
      f = open('вар 1/17 (12).txt')
      a = [int(x) for x in f]
      b = [x for x in a if abs(x)%10==3]
      m = min(b)#-9983
      c = []
      for i in range(len(a)-1):
          m1 = min(a[i],a[i+1])
          if abs(m1)%10==3 and a[i]**2 + a[i+1]**2 < m**2:
              c.append(a[i]**2+a[i+1]**2)
      print(len(c), max(c))
      ```

23.   Исполнитель преобразует число на экране. У исполнителя есть три команды, которым присвоены номера:
        1. Прибавить единицу
        2. Умножить на два
        3. Возвести в квадрат
      
      Программа для исполнителя – это последовательность команд.
      Сколько существует программ, для которых при исходном числе 2 результатом является число 65, при этом траектория вычислений содержит число 16 и не содержит 17?
      Траектория вычислений программы – это последовательность результатов выполнения всех команд программы. Например, для программы 121 при исходном числе 7 траектория будет состоять из чисел 8, 16, 17.

      ```python
      def f(x,y):
          if x > y or x==17:
              return 0
      if x==y:
          return 1
      if x<y:
          return f(x+1,y) + f(x*2,y) + f(x**2,y)

      print(f(2,16)*f(16,65))
      ```


25.   Назовём маской числа последовательность цифр, в которой также могут встречаться следующие символы:
– символ «?» означает ровно одну произвольную цифру;
– символ «\*» означает любую последовательность цифр произвольной длины; в том числе «\*» может задавать и пустую последовательность.
Например, маске 123\*4?5 соответствуют числа 123405 и 12300405.
Среди натуральных чисел, не превышающих 10<sup>8</sup>, найдите все числа, соответствующие маске \*1?542?, делящиеся на 2084 без остатка.
В ответе запишите в первом столбце таблицы все найденные числа в порядке возрастания, а во втором столбце – соответствующие им результаты деления этих чисел на 2084.

      ```python
      for i in range(100):
          for j in range(10):
              for x in range(10):
                  s = str(i)+'1'+str(j)+'542'+str(x)
                  s1 = int(s)
     	          if s1%2084==0 and s1<=10**8:
                      print(s1,s1//2084)
      ```

      ```python
      from fnmatch import fnmatch

      for i in range(0, 10**8, 2084):
          if fnmatch(str(i), '*1?542?'):
              print(i, i//2084)
      ``` 

26.   На прямолинейном участке пути для обеспечения связи необходимо разместить радиопередатчики. Установка каждого такого передатчика возможна на любом из N объектов, включённом в перечень разрешённых. Известно расстояние от нулевой отметки на этом участке до каждого объекта из данного перечня, кроме того по технических нормативам для работы без помех два соседних передатчика должны находиться на расстоянии не менее 8 единиц друг от друга. На данном участке пути необходимо разместить максимальное количество передатчиков, не нарушая технические нормативы. Определите количество передатчиков при таком размещении и максимально возможное расстояние от нулевой отметки до ближайшего к ней передатчика.

      <a href="/mcko/20.01/26.txt" download>26.txt</a>

      <a href="/mcko/20.01/26.xlsx" download>Решение</a> через Эксель

### Вариант 2

6.    Исполнитель Черепаха действует на плоскости с декартовой системой координат. В начальный момент Черепаха находится в начале координат, её голова направлена вдоль положительного направления оси ординат, хвост опущен. При опущенном хвосте Черепаха оставляет на поле след в виде линии. В каждый конкретный момент известно положение исполнителя и направление его движения. У исполнителя существует две команды:

      * Вперёд n (где n – целое число), вызывающая передвижение Черепахи на n единиц в том направлении, куда указывает её голова,<br>
      * Налево m (где m – целое число), вызывающая изменение направления движения на m градусов против часовой стрелки и <br>
      * Направо m (где m – целое число), вызывающая изменение направления движения на m градусов по часовой стрелке.

      Запись Повтори k [Команда1 Команда2 … КомандаS] означает, что последовательность из S команд повторится k раз. 
Черепахе был дан для исполнения следующий алгоритм:

      Направо 198 <br>
      Повтори 5 [Вперёд 10 Налево 144].

      Определите, сколько различных треугольников находятся в области, ограниченной линией, заданной данным алгоритмом.
 
      ```python 
      from turtle import *
      screensize(10000,10000)
      tracer(0)
      r=25

      rt(198)
      for i in range(5):
          fd(10*r)
          rt(144)
      up()

      for x in range(-20,20):
          for y in range(-20,20):
              goto(x*r,y*r)
              dot(3,'blue')
      update()
      ``` 

8.    Инженер Петр пишет программу для банкомата, чтобы он мог разменивать денежные средства. В распоряжении у банкомата имеются монеты номиналом 1 рубль, 2, 5 и 10. Количество монет каждого вида не ограничено. Сколько существует способов разменять сумму 100 рублей? При размене необязательно использовать монеты каждог номинала.

      ```python
      n = 100
      count = 0
      for n1 in range(n//1+1):
          for n2 in range(n//2+1):
              for n5 in range(n//5+1):
                  for n10 in range(n//10+1):
                      if n1 + 2*n2 + 5*n5 + 10*n10 == n:
                          count += 1
      print(count)
      ```

      ```python
      KINDS_OF_COINS = [1, 2, 5, 10]

      def count_change(amount, coins):
          if amount == 0:
              return 1
          if amount < 0 or coins == []:
              return 0

          return (count_change(amount, coins[:-1]) + 
                  count_change(amount - coins[-1], coins))

      print(count_change(100, KINDS_OF_COINS))
      ```

24.   В текстовом файле находится цепочка из символов латинского алфавита A, B, C, D, E, F. Найдите максимальную длину цепочки вида CACACA.... (состоящей из фрагментов CA, последний фрагмент может быть неполным).

      <a href="/mcko/20.01/24.txt" download>24.txt</a>

      ```python
      f=open('24.txt')
      s = f.readline()
      c = ''
      while c in s:
          c+='CA'
      print(len(c[:-2]))
      print(c[:-2] in s)
      ```

