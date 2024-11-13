### Indexing and Slicing (★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/11_NumPy/11_NumPy_​11.pdf)\
Solutions:

```python
import numpy as np

def get_column_from_bottom_to_top( A, c ):
    return A[::-1,c]
def get_odd_rows( A ):
    return A[1::2,:]
def get_even_column_last_row( A ):
    return A[:,::2][-1]
def get_diagonal1( A ):
    return A.diagonal()
def get_diagonal2( A ):
    return A[:, ::-1].diagonal()

exec(input().strip())
```

### Scalar and Array (★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/11_NumPy/11_NumPy_​12.pdf)\
Solutions:

```python
import numpy as np

def toCelsius(f):
    return (f-32) * 5/9

def BMI (wh):
    return wh[:,0]/((wh[:,1]/100)**2)

def distanceTo(p, Points):
    vector = Points - p
    return (vector[:,0]**2 + vector[:,1]**2)**(1/2)

exec(input().strip())
```

### Logistic Regression (★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/11_NumPy/11_NumPy_​13.pdf)\
Solutions:

```python
import numpy as np

def p(x):
    return 1/(1 + np.exp(3.98 - 0.1 * x[:,0] - 0.5*x[:,1]))

exec(input().strip())
```

### Slicing and Element wise Op. (★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/11_NumPy/11_NumPy_​21.pdf)\
Solutions:

```python
import numpy as np

def sum_2_rows(M):
    return M[::2,:] + M[1::2,:]

def sum_left_right(M):
    columns = M.shape[1]
    return M[:,:columns//2] + M[:,columns//2:]

def sum_upper_lower(M):
    rows = M.shape[0]
    return M[:rows//2,:] + M[rows//2:, :]

def sum_4_quadrants(M):
    rows, columns = M.shape
    return M[:rows//2,:columns//2] + M[rows//2:,:columns//2] + M[:rows//2,columns//2:] + M[rows//2:,columns//2:]

def sum_4_cells(M):
    return M[::2,::2] + M[1::2,::2] + M[::2,1::2] + M[1::2,1::2]

def count_leap_years(years):
    christian_years = (years - 543)
    leap_years = (((christian_years % 4 == 0) & ~(christian_years % 100 == 0)) | (christian_years % 400 == 0))
    return len(leap_years[leap_years])

exec(input().strip())
```

### Outer Product (★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/11_NumPy/11_NumPy_​22.pdf)\
Solutions:

```python
import numpy as np

def mult_table(nrows, ncols):
    row = np.arange(1, nrows + 1)
    column = np.arange(1, ncols + 1)
    return np.outer(row, column)

exec(input().strip())
```

### Lower than Mean (★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/11_NumPy/11_NumPy_​23.pdf)\
Solutions:

```python
import numpy as np

def read_data():
    weight = np.array([float(i) for i in input().split()])
    count = int(input())
    data = np.ndarray((count, 4), int)
    for i in range(count):
        data[i] = [int(j) for j in input().split()]
    return weight, data
    
def report_lower_than_mean(weight, data):
    weighted_mean = np.mean(data[:,1:]*weight)
    below_mean = data[np.mean(data[:,1:]*weight, axis = 1) < weighted_mean]
    if len(below_mean) > 0:
        print(", ".join([str(i) for i in below_mean[:,0].T]))
    else:
        print("None")

exec(input().strip())
```

### Peak Indexes (★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/11_NumPy/11_NumPy_​24.pdf)\
Solutions:

```python
import numpy as np
def peak_indexes(x):
    #[1,2,3,4,5,6]
    #right_number [3,4,5,6]
    #middle [2,3,4,5]
    #left_number [1,2,3,4]
    #compare if middle > left and right and if so it is a peak
    #shift end indexes up by one to account for slicing
    right_number = x[2:]
    left_number = x[:-2]
    middle = x[1:-1]
    
    peaks = (middle > right_number) & (middle > left_number)
    return np.arange(1,len(peaks)+1)[peaks]

def main():
    d = np.array([float(e) for e in input().split()])
    pos = peak_indexes(np.array(d))
    if len(pos) > 0:
        print(", ".join([str(e) for e in pos]))
    else:
        print("No peaks")
exec(input().strip())

```

