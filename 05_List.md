### MissingDigits (★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/05_List/05_List_​11.pdf)\
Solutions:

```python
string = input()
found = []
for i in range(10):
    if str(i) not in string:
        found.append(str(i))

if len(found) > 0:
    print(",".join(found))
else:
    print("None")
```

### Nicknames (★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/05_List/05_List_​12.pdf)\
Solutions:

```python
#(dont worry, I generated them automatically :D)
full_names = ['Robert', 'William', 'James', 'John', 'Margaret', 'Edward', 'Sarah', 'Andrew', 'Anthony', 'Deborah']
nicknames = ['Dick', 'Bill', 'Jim', 'Jack', 'Peggy', 'Ed', 'Sally', 'Andy', 'Tony', 'Debbie']

for i in range(int(input())):
    name = input()
    if name in full_names:
        print(nicknames[full_names.index(name)])
    elif name in nicknames:
        print(full_names[nicknames.index(name)])
    else:
        print("Not found")
```

### Back n Front (★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/05_List/05_List_​13.pdf)\
Solutions:

```python
#annoyingly confusing question
data = []

#first set
for i in range(int(input())):
    if len(data) % 2 == 0:
        data.append(int(input()))
    else:
        data.insert(0, int(input())) 
    
#second set (the pdf doesnt tell you this but if it doesnt exist it will just be an empty string)
for number in input().split():
    if len(data) % 2 == 0:
        data.append(int(number))
    else:
        data.insert(0, int(number))

#third set
while True:
    number = input()
    if number == "-1":
        break

    if len(data) % 2 == 0:
        data.append(int(number))
    else:
        data.insert(0, int(number))

print(data)
```

### Peaks (★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/05_List/05_List_​14.pdf)\
Solutions:

```python
#this question is so peak
data = list(map(int, input().split()))
print(data)
count = 0

for i in range(1, len(data)-1):
    if data[i] > max(data[i-1], data[i+1]):
        count += 1

print(count)
```

### UniqueCount (★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/05_List/05_List_​15.pdf)\
Solutions:

```python
data = [int(i) for i in input().split()]
data.sort()

unique_numbers = [data[0]]
for number in data[1:]:
    #since our data is sorted
    #a number is new if it isnt the same as
    #the previous unique number
    if number != unique_numbers[-1]:
        unique_numbers.append(number)

print(len(unique_numbers))
print(unique_numbers[:10])
```

### Collatz (★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/05_List/05_List_​16.pdf)\
Solutions:

```python
sequence = [int(input())]

while sequence[-1] != 1:
    last_number = sequence[-1]
    if last_number % 2 == 0:
        sequence.append(last_number//2)
    else:
        sequence.append(3*last_number + 1)

print("->".join([str(n) for n in sequence][-15:]))
```

### Upgrade (★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/05_List/05_List_​21.pdf)\
Solutions:

```python
grade_rankings = ["F", "D", "D+", "C", "C+", "B", "B+", "A"]
student_ids = []
grades = []

while True:
    command = input().split()
    
    if command[0] == "q":
        break
    
    student_ids.append(command[0])
    grades.append(command[1])

for id in input().split():
    index = student_ids.index(id)
    grades[index] = grade_rankings[min(grade_rankings.index(grades[index])+1,7)]

print("\n".join([f"{student_ids[i]} {grades[i]}" for i in range(len(student_ids))]))
```

### Upgrade 2 (★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/05_List/05_List_​22.pdf)\
Solutions:

```python
grade_rankings = ["F", "D", "D+", "C", "C+", "B", "B+", "A"]
student_ids = []
grades = []

while True:
    command = input().split()
    
    if command[0] == "q":
        break
    
    student_ids.append(command[0])
    grades.append(command[1])

for id in input().split():
    index = student_ids.index(id)
    grades[index] = grade_rankings[min(grade_rankings.index(grades[index])+1,7)]

#you could do this alot easier using a sorting "key" parameter of .sort()
#alternative since you can arrange the data as a tuple (id, grade) then sort
#but im lazy so this is my solution
sorted_student_ids = sorted(student_ids)
for id in sorted_student_ids:
    print(id, grades[student_ids.index(id)])
```

### Third Closest (★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/05_List/05_List_​23.pdf)\
Solutions:

```python
points = []
for i in range(int(input())):
    x, y = [float(i) for i in input().split()]
    
    distance = (x**2+y**2)**(1/2)
    
    #distance, id, x, y
    points.append([distance, i + 1, x, y])

output_point = sorted(points)[2]

print(f"#{output_point[1]}: ({output_point[2]}, {output_point[3]})")
```

### Cut n Shuffle (★★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/05_List/05_List_​31.pdf)\
Solutions:

```python
#Solution Here
```

### QueueTicket (★★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/05_List/05_List_​32.pdf)\
Solutions:

```python
#Solution Here
```

