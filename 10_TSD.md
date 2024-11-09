### Union Intersection (★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/10_TSD/10_TSD_​12.pdf)\
Solutions:

```python
union = intersect = set()
for i in range(int(input())):
    if i == 0:
        union = intersect = set(input().split())
        continue
    current = set(input().split())
    union = union | current
    intersect = intersect & current
print(f'{len(union)}\n{len(intersect)}')
```

### Winner (★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/10_TSD/10_TSD_​13.pdf)\
Solutions:

```python
teams = []
for i in range(int(input())):
    teams.append(input().split())
win, lose = zip(*teams)
print(sorted(list(set(win) - set(lose))))
```

### Database (★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/10_TSD/10_TSD_​14.pdf)\
Solutions:

```python
courses, teachers = {}, {}

#courses.txt
for line in open(input().strip(), "r").readlines():
    key, value = line.strip().split(", ")
    courses[key] = value

#teachers.txt
for line in open(input().strip(), "r").readlines():
    key, value = line.strip().split(", ")
    teachers[key] = value

#database.txt
for pair in open(input().strip(), "r").readlines():
    course, teacher = pair.strip().split(", ")
    
    if course in courses and teacher in teachers:
        print(f"{courses[course]}, {teachers[teacher]}")
    else:
        print("record error")
              
```

### GenreTotalPlaytime (★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/10_TSD/10_TSD_​23.pdf)\
Solutions:

```python
genres = {}

def add_time(t1, t2):
    m1, s1 = t1[0], t1[1]
    m2, s2 = t2[0], t2[1]
    
    m = m1 + m2
    s = s1 + s2
    
    if s >= 60:
        s -= 60
        m += 1
    
    return [m, s]
    
for i in range(int(input())):
    song_data = input().split(",")
    genre, time = song_data[2].strip(), song_data[3].strip()
    
    parsed_time = [int(i) for i in time.split(":")]
    if genre in genres:
        genres[genre] = add_time(genres[genre], parsed_time)
    else:
        genres[genre] = parsed_time

#sort the list [[-min, -sec], name]
#to get sort descending by time and ascending by name
top_3 = sorted([[[-genres[key][0], -genres[key][1]], key] for key in genres])[:3]
for top in top_3:
    print(f"{top[1]} --> {-top[0][0]}:{-top[0][1]:02d}")
```

### Cartoon (★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/10_TSD/10_TSD_​24.pdf)\
Solutions:

```python
animals = {}
while True:
    data = input()
    if data == "q":
        for animal, names in animals.items():
            print(f"{animal}: {', '.join(names)}")
        break
    
    name, animal = data.split(", ")
    
    if animal in animals:
        animals[animal].append(name)
    else:
        animals[animal] = [name]
```

### Location Analysis (★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/10_TSD/10_TSD_​26.pdf)\
Solutions:

```python
users = {}

for i in range(int(input())):
    user, locations = input().split(":")
    locations = locations.strip().split(", ")
    
    users[user] = locations

search_user = input()
matches = []
for user, locations in users.items():
    if user == search_user:
        continue
    
    for location in locations:
        if location in users[search_user]:
            matches.append(user)
            break

if matches == []:
    print("Not Found")
else:
    print(*matches, sep="\n")
```

### Celebrity (★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/10_TSD/10_TSD_​27.pdf)\
Solutions:

```python
def knows(R,x,y):
    return y in R[x]

def is_celeb(R,x):

    #if x knows someone other than themselves
    if len(R[x] - {x}) > 0:
        return False
    
    #if someone doesnt know x
    for person, relations in R.items():
        if person == x:
            continue
        if x not in relations:
            return False
        
    return True

def find_celeb(R):
    for person in R:
        if is_celeb(R, person):
            return person
        
def read_relations():
    R = {}
    while True:
        data = input()
        if data == "q":
            break
        person1, person2 = data.split()
        if person1 in R:
            R[person1].add(person2)
        else:
            R[person1] = set([person2])
            
        if person2 not in R:
            R[person2] = set()
    
    return R

def main():
    R = read_relations()
    c= find_celeb(R)
    if c == None:
        print('Not Found')
    else:
        print(c)
    
exec(input().strip())
```

### Polynomial (★★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/10_TSD/10_TSD_​33.pdf)\
Solutions:

```python
#converts a dict of power -> coef into
#a tuple list [(coef, power)]
def dict_to_poly(coefs):
    output = []
    for power, coef in coefs.items():
        if coef != 0:
            output.append([-power, coef])
    return [(i[1],-i[0]) for i in sorted(output)]

def add_poly(p1,p2):
    coefs = {}
    for terms in [*p1, *p2]:
        if terms[1] in coefs:
            coefs[terms[1]] += terms[0]
        else:
            coefs[terms[1]] = terms[0]
            
    return dict_to_poly(coefs)

def mult_poly(p1,p2):
    coefs = {}
    
    for terms_1 in p1:
        for terms_2 in p2:
            power = terms_1[1] + terms_2[1]
            coef = terms_1[0] * terms_2[0]
            
            if power in coefs:
                coefs[power] += coef
            else:
                coefs[power] = coef
    
    return dict_to_poly(coefs)

for i in range(3):
    exec(input().strip())
```

### Student Info (★★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/10_TSD/10_TSD_​35.pdf)\
Solutions:

```python
students = []

for i in range(int(input())):
    students.append(input().split())

conditions = input().split()
matches = []
for student in students:
    match = True
    for condition in conditions:
        #grader doesnt want name matches
        if condition not in student[1:]:
            match = False
            break
        
    if match:
        matches.append(student)

if matches == []:
    print("Not Found")
else:
    print(*sorted([" ".join(i) for i in matches]), sep="\n")
```

### Dept Selection (★★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/10_TSD/10_TSD_​37.pdf)\
Solutions:

```python
slots = {}

for i in range(int(input())):
    faculty, count = input().split()
    if faculty in slots:
        slots[faculty] += count
    else:
        slots[faculty] = int(count)

students = []
for i in range(int(input())):
    student_info = input().split()
    #-score, id, [preferences]
    students.append([-float(student_info[1]), student_info[0], student_info[2:]])

results = []
for student in sorted(students):
    for faculty in student[2]:
        if slots.get(faculty, 0) > 0:
            results.append(f"{student[1]} {faculty}")
            slots[faculty] -= 1
            break

print(*sorted(results), sep="\n")
```

### Sky Train (★★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/10_TSD/10_TSD_​38.pdf)\
Solutions:

```python
connections = {}

while True:
    data = input().split()
    if len(data) == 1:
        break
    
    if data[0] in connections:
        connections[data[0]].append(data[1])
    else:
        connections[data[0]] = [data[1]]
    #connections are symmetric
    if data[1] in connections:
        connections[data[1]].append(data[0])
    else:
        connections[data[1]] = [data[0]]
    
    

valid_connections = set([data[0]])
for connection in connections.get(data[0], []):
    valid_connections.add(connection)
    for sub_connection in connections.get(connection, []):
        valid_connections.add(sub_connection)

print(*sorted(list(valid_connections)), sep="\n")
```

