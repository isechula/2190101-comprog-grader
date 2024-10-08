### Plural (★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/07_StrFile/07_StrFile_​11.pdf)\
Solutions:

```python
def pluralize(word):
  new_word = ''
  if word[-1] == 's' or word[-1] == 'x' or word[-2:] == 'ch':
    new_word = word + 'es'
  elif word[-1] == 'y' and word[-2] not in 'aeiou':
    new_word = word[:-1] + 'ies'
  else:
    new_word = word + 's'
  return new_word

print(pluralize(input()))
```

### CamelCase (★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/07_StrFile/07_StrFile_​13.pdf)\
Solutions:

```python
sentence = input()
new_sentence = ''

alpha_upper = [chr(i) for i in range(65,91)]
alpha_lower = [chr(i) for i in range(97,123)]

for char in sentence:
    if char in alpha_lower or char in map(str,(range(10))):
        new_sentence += char
    elif char in alpha_upper:
        new_sentence += alpha_lower[alpha_upper.index(char)]
    else:
        new_sentence += ' '

new_sentence = new_sentence.split()

newer_sentence = ''
for word in new_sentence:
    if word[0] in alpha_lower:
        word = alpha_upper[alpha_lower.index(word[0])] + word[1:]
    newer_sentence += word

if newer_sentence[0] in alpha_upper:
    newer_sentence = alpha_lower[alpha_upper.index(newer_sentence[0])] + newer_sentence[1:]

print(newer_sentence)
```

```python
valid_characters = "abcdefghijklmnopqrstuvwxyz0123456789"

#something something oneliners
#replace all non valid characters with spaces
#then turn into a string to be stripped
#then turn back into an array so it stays mutable
letters = list("".join([i if i in valid_characters else " " for i in input().lower()]).strip())

#javascript programmers rejoice!
camelCase = ""

#since all characters start in lowercase
#if we encounter a space just make the next letter uppercase
for i in range(len(letters)):
    letter = letters[i]
    if letter == " ":
        letters[i+1] = letters[i+1].upper()
    else:
        camelCase += letter

print(camelCase)
```

### Rot13 (★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/07_StrFile/07_StrFile_​21.pdf)\
Solutions:

```python
def rot13(s):
    s2 = ''
    for c in s:
        if ord(c) >= 65 and ord(c) <= 77:
            s2 += chr(ord(c)+13)
        elif ord(c) >= 78 and ord(c) <= 90:
            s2 += chr(ord(c)+13-26)
        elif ord(c) >= 97 and ord(c) <= 109:
            s2 += chr(ord(c)+13)
        elif ord(c) >= 110 and ord(c) <= 122:
            s2 += chr(ord(c)+13-26)
        else:
            s2 += c
    return s2

while True:
    sent = input()
    if sent == 'end':
        break
    print(rot13(sent))
```

```python
#solution where you dont have to remember any unicode tricks
alphabet = "abcdefghijklmnopqrstuvwxyz"

def rot13(string):
    output = ""
    for letter in string:
        if letter.lower() not in alphabet:
            output += letter
            continue
        
        cypher_letter = alphabet[(alphabet.index(letter.lower()) + 13) % 26]
        if letter.isupper():
            output += cypher_letter.upper()
        else:
            output += cypher_letter
    return output

while True:
    string = input()
    
    if string == "end":
        break
    print(rot13(string))
```

### Anagram (★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/07_StrFile/07_StrFile_​22.pdf)\
Solutions:

```python
str1 = list(''.join(input().lower().split()))
str2 = list(''.join(input().lower().split()))

ana = 'YES'
if len(str1) != len(str2):
    ana = 'NO'
else:
    for c in str1:
        if c in str2:
            str2.remove(c)
        else:
            ana = 'NO'
            break

print(ana)
```

```python
#i know they want me to use unicode but like this is alot easier
alphabet = "abcdefghijklmnopqrstuvwxyz"

def count_letters(string):
    letters = [0] * 26
    for letter in string.lower():
        if letter in alphabet:
            letters[alphabet.index(letter)] += 1
    return letters

#dunno if ill ever get used to array comparisons looking like this
if count_letters(input()) == count_letters(input()):
    print("YES")
else:
    print("NO")
```

### File Min Max Average (★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/07_StrFile/07_StrFile_​23.pdf)\
Solutions:

```python
#Solution Here
```

### DNA (★★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/07_StrFile/07_StrFile_​31.pdf)\
Solutions:

```python
#Solution Here
```

### Password Strength (★★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/07_StrFile/07_StrFile_​32.pdf)\
Solutions:

```python
#Solution Here
```

### File Merge (★★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/07_StrFile/07_StrFile_​33.pdf)\
Solutions:

```python
#Solution Here
```

