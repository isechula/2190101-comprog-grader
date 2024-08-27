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

```python
input_string = input()
count, total = 0, 0
while input_string != "q":
    count += 1
    total += float(input_string)
    input_string = input()

if count > 0:
    print(round(total/count,2))
else:
    print("No Data")
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
correct = input()
student = input()
score = 0

if len(correct) == len(student):
    for i in range(len(correct)):
        if correct[i] == student[i]:
            score += 1
    print(score)
else:
    print("Incomplete answer")
```

### ​Parentheses (​★)

[Instructions](https://2190101.nattee.net/problems/867/get_statement/04_Loop_04.pdf)\
Solutions:

```python
text = input()
text2 = ''

for i in range(len(text)):
    if text[i] == '(':
        text2 += '['
    elif text[i] == '[':
        text2 += '('
    elif text[i] == ')':
        text2 += ']'
    elif text[i] == ']':
        text2 += ')'
    else:
        text2 += text[i]

print(text2)
```

### ​CountWord (​★)

[Instructions](https://2190101.nattee.net/problems/868/get_statement/04_Loop_05.pdf)\
Solutions:

```python
# Please tell me there is a better way to do this...
keyword = input()
sentence = input()
word = ''
word_list = []

for char in sentence:
    if char not in "\"(),.' ":
        word += char
    else:
        if word != '':
            word_list += [word]
            word = ''

if sentence[-1] not in "\"(),.' ":
    word_list += [word]

number = 0

for word in word_list:
    if keyword == word:
        number += 1

print(number)
```

### ​PrintTriangle (​★)

[Instructions](https://2190101.nattee.net/problems/869/get_statement/04_Loop_06.pdf)\
Solutions:

```python
h = int(input())

print(" "*(h-1)+"*")

for i in range(1,h-1):
    print(" "*(h-i-1)+"*"+(2*i-1)*" "+"*")

print("*"*(2*h-1))
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

