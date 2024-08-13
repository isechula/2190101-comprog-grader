### ​CitizenID (​★)

[Instructions](https://2190101.nattee.net/problems/840/get_statement/02_StrList_01.pdf)\
Solutions:

```python
inp = input()

formula = (11-(sum([(13-i)*int(inp[i]) for i in range(12)])%11))%10

print(inp[0], inp[1:5], inp[5:10], inp[-2:], formula)
```

```python
id = input()

checksum = (11 - (sum((13 - i) * int(id[i]) for i in range(0,12)) % 11)) % 10

print(f"{id[0]} {id[1:5]} {id[5:10]} {id[10:12]} {checksum}")
```

### ​Arabic ​Numerals (​★)

[Instructions](https://2190101.nattee.net/problems/841/get_statement/02_StrList_02.pdf)\
Solutions:

```python
n = input()
mid = "-->"
suf = ['zero', 'one', 'two', 'three', 'four', 'five', 'six', 'seven', 'eight', 'nine']

print(n, mid, suf[int(n)])
```

```python
numbers = ["zero", "one", "two", "three", "four", "five", "six", "seven", "eight", "nine"]
n = input()

print(f"{n} --> {numbers[int(n)]}")
```

### ​USDate (​★)

[Instructions](https://2190101.nattee.net/problems/842/get_statement/02_StrList_03.pdf)\
Solutions:

```python
d, m, y = input().split('/')
ml = ['January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'October', 'November', 'December']

print(ml[int(m)-1], str(d)+",", y)
```

```python
months = ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"]
date = input().split("/")

print(f"{months[int(date[1]) - 1]} {date[0]}, {date[2]}")
```

### ​NDigits (​★)

[Instructions](https://2190101.nattee.net/problems/843/get_statement/02_StrList_04.pdf)\
Solutions:

```python
n = [eval(i) for i in input()]
i = int(input())

if len(n) < i:
    il = i - len(n)
    for x in range(il):
        n.insert(x, 0)

print(*n, sep='')
```

```python
number = input()
length = int(input())
length_difference = length - len(number)

print("0"*length_difference + number)
```

### ​WeeklySales (​★)

[Instructions](https://2190101.nattee.net/problems/844/get_statement/02_StrList_05.pdf)\
Solutions:

```python
inp = input().split()
print(sum([int(i) for i in inp]))
```

```python
print(sum(map(int,input().split())))
```

### ​AddVector (​★★)

[Instructions](https://2190101.nattee.net/problems/845/get_statement/02_StrList_06.pdf)\
Solutions:

```python
u = [float(i) for i in (input().strip('[]')).split(',')]
v = [float(i) for i in (input().strip('[]')).split(',')]


print(u, '+', v, '=', [x+y for x, y in zip(u, v)])
```

```python
u = [float(i) for i in (input().strip('[]')).split(',')]
v = [float(i) for i in (input().strip('[]')).split(',')]


print(u, '+', v, '=', [x+y for x, y in zip(u, v)])
```

### ​Decryption (​★★★)

[Instructions](https://2190101.nattee.net/problems/846/get_statement/02_StrList_07.pdf)\
Solutions:

```python
symbols = ["A","B","C","D","E","F","G","H","I","J"]

n = input()
num_1 = n[3::7]
num_2 = n[7::5]

sum_num = str(int(num_1) + int(num_2) + 10000)

c_num = sum_num[-4:-1]

sum_c_num = str(sum(map(int, c_num)))
code = int(sum_c_num[-1])

print(c_num+symbols[int(code)])
```

```python
decryption_table = list("ABCDEFGHIJ")

data = input()
combination_term = int(data[3:32:7]) + int(data[7:28:5]) + 10000
middle_digits = str((combination_term//10 % 1000))
middle_digits_sum = sum(int(i) for i in middle_digits)

print(f"{middle_digits}{decryption_table[middle_digits_sum % 10]}")
```

### ​Decimal2Fraction (​★★★)

[Instructions](https://2190101.nattee.net/problems/1038/get_statement/02_StrList_08.pdf)\
Solutions:

```python
import math

inp = input().split(',')

a = int(inp[0] + inp[1] + inp[2]) - int(inp[0] + inp[1])
b = int(f'{"9" * len(inp[2])}{"0" * len(inp[1])}')

gcd = math.gcd(a, b)

print(f'{a//gcd} / {b//gcd}')
```

```python
import math

a,b,c = input().split(",")

top = int(a+b+c) - int(a+b)
bottom = 10**(len(b)+len(c)) - 10**len(b)
gcd = math.gcd(top, bottom)

print(f"{top//gcd} / {bottom//gcd}")
```
