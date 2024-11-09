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
#Solution Here
```

### Student Info (★★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/10_TSD/10_TSD_​35.pdf)\
Solutions:

```python
#Solution Here
```

### Dept Selection (★★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/10_TSD/10_TSD_​37.pdf)\
Solutions:

```python
#Solution Here
```

### Sky Train (★★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/10_TSD/10_TSD_​38.pdf)\
Solutions:

```python
#Solution Here
```

