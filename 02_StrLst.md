### ​CitizenID (​★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/02_StrList/02_StrList_​01.pdf)\
Solutions:

```python
inp = input()

formula = (11-(sum([(13-i)*int(inp[i]) for i in range(12)])%11))%10

print(inp[0], inp[1:5], inp[5:10], inp[-2:], formula)
```
```python
id: list[int | str] = list(map(int, input()))

id_count_sum: int = sum(map( lambda enum: (enum[0] + 2) * enum[1], enumerate(id[::-1]) ))

n12: int = (11 - (id_count_sum % 11)) % 10

id.insert(1, " ")
id.insert(6, " ")
id.insert(12, " ")

id.append(" ")
id.append(n12)

output_id: str = "".join(map(str,id))

print(output_id)
```
### ​Arabic ​Numerals (​★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/02_StrList/02_StrList_​02.pdf)\
Solutions:

```python
n = input()
mid = "-->"
suf = ['zero', 'one', 'two', 'three', 'four', 'five', 'six', 'seven', 'eight', 'nine']

print(n, mid, suf[int(n)])
```

### ​USDate (​★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/02_StrList/02_StrList_​03.pdf)\
Solutions:

```python
d, m, y = input().split('/')
ml = ['January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'October', 'November', 'December']

print(ml[int(m)-1], str(d)+",", y)
```

### ​NDigits (​★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/02_StrList/02_StrList_​04.pdf)\
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
```python
from itertools import zip_longest

m: str = input()
n: int = int(input())

m_list: list[int] = list(map(int, m))[::-1]

n_list: list[int] = [0 for _ in range(n)]

zippped_list = zip_longest(m_list, n_list, fillvalue=0)

sum_list: list[int] = list(map(sum, zippped_list))[::-1]

output: str = "".join(map(str, sum_list))

print(output)
```
### ​WeeklySales (​★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/02_StrList/02_StrList_​05.pdf)\
Solutions:

```python
inp = input().split()
print(sum([int(i) for i in inp]))
```

```python
print(sum(map(int,input().split())))
```

### ​AddVector (​★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/02_StrList/02_StrList_​06.pdf)\
Solutions:

```python
u = [float(i) for i in (input().strip('[]')).split(',')]
v = [float(i) for i in (input().strip('[]')).split(',')]


print(u, '+', v, '=', [x+y for x, y in zip(u, v)])
```

```python
u = list(map(float, input()[1:-1].split(", ")))
v = list(map(float, input()[1:-1].split(", ")))
vec_sum = [u[0]+v[0], u[1]+v[1], u[2]+v[2]]

print(f"{u} + {v} = {vec_sum}")
```

### ​Decryption (​★★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/02_StrList/02_StrList_​07.pdf)\
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
```python
secret: str = input()
a: str = secret[3::7]
b: str = secret[7::5]

d: str = str(int(a) + int(b) + 10000)[-4:-1]
e: int = (sum(map(int,d)) % 10) + 1

# Get ASCII Letter
f: str = chr(e + 64)

decoded_data: str = d + f

print(decoded_data)
```
### ​Decimal2Fraction (​★★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/02_StrList/02_StrList_​08.pdf)\
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

```python
from fractions import Fraction

nums = input().split(',')

numerator = int(nums[0] + nums[1] + nums[2]) - int(nums[0] + nums[1])
denominator = int('9' * len(nums[2]) + '0' * len(nums[1]))
frac = str(Fraction(f'{numerator}/{denominator}')).split('/')
try:
    print(f'{frac[0]} / {frac[1]}')
except IndexError:
    print(f'{frac[0]} / 1')
```
