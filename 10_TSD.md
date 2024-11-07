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
#Solution Here
```

### GenreTotalPlaytime (★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/10_TSD/10_TSD_​23.pdf)\
Solutions:

```python
#Solution Here
```

### Cartoon (★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/10_TSD/10_TSD_​24.pdf)\
Solutions:

```python
#Solution Here
```

### Location Analysis (★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/10_TSD/10_TSD_​26.pdf)\
Solutions:

```python
#Solution Here
```

### Celebrity (★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/10_TSD/10_TSD_​27.pdf)\
Solutions:

```python
#Solution Here
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

