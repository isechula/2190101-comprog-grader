### Binary Adder (★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/06_Func/06_Func_​11.pdf)\
Solutions:

```python
#the never-ending urge to turn everthing into one liners
print(bin(sum([int(i, 2) for i in input().split()]))[2:])

#also a one liner :P
print(bin(sum(map(lambda y: int(y,2),input().split())))[2:])
```

### NextPrime (★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/06_Func/06_Func_​12.pdf)\

Given Template:

```python
def is_prime(n):
    if n <= 1:
        return False
    for k in range(2, int(n**0.5)+1):
        if n%k == 0:
            return False
    return True
```

Solutions:

```python
#(template is above this)

def next_prime(N):
    while True:
        #add first since N is exclusive
        N += 1

        if is_prime(N):
            return N

def next_twin_prime(N):
    #loop through all future primes, and check if the next prime differs by 2
    while True:
        N = next_prime(N)

        if next_prime(N) - N == 2:
            return (N, next_prime(N))

exec(input().strip())
```

```python
#method using python comparators
def next_prime(n):
    n+=1
    # means != True
    while not is_prime(n):
        n+=1
    return n

#method without using recursive
def next_twin_prime(n):
    n+=1
    while True:
        #stops the loop when the condition is met
        if is_prime(n) and is_prime(n+2):
            break
        n+=1
    return f"({n}, {n+2})"
```

### Function Call (★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/06_Func/06_Func_​21.pdf)\

Given Template:

```python
def read_answers():
    N = int(input())
    answers = []
    for k in range(N):
        sid, ans = input().split()
        answers.append([sid, ans])
    return answers

def marking(answer, solution):
    score = 0
    for i in range(len(answer)):
        if answer[i] == solution[i]:
            score += 1
    return score

def grading(score):
    g = [[80,"A"], [70,"B"],
         [60,"C"], [50,"D"]]
    for a,b in g:
        if score >= a:
            return b
    return "F"

def scoring(answers, solution):
	scores = []
	for sid, ans in answers:
		score = marking(ans, solution) / len(solution) * 100
		grade = grading(score)
		scores.append([sid, score, grade])
	return scores

def report(scores):
	for sid,sc,grade in scores:
		print(sid, sc, grade)

def sort(scores):
	x = []
	for sid,score,grade in scores:
		x.append([score, sid, grade])
	x.sort()
	for i in range(len(x)):
		scores[i] = [x[i][1], x[i][0], x[i][2]]
```

Solutions:

```python
answer_key = input()
answers = read_answers()
scores = scoring(answers, answer_key)
sort(scores)
report(scores[::-1])
```

```python
#from the return values we can replace declaring variables with the function literals
r = scoring(solution=input(),answers=read_answers())
sort(r)
report(reversed(r))
```

### Distance (★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/06_Func/06_Func_​22.pdf)\
Solutions:

```python
#Solution Here
```

### FourFunctions (★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/06_Func/06_Func_​23.pdf)\
Solutions:

```python
#Solution Here
```

### Refactor (★★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/06_Func/06_Func_​31.pdf)\
Solutions:

```python
#Solution Here
```
