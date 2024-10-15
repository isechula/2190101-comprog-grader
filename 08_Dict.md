### Reverse n Keys (★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/08_Dict/08_Dict_​11.pdf)\
Solutions:

```python
#at time of writing there are 3 test cases and none of them test the keys() function lol
def keys(dictionary, target_value):
    output = []
    for key in dictionary:
        if dictionary[key] == target_value:
            output.append(key)
    return output

def reverse(dictionary):
    output = {}
    for key in dictionary:
        output[dictionary[key]] = key
    return output

exec(input().strip())
```

### Nicknames (★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/08_Dict/08_Dict_​12.pdf)\
Solutions:

```python
names = {}
for i in range(int(input())):
    first_name, nickname = input().strip().split()
    names[first_name] = nickname
    names[nickname] = first_name

for i in range(int(input())):
    print(names.get(input().strip(), "Not found"))
```

### Char Count (★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/08_Dict/08_Dict_​21.pdf)\
Solutions:

```python
letters = {}
for letter in input().lower():
    if not letter.isalpha():
        continue
    
    if letter in letters:
        letters[letter] += 1
    else:
        letters[letter] = 1

#i feel magical
#basically turn the dict an array with the form [[-count1, letter1], ...]
#then sort that array ascending, which makes it sort by descending count then ascending letters
#(just be sure to invert the count again)
for num, letter in sorted([[-letters[k],k] for k in letters]):
    print(f"{letter} -> {-num}")
```

### Ice Cream Sales (★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/08_Dict/08_Dict_​22.pdf)\
Solutions:

```python
#Solution Here
```

### Telephone Directory (★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/08_Dict/08_Dict_​23.pdf)\
Solutions:

```python
#Solution Here
```

### Texting (★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/08_Dict/08_Dict_​24.pdf)\
Solutions:

```python
#Solution Here
```

### Cash (★★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/08_Dict/08_Dict_​31.pdf)\
Solutions:

```python
#Solution Here
```

