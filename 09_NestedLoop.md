### Dedent (★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/09_NestedLoop/09_NestedLoop_​11.pdf)\
Solutions:

```python
def count_periods(line):
    count = 0
    for letter in line:
        if letter != ".":
            return count
        count += 1
    return count

lines = int(input())

for i in range(lines):
    line = input()
    print(line[count_periods(line)//2:])
```

### Factorization (★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/09_NestedLoop/09_NestedLoop_​21.pdf)\
Solutions:

```python
#you can just do a simpler method of generating primes
#(but this solution is cool 😎)
#https://en.wikipedia.org/wiki/Sieve_of_Eratosthenes
def eratosthenes(upper_bound):
    is_primes = [True]*(upper_bound-1)
    
    i = 2
    while i**2 <= upper_bound:
        if not is_primes[i-2]:
            i += 1
            continue
        for j in range(i**2,upper_bound+1,i):
            is_primes[j-2] = False
        i += 1
    prime_numbers = []
    for index, is_prime in enumerate(is_primes):
        if is_prime:
            prime_numbers.append(index + 2)
    return prime_numbers

def factor(number):
    #a loose upperbound for the largest prime factor of a number is
    #the floor of n/2 for even numbers and n/3 for odd numbers
    primes = eratosthenes(round((number/2 if number % 2 == 0 else number/3) - .5))
    factors = []
    for prime in primes:
        count = 0
        while number % prime == 0:
            count += 1
            number //= prime
        if count > 0:
            factors.append([prime, count])
    
    #special case for prime numbers
    if factors == []:
        return [[number, 1]]
    return factors

exec(input().strip())
```

### Matrix (★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/09_NestedList/09_NestedList_​22.pdf)\
Given:
```python
def read_matrix():
    m = []
    nrows = int(input())
    for k in range(nrows):
        x = input().split()
        r = []
        for e in x:
            r.append(float(e))
        m.append(r)
    return m
```

Solutions:

```python
#pdf test cases use "mul_c/mul" but grader uses "mult_c/mult"
def mult_c(constant, matrix):
    output = []
    for row in matrix:
        new_row = []
        for number in row:
            new_row.append(number * constant)
        output.append(new_row)
    return output

def mult(A, B):
    output = []
    for row in A:
        new_row = []
        
        columns = []
        #generate columns
        for i in range(len(B[0])):
            column = []
            for j in range(len(B)):
                column.append(B[j][i])
            columns.append(column)
        
        #this part could go into the column generator
        #but this is more readable
        for column in columns:
            total = 0
            for i in range(len(row)):
                total += row[i]*column[i]
            new_row.append(total)
        output.append(new_row)
            
    return output
            
exec(input().strip())
```

### Tiling Puzzle (★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/09_NestedList/09_NestedList_​25.pdf)\
Solutions:

```python
#https://2190101.nattee.net/problems/926/get_statement/09_MoreDC_25.pdf
def row_number(t, e):
    for index, row in enumerate(t):
        if e in row:
            return index

def flatten(t):
    output = []
    for row in t:
        for num in row:
            if num != 0:
                output.append(num)
    return output

def inversions(x):
    count = 0
    for i in range(len(x)):
        for j in range(i, len(x)):
            if x[i] > x[j]:
                count += 1
    return(count)

def solvable(t):
    if len(t) % 2 == 0:
        #one liner possible (but unreadable)
        #return (inversions(flatten(t)) % 2 == 0) ^ (row_number(t, 0) % 2 == 0)
        # ^ is xor
        if inversions(flatten(t)) % 2 == 0:
            return row_number(t, 0) % 2 == 1
        else:
            return row_number(t, 0) % 2 == 0
    else:
        return inversions(flatten(t)) % 2 == 0
        
exec(input().strip())

```

### Pythagorean Triple (★★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/09_NestedLoop/09_NestedLoop_​31.pdf)\
Solutions:

```python
def gcd(a, b):
 while b != 0:
     a, b = b, a%b
 return a

def is_coprime(a, b, c):
    return 1 in [gcd(a,b), gcd(a,c), gcd(b,c)]

def primitive_Pythagorean_triples(max_len):
    answers = []
    for a in range(1, max_len+1):
        for b in range(a, max_len+1):
            for c in range(b, max_len+1):
                if not is_coprime(a,b,c):
                    continue
                if a**2 + b**2 == c**2:
                    #question wants the answers
                    #sorted by c, a then b
                    answers.append([c, a, b])
    #undo shuffling done from sorting
    return [[i[1],i[2],i[0]] for i in sorted(answers)]

exec(input().strip())
```

### FirstFit BestFit (★★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/09_NestedList/09_NestedList_​32.pdf)\
Solutions:

```python
#since this can be used for both
#first fit and best fit
def first_fit_index(L, e):
    for index, sub_list in enumerate(L):
        if sum(sub_list) + e <= 100:
            return index

def first_fit(L, e):
    index = first_fit_index(L,e)
    if index != None:
        L[index].append(e)
    else:
        L.append([e])

def best_fit(L, e):
    #set initial value to first fit
    initial_index = first_fit_index(L, e)
    best_index = initial_index
    
    #if no first fit is found, add a new sub list instead
    if best_index == None:
        L.append([e])
        return
    
    best_difference = 100 - (sum(L[best_index]) + e)
    
    for index, sub_list in enumerate(L[best_index + 1:]):
        difference = 100 - (sum(sub_list) + e)
        if difference < best_difference and difference >= 0:
            best_index, best_difference = index + initial_index + 1, difference
    
    L[best_index].append(e)
    
def partition_FF(D):
    #to avoid mutating the original list
    D = D.copy()
    
    partitioned = []
    while len(D) > 0:
        first_fit(partitioned, D.pop(0))
    
    return partitioned

def partition_BF(D):
    #to avoid mutating the original list
    D = D.copy()
    
    partitioned = []
    while len(D) > 0:
        best_fit(partitioned, D.pop(0))
    
    return partitioned

exec(input().strip())
```

### Fill In Numbers (★★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/09_NestedList/09_NestedList_​34.pdf)\
Solutions:

```python
def pattern1(nrows, ncols):
    output = []
    for i in range(nrows):
        row = []
        for j in range(ncols):
            row.append(j + i*ncols + 1)
        output.append(row)
    return output

def pattern2(nrows, ncols):
    output = []
    for i in range(nrows):
        row = []
        for j in range(ncols):
            row.append(i + j*nrows + 1)
        output.append(row)
    return output

def pattern3(n):
    output = []
    num = 1
    for i in range(n):
        row = []
        for j in range(n-i):
            #a formula is possible but this is easier and more readable
            row.append(num)
            num += 1
        output.append([0]*i + row)
    return output

#this solution is easy to understand
#i had shorter solution that was formulaic
#but it was hard to understand
#(it relies on the arithmetic sequence-like pattern)
def pattern4(n):
    #generates a "triangle" in the form
    #[[1], [2,3], ...]
    triangle = []
    num = 1
    for i in range(n):
        triangle.append([])
        for j in range(i+1):
            triangle[-1].append(num)
            num += 1
    
    #add every last number in the triangle
    #then every second last
    #and so on
    output = []
    for i in range(n):
        row = []
        for j in range(i,n):
            row.append(triangle[j][-(i+1)])
        output.append([0]*i+row)
    return output

#again a formulaic solution is possible
#although here its actually pretty simple too
#but i like this solution which i thought up for
#pattern6 so much that im replacing my pattern4 and 5
#with it
def pattern5(n):
    #generates a "triangle" in the form
    #[[1,2,3,4,...,n], [n+1,n+2,...], ...]
    triangle = []
    num = 1
    for i in range(n):
        triangle.append([])
        for j in range(n-i):
            triangle[-1].append(num)
            num += 1
    
    #add every first number in the triangle
    #then every second
    #and so on
    output = []
    for i in range(n):
        row = []
        for j in range(n-i):
            row.append(triangle[j][i])
        output.append([0]*i+row)
    return output

#same as solution 5 but reverse every second row
def pattern6(n):
    #generates a "triangle" in the form
    #[[1,2,3,4,...,n], [n+1,n+2,...], ...]
    triangle = []
    num = 1
    for i in range(n):
        triangle.append([])
        for j in range(n-i):
            triangle[-1].append(num)
            num += 1
        #reverse every second row
        if i % 2 == 1:
            triangle[-1] = triangle[-1][::-1]
    
    #add every first number in the triangle
    #then every second
    #and so on
    output = []
    for i in range(n):
        row = []
        for j in range(n-i):
            row.append(triangle[j][i])
        output.append([0]*i+row)
    return output
exec(input().strip())
```

