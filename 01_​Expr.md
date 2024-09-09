### ​Stirling ​Factorial (​★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/01_Expr/01_Expr_01.pdf)\
Solutions:

```python
import math

n = int(input())
print(((2*math.pi)**(1/2))*(n**(n+(1/2)))*(math.e**(-n+(1/(12*n+1)))))
print(((2*math.pi)**(1/2))*(n**(n+(1/2)))*(math.e**(-n+(1/(12*n)))))
```

### ​Quadratic ​Root (​★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/01_Expr/01_Expr_02.pdf)\
Solutions:

```python
a = float(input())
b = float(input())
c = float(input())
print(round((-b-((b**2)-(4*a*c))**(1/2))/(2*a), 3), round((-b+((b**2)-(4*a*c))**(1/2))/(2*a), 3))
```

### ​An ​Expression (​★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/01_Expr/01_Expr_03.pdf)\
Solutions:

```python
import math

value = (math.pi-(math.factorial(10)/(8**8))+(math.log(9.7)**((7/(71**(1/2)))-math.sin(math.radians(40)))))/(1.2**(2.3**(1/3)))
print(round(value, 6))
```

### ​Body ​Surface ​Area (​★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/01_Expr/01_Expr_04.pdf)\
Solutions:

```python
import math

w = float(input())
h = float(input())
mosteller = ((w*h)**(1/2))/60
haycock = 0.024265*(w**0.5378)*(h**0.3964)
boyd = 0.0333*(w**(0.6157-(0.0188*math.log10(w))))*(h**0.3)
print(f'{mosteller}\n{haycock}\n{boyd}')
```

### ​Cubic ​Equation (​★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/01_Expr/01_Expr_05.pdf)\
Solutions:

```python
import math

a, b, c, d = list(map(float, input().split()))

sum_term = (2*(b**3) - 9*a*b*c + 27*(a**2)*d)
inner_root = math.sqrt(sum_term**2 - (4*((b**2 - 3*a*c)**3)))
inv_3a = 1/(3*a)

answer = (-b/(3*a)) - inv_3a*(((sum_term + inner_root)/2)**(1/3)) - inv_3a*(((sum_term - inner_root)/2)**(1/3))

print(round(answer,3))
```

### ​Duration (​★★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/01_Expr/01_Expr_06.pdf)\
Solutions:

```python
def dcalc(start_time, end_time):
    start_seconds = start_time[0] * 3600 + start_time[1] * 60 + start_time[2]
    end_seconds = end_time[0] * 3600 + end_time[1] * 60 + end_time[2]
    difference_seconds = abs(end_seconds - start_seconds)
    diff_hours = difference_seconds // 3600
    difference_seconds %= 3600
    diff_minutes = difference_seconds // 60
    diff_seconds = difference_seconds % 60
    return [diff_hours, diff_minutes, diff_seconds]


start = []
end = []
for i in range(3):
    start.append(input())
for i in range(3):
    end.append(input())

stl = []
etl = []
passed = False
for s in start:
    if not passed:
        stl.append(s)
        passed = True
        continue
    if int(s) > 9:
        stl.append(s)
    else:
        stl.append('0' + s)
for s in end:
    if not passed:
        etl.append(s)
        passed = True
        continue
    if int(s) > 9:
        etl.append(s)
    else:
        etl.append('0' + s)
sti = int(''.join(stl))
eti = int(''.join(etl))
if sti < eti:
    time = dcalc([int(s) for s in start], [int(s) for s in end])
else:
    not_time = dcalc([int(s) for s in end], [int(s) for s in start])
    time = dcalc(not_time, [24,0,0])
    

if sti == eti:
    print('0:0:0')
else:
    print(':'.join([str(s) for s in time]))
```

```python
h1 = int(input())
m1 = int(input())
s1 = int(input())
t1 = h1 * 3600 + m1 * 60 + s1

h2 = int(input())
m2 = int(input())
s2 = int(input()) 
t2 = h2 * 3600 + m2 * 60 + s2

dt = t2 - t1

dh = (dt // 3600) % 24
dm = (dt % 3600) // 60
ds = dt % 60

print(dh,dm,ds,sep=":")
```