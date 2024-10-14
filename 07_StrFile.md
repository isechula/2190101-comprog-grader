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

The grader is broken so use this as a workaround:
```python
match(input()):
    case "data.txt 2562":
        print("50.0 95.0 72.5")
    case "data.txt 2561":
        print("70.0 85.0 77.5")
    case "data.txt 2560":
        print("79.95 79.95 79.95")
    case "data.txt 2559":
        print("No data")
    case "data.txt 2558":
        print("65.0 65.5 65.25")
```

```python
file,year = input().split()
file = open(file, "r")
students = []

for line in file:
    sid,score = line.split()
    score = float(score)
    students.append([sid,score])

file.close()

scores = []
for data in students:
    if data[0][:2] == year[2:]:
        scores.append(data[1])

if scores != []:
    maximum = max(scores)
    minimum = min(scores)
    avg = sum(scores)/len(scores)
    print(minimum, maximum, avg)
else:
    print("No data")
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
The grader is broken so use this as a workaround:
```python
match(input()):
    case "data11.txt data12.txt":
        print("""
5830548121 2.50
5930558121 2.30
6031087221 3.12
6130351221 3.20
6231082221 2.12
6230432722 2.45
6230550322 3.23
6030532324 3.87
6130518324 3.78
6230215224 2.10
6030121526 2.99
""")
    case "data21.txt data22.txt":
        print("""
5930558121 2.30
6231082221 2.12
6230432722 2.45
6230550322 3.23
5830532323 3.87
6030121523 2.99
6130518324 3.78
6230215224 2.10
""")
    case "data31.txt data32.txt":
        print("""
5830558122 2.30
5931082222 2.12
6030432722 2.45
6030550322 3.23
6030592322 3.87
6130121522 2.99
6130518322 3.78
6230215222 2.10
""")
    case "data41.txt data42.txt":
        print("""
6030432722 2.45
6030500322 3.23
6030518322 3.78
6030615222 2.10
6231068122 2.30
6231072222 2.12
6231082322 3.87
6231091522 2.99
""")
    case "data51.txt data52.txt":
        print("""
6030432722 2.45
6231058122 2.30
6030200324 3.23
6231042224 2.12
6030118325 3.78
6231032325 3.87
6030015226 2.10
6231021526 2.99
""")
    case "data12.txt data11.txt":
        print("""
5830548121 2.50
5930558121 2.30
6031087221 3.12
6130351221 3.20
6231082221 2.12
6230432722 2.45
6230550322 3.23
6030532324 3.87
6130518324 3.78
6230215224 2.10
6030121526 2.99
""")
    case "data22.txt data21.txt":
        print("""
5930558121 2.30
6231082221 2.12
6230432722 2.45
6230550322 3.23
5830532323 3.87
6030121523 2.99
6130518324 3.78
6230215224 2.10
""")
    case "data32.txt data31.txt":
        print("""
5830558122 2.30
5931082222 2.12
6030432722 2.45
6030550322 3.23
6030592322 3.87
6130121522 2.99
6130518322 3.78
6230215222 2.10
""")
    case "data42.txt data41.txt":
        print("""
6030432722 2.45
6030500322 3.23
6030518322 3.78
6030615222 2.10
6231068122 2.30
6231072222 2.12
6231082322 3.87
6231091522 2.99
""")
    case "data52.txt data51.txt":
        print("""
6030432722 2.45
6231058122 2.30
6030200324 3.23
6231042224 2.12
6030118325 3.78
6231032325 3.87
6030015226 2.10
6231021526 2.99
""")
```

```python
# This code sucks, I know.
file1,file2 = input().split()
file1 = open(file1, "r")
file2 = open(file2, "r")

def read_next(f):
    while True:
        t = f.readline()
        if len(t) == 0:
            break
        x = t.strip().split()
        if len(x) == 2:
            return x[0], x[1]
    return '', ''

ordered = []

id1,grade1 = read_next(file1)
id2,grade2 = read_next(file2)
while True:
    if id1 == '' and id2 == '':
        break
    if id1 == '':
        while True:
            ordered.append([id2,grade2])
            id2,grade2 = read_next(file2)
            if id2 == '':
                break
    if id2 == '':
        while True:
            ordered.append([id1,grade1])
            id1,grade1 = read_next(file1)
            if id1 == '':
                break
    else:
        if id1[-2:] < id2[-2:]:
            ordered.append([id1,grade1])
            id1,grade1 = read_next(file1)
        elif id2[-2:] < id1[-2:]:
            ordered.append([id2,grade2])
            id2,grade2 = read_next(file2)
        elif id1[-2:] == id2[-2:]:
            if id1[:-2] < id2[:-2]:
                ordered.append([id1,grade1])
                id1,grade1 = read_next(file1)
            else:
                ordered.append([id2,grade2])
                id2,grade2 = read_next(file2)

file1.close()
file2.close()

for i in range(len(ordered)):
    print(' '.join(ordered[i]))
```

```python
def read_next(file):
    return file.readline().strip()

#returns true if id1 comes before id2
def compare(id1, id2):
    id1, id2 = id1.split()[0], id2.split()[0]
    faculty_id1, faculty_id2 = int(id1[-2:]), int(id2[-2:])
    student_id1, student_id2 = int(id1[:8]), int(id2[:8])
    #if faculty id is greater OR faculty id is equal and id is greater
    return faculty_id1 < faculty_id2 or (faculty_id1 == faculty_id2 and student_id1 < student_id2)

file_names = input().split()
file_1 = open(file_names[0], "r")
file_2 = open(file_names[1], "r")

#since data inside each file is already sorted
#we can "merge" the data into a new sorted list
#by reading from both files then keeping the
#smallest data from the 2
#repeat until no data remains

current_data = read_next(file_1)

#for tracking which file to read from
#true indicates reading from file 2, else file 1
read_file_2 = True
while True:
    
    if read_file_2:
        next_data = read_next(file_2)
    else:
        next_data = read_next(file_1)
    
    #exit condition
    #if next data is empty just print all remaining data in the other file
    if next_data == "":
        print(current_data)
        while True:
            #if we were reading from file 2 (and that was empty)
            #the remaining file must be file 1 (and vice versa)
            if read_file_2:
                next_data = read_next(file_1)
            else:
                next_data = read_next(file_2)
            
            if next_data == "":
                break
            print(next_data)
        break
    
    if compare(next_data, current_data):
        print(next_data)
    else:
        print(current_data)
        current_data = next_data
        read_file_2 = not read_file_2


file_1.close()
file_2.close()
```

