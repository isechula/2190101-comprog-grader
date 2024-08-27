### ​BirthdayParadox (​◇◇)

[Instructions](https://2190101.nattee.net/problems/874/get_statement/04_Loop_001.pdf)\
Solutions:

```python
p = float(input())
k,t = 1,1

while True:
    t = t*(365-(k-1))/365
    if 1-t >= p:
        break
    k += 1
    
print(k)
```

### ​Partition (​◇◇)

[Instructions](https://2190101.nattee.net/problems/875/get_statement/04_Loop_002.pdf)\
Solutions:

```python
d = list(map(int,input().split()))
p = d[-1]
i,j = -1,0
n = len(d)

while j < n-1:
    if d[j] <= p:
        i += 1
        d[i],d[j] = d[j],d[i]
    j += 1

d[i+1],d[-1] = d[-1],d[i+1]

print(d)
```

### ​Average (​★)

[Instructions](https://2190101.nattee.net/problems/864/get_statement/04_Loop_01.pdf)\
Solutions:

```python
num = []

while True:
    a = input()
    if a == 'q':
        break
    num += [float(a)]

if num == []:
    print("No Data")
else:
    print(round(sum(num)/len(num),2))
```

### ​Bisection ​Log10 (​★)

[Instructions](https://2190101.nattee.net/problems/865/get_statement/04_Loop_02.pdf)\
Solutions:

```python
a = float(input())
L,U = 0,a
x = (L+U)/2
    
while not abs(a-10**x) <= (10**-10)*max(a,x**2):
    if 10**x > a:
        U = x
    else:
        L = x
    x = (L+U)/2

print(round(x,6))
```

### ​MCQ (​★)

[Instructions](https://2190101.nattee.net/problems/866/get_statement/04_Loop_03.pdf)\
Solutions:

```python
#Solution Here
```

### ​Parentheses (​★)

[Instructions](https://2190101.nattee.net/problems/867/get_statement/04_Loop_04.pdf)\
Solutions:

```python
#Solution Here
```

### ​CountWord (​★)

[Instructions](https://2190101.nattee.net/problems/868/get_statement/04_Loop_05.pdf)\
Solutions:

```python
#Solution Here
```

### ​PrintTriangle (​★)

[Instructions](https://2190101.nattee.net/problems/869/get_statement/04_Loop_06.pdf)\
Solutions:

```python
#Solution Here
```

### ​Bisection ​Log10 ​2 (​★★)

[Instructions](https://2190101.nattee.net/problems/870/get_statement/04_Loop_10.pdf)\
Solutions:

```python
#Solution Here
```

### ​RLE (​★★)

[Instructions](https://2190101.nattee.net/problems/871/get_statement/04_Loop_11.pdf)\
Solutions:

```python
#Solution Here
```

### ​ZigZag ​1 (​★★)

[Instructions](https://2190101.nattee.net/problems/872/get_statement/04_Loop_12.pdf)\
Solutions:

```python
#Solution Here
```

### ​Max ​2ndMax (​★★)

[Instructions](https://2190101.nattee.net/problems/876/get_statement/04_Loop_13.pdf)\
Solutions:

```python
#Solution Here
```

### ​ZigZag ​2 (​★★★)

[Instructions](https://2190101.nattee.net/problems/873/get_statement/04_Loop_20.pdf)\
Solutions:

```python
#Solution Here
```

