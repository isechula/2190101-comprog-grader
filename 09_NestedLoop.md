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
        for j in range(2*i,upper_bound+1,i):
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
#Solution Here
```

### Pythagorean Triple (★★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/09_NestedLoop/09_NestedLoop_​31.pdf)\
Solutions:

```python
#Solution Here
```

### FirstFit BestFit (★★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/09_NestedList/09_NestedList_​32.pdf)\
Solutions:

```python
#Solution Here
```

### Fill In Numbers (★★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/09_NestedList/09_NestedList_​34.pdf)\
Solutions:

```python
#Solution Here
```

