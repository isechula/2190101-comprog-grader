### Complex Number (★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/12_Class/12_Class_​21.pdf)\
Solutions:

```python
class Complex:
    def __init__(self, a, b):
        self.a = a
        self.b = b
    
    def __str__(self):        
        if self.b == 1:
            imaginary = "i"
        elif self.b == -1:
            imaginary = "-i"
        else:
            imaginary = f"{self.b}i"
        
        #cases where both are shown
        if self.a != 0 and self.b != 0:
            if self.b < 0:
                return f"{self.a}{imaginary}"
            elif self.b > 0:
                return f"{self.a}+{imaginary}"
        #cases where only 1 is shown
        else:
            if self.a != 0:
                return f"{self.a}"
            elif self.b != 0:
                return f"{imaginary}"
            #edge case for 0 + 0i
            else:
                return "0"
    
    def __add__(self, other):
        return Complex(self.a + other.a, self.b + other.b)
    
    def __mul__(self, other):
        return Complex(self.a * other.a - self.b * other.b, self.a * other.b + self.b * other.a)
    
    def __truediv__(self, other):
        real = (self.a * other.a + self.b * other.b)
        imaginary = (-self.a * other.b + self.b * other.a)
        divisor = (other.a**2 + other.b**2)
        return Complex(real/divisor, imaginary/divisor)

t, a, b, c, d = [int(x) for x in input().split()]
c1 = Complex(a,b)
c2 = Complex(c,d)
if t == 1: print(c1)
elif t == 2: print(c2)
elif t == 3: print(c1+c2)
elif t == 4: print(c1*c2)
else: print(c1/c2)
```

### Card (★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/12_Class/12_Class_​22.pdf)\
Solutions:

```python
class Card:
    sorted_values = ["3", "4", "5", "6", "7", "8", "9", "10", "J", "Q", "K", "A", "2"]
    sorted_suits = ["club", "diamond", "heart", "spade"]
    
    def __init__(self, value, suit):
        self.value = value
        self.suit = suit
        
    def __str__(self):
        return f"({self.value} {self.suit})"
    
    def getScore(self):
        if self.value == "A":
            return 1
        elif self.value in ["J", "Q", "K"]:
            return 10
        else:
            return int(self.value)
        
    def sum(self, other):
        return (self.getScore() + other.getScore()) % 10
        
    def __lt__(self, other):
        if self.value != other.value:
            return Card.sorted_values.index(self.value) < Card.sorted_values.index(other.value)
        else:
            return Card.sorted_suits.index(self.suit) < Card.sorted_suits.index(other.suit)
            
n = int(input())
cards = []
for i in range(n):
    value, suit = input().split()
    cards.append(Card(value, suit))
for i in range(n):
    print(cards[i].getScore())
print("----------")
for i in range(n-1):
    print(Card.sum(cards[i], cards[i+1]))
print("----------")
cards.sort()
for i in range(n):
    print(cards[i]) 
```

### Next Card (★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/12_Class/12_Class_​23.pdf)\
Solutions:

```python
class Card:
    sorted_values = ["3", "4", "5", "6", "7", "8", "9", "10", "J", "Q", "K", "A", "2"]
    sorted_suits = ["club", "diamond", "heart", "spade"]
    def __init__(self, value, suit):
        self.value = value
        self.suit = suit
        
    def __str__(self):
        return f"({self.value} {self.suit})"
    
    def next1(self):
        #if suit isnt max increment suit
        if self.suit != "spade":
            suit = self.sorted_suits[self.sorted_suits.index(self.suit) + 1]
            return Card(self.value, suit)
        else:
            suit = "club"
        
        #if value isnt max increment value
        if self.value != "2":
            value = self.sorted_values[self.sorted_values.index(self.value) + 1]
            return Card(value, suit)
        
        #if both are max return the lowest value
        return Card("3", "club")
    
    def next2(self):
        next_card = self.next1()
        self.value = next_card.value
        self.suit = next_card.suit

n = int(input())
cards = []
for i in range(n):
    value, suit = input().split()
    cards.append(Card(value, suit))
for i in range(n):
    print(cards[i].next1())
print("----------")
for i in range(n):
    print(cards[i])
print("----------")
for i in range(n):
    cards[i].next2()
    cards[i].next2()
    print(cards[i])
```

### Point in Rect (★★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/12_Class/12_Class_​31.pdf)\
Solutions:

```python
class Point:
    def __init__(self, x, y):
        self.x = x
        self.y = y
    def __str__(self):
        return f"({self.x},{self.y})"

class Rect:
    def __init__(self, p1, p2):
        self.lowerleft = p1
        self.upperright = p2
    
    def area(self):
        length = self.upperright.x - self.lowerleft.x
        height = self.upperright.y - self.lowerleft.y
        return length*height
    
    def contains(self, p):
        if p.x < self.lowerleft.x: return False
        if p.y < self.lowerleft.y: return False
        if p.x > self.upperright.x: return False
        if p.y > self.upperright.y: return False
        return True

x1,y1,x2,y2 = [int(e) for e in input().split()]
lowerleft = Point(x1,y1)
upperright = Point(x2,y2)
rect = Rect(lowerleft, upperright)
print(rect.area())
m = int(input())
for i in range(m):
    x,y = [int(e) for e in input().split()]
    p = Point(x,y)
    print(rect.contains(p))

```

### Rect Sorted by Area (★★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/12_Class/12_Class_​32.pdf)\
Solutions:

```python
class Point:
    def __init__(self, x, y):
        self.x = x
        self.y = y
    def __str__(self):
        return f"({self.x},{self.y})"

class Rect:
    def __init__(self, p1, p2):
        self.lowerleft = p1
        self.upperright = p2
    
    def __str__(self):
        return f"{self.lowerleft}-{self.upperright}"
    def area(self):
        length = self.upperright.x - self.lowerleft.x
        height = self.upperright.y - self.lowerleft.y
        return length*height
    
    def __lt__(self, other):
        return self.area() < other.area()

n = int(input())
rects = []
for i in range(n):
    x1,y1,x2,y2 = [int(e) for e in input().split()]
    rects.append(Rect(Point(x1,y1), Point(x2,y2)))
rects.sort()
for i in range(n):
    print(rects[i])

```

### Piggy Bank 1 (★★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/12_Class/12_Class_​33.pdf)\
Solutions:

```python
class piggybank:
    def __init__(self):
        #initialize coins dict
        self.coins = {1:0, 2:0, 5:0, 10:0}
        
    def add1(self, n):
        self.coins[1] += n
    def add2(self, n):
        self.coins[2] += n
    def add5(self, n):
        self.coins[5] += n
    def add10(self, n):
        self.coins[10] += n
    
    def __int__(self):
        total = 0
        for value, amount in self.coins.items():
            total += value * amount
        return total
    
    def __lt__(self, other):
        return int(self) < int(other)
    
    def __str__(self):
        return str(self.coins).replace(": ", ":")
    
cmd1 = input().split(';')
cmd2 = input().split(';')
p1 = piggybank() ; p2 = piggybank()
for c in cmd1: eval(c)
for c in cmd2: eval(c)
```

### Piggy Bank 2 (★★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/12_Class/12_Class_​34.pdf)\
Solutions:

```python
class piggybank:
    def __init__(self):
        #initialize coins dict
        self.coins = {}
        self.total_coins = 0
        
    def add(self, v, n):
        if self.total_coins + n > 100:
            return False
        self.total_coins += n
        
        v = float(v)
        
        if v in self.coins:
            self.coins[v] += n
        else:
            self.coins[v] = n
            
        return True
        
    def __float__(self):
        total = 0.
        for value, amount in self.coins.items():
            total += value * amount
        return total
    
    def __str__(self):
        middle = ", ".join([f"{key}:{self.coins[key]}" for key in sorted(self.coins.keys())])
        return "{" + middle + "}"

cmd1 = input().split(';')
cmd2 = input().split(';')
p1 = piggybank(); p2 = piggybank()
for c in cmd1: eval(c)
for c in cmd2: eval(c)
```

### Roman Numeral (★★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/12_Class/12_Class_​35.pdf)\
Solutions:

```python
class roman:
    values = {"I":1, "IV":4, "V":5, "IX":9, "X":10, "XL":40, "L":50, "XC":90, "C":100, "CD":400, "D":500, "CM":900, "M":1000}
    def __init__(self, r):
        #special case for single letters as this algorithm
        #only works for more than 1 letter
        if len(r) == 1:
            self.value = roman.values[r]
            return
        
        #process the 2 long special cases
        #by checking pairs of letters in r
        #if the pair is a special case, add that special case
        #and move onto the next pair
        #if pair isnt a special case add value of first number in pair
        #then check the next pair
        value = 0
        previous = r[0]
        special_cases = ["IV", "IX", "XL", "XC", "CD", "CM"]
        index = 1
        while index < len(r):
            letter = r[index]
            if previous + letter in special_cases:
                value += roman.values[previous + letter] 
                index += 2
                if index < len(r):
                    previous = r[index-1]
                #edge case for when there is 1 last letter following a special case
                elif index - 1 < len(r):
                    value += roman.values[r[index-1]]
                
            else:
                value += roman.values[previous]
                previous = letter
                index += 1
                #also add current letter's value on last iteration
                if index >= len(r):
                    value += roman.values[letter]

        self.value = value
            
            
    def __lt__(self, rhs):
        return self.value < rhs.value
    
    #add up the "tokens" prioritizing the larger "tokens"
    #until the value is reached
    def __str__(self):
        output = ""
        current_value = 0
        while current_value < self.value:
            for key, value in list(roman.values.items())[::-1]:
                if value + current_value <= self.value:
                    output += key
                    current_value += value
                    break
        return output
    def __int__(self):
        return self.value
    def __add__(self, rhs):
        #i didnt notice they wanted me to return the value as the roman() class
        #since i chose to have my roman class just have a value variable
        #imma do something a bit hacky
        output = roman("I")
        output.value =self.value + rhs.value
        return output

t, r1, r2 = input().split()
a = roman(r1); b = roman(r2)
if t == '1' : print(a < b)
elif t == '2' : print(int(a),int(b))
elif t == '3' : print(str(a),str(b))
elif t == '4' : print(int(a + b))
else : print(str(a + b))

```

