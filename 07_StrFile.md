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
data.txt:
```
6230012121 90.0
6130351221 80.0
6231027921 80.0
5830548121 65.5
6031087221 79.9
6230550321 70.0
6230432721 60.0
6230215221 50.0
6130518321 70.0
```

Solutions:

```python
#Solution Here
```

### DNA (★★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/07_StrFile/07_StrFile_​31.pdf)\
Solutions:

```python
#formatted such that index-2 = corresponding base pair
base_pairs = "actg"

#felt like making everything a function today
def validate(dna):
    for nucleotide in dna:
        if nucleotide not in base_pairs:
            return False
    return True

def reverse_complement(dna):
    output = ""
    for nucleotide in dna:
        output += base_pairs[base_pairs.index(nucleotide) - 2]
    return output.upper()[::-1]

def frequency(dna):
    nucleotides = [0] * 4
    for nucleotide in dna:
        nucleotides[base_pairs.index(nucleotide)] += 1
    return f"A={nucleotides[0]}, T={nucleotides[2]}, G={nucleotides[3]}, C={nucleotides[1]}"

def pair_count(dna, pair):
    count = 0
    searched_index = 0
    while searched_index < len(dna):
        next_index = dna.find(pair,searched_index)
        if next_index == -1:
            break;
        
        count += 1
        searched_index = next_index + 1
    return count

#part that handles the input
dna = input().lower().strip()

if not validate(dna):
    print("Invalid DNA")
else:
    command = input().strip()
    
    if command == "R":
        print(reverse_complement(dna))
    elif command == "F":
        print(frequency(dna))
    else:
        print(pair_count(dna, input().lower().strip()))
```

### Password Strength (★★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/07_StrFile/07_StrFile_​32.pdf)\
Solutions:

```python
#i know they want me to do like functions for this one
#but this is just easier since its not like any of the seperate checks are reused
password = input()
problems = []

#atleast 8 characters
if len(password) < 8:
    problems.append("Less than 8 characters")

#atleast 1 lower, upper, number and symbol
has_lower, has_upper, has_number, has_symbol = [False]*4
for letter in password:
    if letter.islower():
        has_lower = True
    elif letter.isupper():
        has_upper = True
    elif letter.isnumeric():
        has_number = True
    elif not letter.isalnum():
        has_symbol = True
        
if not has_lower:
    problems.append("No lowercase letters")

if not has_upper:
    problems.append("No uppercase letters")
    
if not has_number:
    problems.append("No numbers")

if not has_symbol:
    problems.append("No symbols")


#make 4 letter long clusters for checking
four_letter_clusters = []
for i in range(len(password) - 3):
    four_letter_clusters.append(password[i:i+4])

#no 4 repeating character
for cluster in four_letter_clusters:
    if cluster[0] == cluster[1] == cluster[2] == cluster[3]:
        problems.append("Character repetition")
        break
        
#no consecutive numbers letter or keyboard keys
alphabet = "abcdefghijklmnopqrstuvwxyz"
numbers = "01234567890"
qwerty = "!@#$%^&*()_+qwertyuiopasdfghjklzxcvbnm"

for cluster in four_letter_clusters:
    cluster = cluster.lower()
    if cluster in numbers or cluster in numbers[::-1]:
        problems.append("Number sequence")
        break
    
for cluster in four_letter_clusters:
    cluster = cluster.lower()     
    if cluster in alphabet or cluster in alphabet[::-1]:
        problems.append("Letter sequence")
        break
    
for cluster in four_letter_clusters:
    cluster = cluster.lower()
    if cluster in qwerty or cluster in qwerty[::-1]:
        problems.append("Keyboard pattern")
        break

#output
if len(problems) == 0:
    print("OK")
else:
    #putting knowledge to use is always fun
    print(*problems, sep="\n")

```

### File Merge (★★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/07_StrFile/07_StrFile_​33.pdf)\
Solutions:

```python
#Solution Here
```

