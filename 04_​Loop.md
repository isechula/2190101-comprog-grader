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

```python
number = float(input())
lower_bound = 0
upper_bound = number
middle = (lower_bound + upper_bound)/2
guess = 10 ** middle

#while our guess is "not close enough" to the answer
while abs(number - guess) > 10**-10 * max(number, guess):
    #if our guess is too high, lower the upper bound
    #else if our guess is too low, raise the lower bound
    if guess > number:
        upper_bound = middle
    elif guess < number:
        lower_bound = middle
        
    middle = (lower_bound + upper_bound)/2
    guess = 10 ** middle

print(round(middle,6))
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

```python
#I don't know if this is exactly "better"
#It's atleast shorter
keyword = input()

#filter out special characters
filtered_sentence = ""
for letter in input():
    if letter in "\"\'(),.":
        filtered_sentence += " "
    else:
        filtered_sentence += letter

count = 0
for word in filtered_sentence.split():
    if keyword == word:
        count += 1

print(count)
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
a = float(input())
b = a
L = 0
U = 0

while True:
    b //= 10
    U += 1
    if b == 0:
        break

x = (L+U)/2
    
while not abs(a-10**x) <= (10**-10)*max(a,x**2):
    if 10**x > a:
        U = x
    else:
        L = x
    x = (L+U)/2

print(round(x,6))
```

```python
number = float(input())
lower_bound = 0
#since 1 + log_10(n) is a fancy way of asking how many digits there are in the decimal
#representation of the number
#(btw this wouldn't work with float inputs)
upper_bound = len(str(number))
    
middle = (lower_bound + upper_bound)/2
guess = 10 ** middle

#while our guess is "not close enough" to the answer
while abs(number - guess) > 10**-10 * max(number, guess):
    #if our guess is too high, lower the upper bound
    #else if our guess is too low, raise the lower bound
    if guess > number:
        upper_bound = middle
    elif guess < number:
        lower_bound = middle
        
    middle = (lower_bound + upper_bound)/2
    guess = 10 ** middle

print(round(middle,6))
```

### ​RLE (​★★)

[Instructions](https://2190101.nattee.net/problems/871/get_statement/04_Loop_11.pdf)\
Solutions:

```python
string = input()
encoded = ''
current = string[0]
count = 0

for char in string:
    if char == current:
        count += 1
    else:
        encoded += current + " " + str(count) + " "
        current = char
        count = 1

encoded += current + " " + str(count)

print(encoded)
```

### ​ZigZag ​1 (​★★)

[Instructions](https://2190101.nattee.net/problems/872/get_statement/04_Loop_12.pdf)\
Solutions:

```python
pair = int(input())
mylist = []

for i in range(pair):
    mylist += [list(map(int,input().split()))]

command = input()
X = []
Y = []

if command == 'Zig-Zag':
    for i in range(pair):
        if i%2 == 0:
            X += [mylist[i][0]]
            Y += [mylist[i][1]]
        else:
            X += [mylist[i][1]]
            Y += [mylist[i][0]]
elif command == 'Zag-Zig':
    for i in range(pair):
        if i%2 != 0:
            X += [mylist[i][0]]
            Y += [mylist[i][1]]
        else:
            X += [mylist[i][1]]
            Y += [mylist[i][0]]

print(min(X),max(Y))
```

### ​Max ​2ndMax (​★★)

[Instructions](https://2190101.nattee.net/problems/876/get_statement/04_Loop_13.pdf)\
Solutions:

```python
# I passed the examples but scored 0 on the test cases, idk
exec(input().strip())
n = int(input())

largest = int(input())
second = int(input())

if second > largest:
    second,largest = largest,second
    
for i in range(n-2):
    num = int(input())
    if num >= largest:
        second = largest
        largest = num
    elif num > second:
        second = num

print(largest, second)
```
```python
# Temporary solution before they fix the exec thingy
lol = input()
print('spj')
n = int(input())

largest = int(input())
second = int(input())

if second > largest:
    second,largest = largest,second
    
for i in range(n-2):
    num = int(input())
    if num >= largest:
        second = largest
        largest = num
    elif num > second:
        second = num

print(largest, second)
```

### ​ZigZag ​2 (​★★★)

[Instructions](https://2190101.nattee.net/problems/873/get_statement/04_Loop_20.pdf)\
Solutions:

```python
red_min,blue_min = map(int,input().split())
red_max,blue_max = red_min,blue_min

i = 1

while True:
    command = input()
    if command == "Zig-Zag" or command == "Zag-Zig":
        break
    X,Y = map(int,command.split())
    if i%2 == 0:
        if X < red_min:
            red_min = X
        elif X > red_max:
            red_max = X
        if Y < blue_min:
            blue_min = Y
        elif Y > blue_max:
            blue_max = Y
    else:
        if Y < red_min:
            red_min = Y
        elif Y > red_max:
            red_max = Y
        if X < blue_min:
            blue_min = X
        elif X > blue_max:
            blue_max = X
    i += 1

if command == "Zig-Zag":
    print(red_min, blue_max)
elif command == "Zag-Zig":
    print(blue_min, red_max)
```

