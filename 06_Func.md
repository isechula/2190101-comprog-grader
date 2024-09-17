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
def distance1(x1, y1, x2, y2):
    dis = ((x1 - x2)**2 + (y1 - y2)**2)**0.5
    return dis

def distance2(p1, p2):
    dis = ((p1[0] - p2[0])**2 + (p1[1] - p2[1])**2)**0.5
    return dis

def distance3(c1, c2):
    dis = distance2(c1, c2)
    overlap = (c1[2]+c2[2]) >= dis
    return dis,overlap

def perimeter(points):
    per = 0
    for i in range(len(points)-1):
        per += distance2(points[i], points[i+1])
    per += distance2(points[-1], points[0])
    return per

exec(input().strip())
```

```python
def perimeter(points):
    total = 0
    #since points[-1] is the last point
    #i can avoid having to do an edge case
    for i in range(len(points)):
        total += distance2(points[i - 1], points[i])
    return total
```

### FourFunctions (★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/06_Func/06_Func_​23.pdf)\
Solutions:

```python
def make_int_list(x):
    return list(map(int,x.split()))
	# receive x as string input and convert them into list

def is_odd(e):
    return e % 2 == 1
	# return true if e is an odd number; otherwise, return false

def odd_list(alist):
    olist = list()
    for e in alist:
        if is_odd(e):
            olist.append(e)
    return olist
    # return a list which is like alist, but contains only odd numbers


def sum_square(alist):
    net = 0
    for e in alist:
        net += e**2
    return net
    # return a sum of square of each number in alist
    
exec(input().strip())
```

```python
#a few alternative solutions:
def is_odd(e):
    #if you like being fun:
    return not not e & 1

def sum_square(alist):
    return sum(i * i for i in alist)
```

### Refactor (★★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/06_Func/06_Func_​31.pdf)\
Solutions:

```python
mname = ["Jan", "Feb","Mar","Apr","May","Jun","Jul","Aug","Sep","Oct","Nov","Dec"]

def read_date():
    # read the day, month, and year separated by space.
    # return a list containing the day, month, and year.
    date1 = input().split()
    d1 = int(date1[0])
    m1 = mname.index(date1[1][:3]) + 1
    y1 = int(date1[2])
    
    return [d1,m1,y1]

def zodiac(d1,m1):
    # return the zodiac sign given the day (d) and month (m)
    if d1 >= 22 and m1==3 or d1 <=21 and m1==4 : z1 = "Aries"
    elif d1 >= 22 and m1==4 or d1 <=21 and m1==5 : z1 = "Taurus"
    elif d1 >= 22 and m1==5 or d1 <=21 and m1==6 : z1 = "Gemini"
    elif d1 >= 22 and m1==6 or d1 <=21 and m1==7 : z1 = "Cancer"
    elif d1 >= 22 and m1==7 or d1 <=21 and m1==8 : z1 = "Leo"
    elif d1 >= 22 and m1==8 or d1 <=21 and m1==9 : z1 = "Virgo"
    elif d1 >= 22 and m1==9 or d1 <=21 and m1==10 : z1 = "Libra"
    elif d1 >= 22 and m1==10 or d1 <=21 and m1==11 : z1 = "Scorpio"
    elif d1 >= 22 and m1==11 or d1 <=21 and m1==12 : z1 = "Sagittarius"
    elif d1 >= 22 and m1==12 or d1 <=20 and m1==1 : z1 = "Capricorn"
    elif d1 >= 21 and m1==1 or d1 <=20 and m1==2 : z1 = "Aquarius"
    elif d1 >= 21 and m1==2 or d1 <=21 and m1==3 : z1 = "Pisces"
    
    return z1


def days_in_feb(y):
    # return the number of days in February of the given year (y).
    days_in_feb = 28
    if y % 400 == 0 or y % 100 != 0 and y%4 == 0:
        days_in_feb = 29
        
    return days_in_feb


def days_in_month(m,y):
    # return the number of days	 given the month (m) and year (y)
    days_in_feb = 28
    if y % 400 == 0 or y % 100 != 0 and y%4 == 0 :
        days_in_feb = 29

    days_in_m = 31
    if m==4 or m==6 or m==9 or m==11 :
         days_in_m = 30
    elif m==2 :
         days_in_m = days_in_feb
         
    return days_in_m


def days_in_between(d1,m1,y1,d2,m2,y2):
    # return the number of days from d1, m1, y1 to d2, m2, y2.
    days_in_feb1 = days_in_feb(y1)
    days_in_feb2 = days_in_feb(y2)
    days_in_m1 = days_in_month(m1,y1)
        
    days = 0
    if m1 < 12 : days += 31
    if m1 < 11 : days += 30
    if m1 < 10 : days += 31
    if m1 < 9 : days += 30
    if m1 < 8 : days += 31
    if m1 < 7 : days += 31
    if m1 < 6 : days += 30
    if m1 < 5 : days += 31
    if m1 < 4 : days += 30
    if m1 < 3 : days += 31
    if m1 < 2 : days += days_in_feb1
    if m2 > 1 : days += 31
    if m2 > 2 : days += days_in_feb2
    if m2 > 3 : days += 31
    if m2 > 4 : days += 30
    if m2 > 5 : days += 31
    if m2 > 6 : days += 30
    if m2 > 7 : days += 31
    if m2 > 8 : days += 31
    if m2 > 9 : days += 30
    if m2 > 10 : days += 31
    if m2 > 11 : days += 30
    days += (days_in_m1 - d1 + 1) + int((y2 - y1 - 1)*365.25) + (d2 - 1)
    
    return days


def main() :
    d1,m1,y1 = read_date()
    d2,m2,y2 = read_date()
    print(zodiac(d1,m1), zodiac(d2,m2))
    print(days_in_between(d1,m1,y1,d2,m2,y2))
    # display the zodiac sign of d1, m1, y1 and d2, m2, y2 on the same line, separated by space.
    # display the number of days from d1, m1, y1 and d2, m2, y2.

exec(input().strip())
```
