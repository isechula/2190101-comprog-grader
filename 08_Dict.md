### Reverse n Keys (★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/08_Dict/08_Dict_​11.pdf)\
Solutions:

```python
#at time of writing there are 3 test cases and none of them test the keys() function lol
def keys(dictionary, target_value):
    output = []
    for key in dictionary:
        if dictionary[key] == target_value:
            output.append(key)
    return output

def reverse(dictionary):
    output = {}
    for key in dictionary:
        output[dictionary[key]] = key
    return output

exec(input().strip())
```

### Nicknames (★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/08_Dict/08_Dict_​12.pdf)\
Solutions:

```python
names = {}
for i in range(int(input())):
    first_name, nickname = input().strip().split()
    names[first_name] = nickname
    names[nickname] = first_name

for i in range(int(input())):
    print(names.get(input().strip(), "Not found"))
```

### Char Count (★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/08_Dict/08_Dict_​21.pdf)\
Solutions:

```python
letters = {}
for letter in input().lower():
    if not letter.isalpha():
        continue

    if letter in letters:
        letters[letter] += 1
    else:
        letters[letter] = 1

#i feel magical
#basically turn the dict an array with the form [[-count1, letter1], ...]
#then sort that array ascending, which makes it sort by descending count then ascending letters
#(just be sure to invert the count again)
for num, letter in sorted([[-letters[k],k] for k in letters]):
    print(f"{letter} -> {-num}")
```

### Ice Cream Sales (★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/08_Dict/08_Dict_​22.pdf)\
Solutions:

```python
ice_cream_prices = {}
for i in range(int(input())):
    name, price = input().strip().split()
    ice_cream_prices[name] = float(price)

ice_cream_sales = {}
for i in range(int(input())):
    name, amount = input().strip().split()
    if name not in ice_cream_prices:
        continue
    if name not in ice_cream_sales:
        ice_cream_sales[name] = 0
    ice_cream_sales[name] += ice_cream_prices[name] * int(amount)

if ice_cream_sales == {}:
    print("No ice cream sales")
else:
    print(f"Total ice cream sales: {sum(ice_cream_sales.values())}")
    #surely there must be a better way to do this right?
    top_sales = sorted([-ice_cream_sales[k], k] for k in ice_cream_sales)
    print("Top sales: " + ", ".join([arr[1] for arr in top_sales if arr[0] == top_sales[0][0]]))


```

```python

import re
menu = dict()
sales = dict()
for i in range(int(input())):
    k,v = input().split()
    menu[k] = float(v)

for i in range(int(input())):
    k,v = input().split()
    if k in menu.keys():
        if sales.get(k, False):
            sales[k] += menu[k]*int(v)
        else:
            sales[k] = menu[k]*int(v)

if sales:
    print(f'Total ice cream sales: %.1f' % sum(sales.values()))
    print(f'Top sales: {re.sub(r"['\]\[]","",str([k for k in sorted(sales.keys()) if sales[k] == max(sales.values())]))}')

else:
    print("No ice cream sales")

```

### Telephone Directory (★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/08_Dict/08_Dict_​23.pdf)\
Solutions:

```python
numbers = {}
for i in range(int(input())):
    first_name, last_name, number = input().strip().split()
    full_name = first_name + " " + last_name
    numbers[full_name] = number
    numbers[number] = full_name

for i in range(int(input())):
    search_string = input().strip()
    print(search_string + " --> " + numbers.get(search_string, "Not found"))
```

### Texting (★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/08_Dict/08_Dict_​24.pdf)\
Solutions:

```python
alphabet = "abcdefghijklmnopqrstuvwxyz"
keys = "23456789"
#i couldnt think of a way to autogenerate the special cases in 1 line :pensive:
text_to_keys = {letter:str(keys[i//3])*((i)%3 + 1) for i, letter in enumerate(alphabet) if i < 15}
text_to_keys.update({
    " ":"0",
    "p":"7",
    "q":"77",
    "r":"777",
    "s":"7777",
    "t":"8",
    "u":"88",
    "v":"888",
    "w":"9",
    "x":"99",
    "y":"999",
    "z":"9999"
    })

keys_to_text = {text_to_keys[k]:k for k in text_to_keys}

def text2keys(text):
    output = ""
    for letter in text.lower():
        if letter in text_to_keys:
            output += text_to_keys[letter] + " "
    return output.strip()

def keys2text(keys):
    return "".join([keys_to_text[k] for k in keys.split()])

exec(input().strip())

```

### Cash (★★★)

[Instructions](https://github.com/isechula/2190101-comprog-grader/blob/main/pdfs/08_Dict/08_Dict_​31.pdf)\
Solutions:

```python

def total(pocket):
    return sum([int(k) * int(pocket[k]) for k in pocket])

def take(pocket, money_in):
    for bank_note in money_in:
        if bank_note in pocket:
            pocket[bank_note] += money_in[bank_note]
        else:
            pocket[bank_note] = money_in[bank_note]

def pay(pocket, amount):
    removed = {}
    #find largest banknote < amount
    #subtract that from amount
    #repeat till no bank notes remain
    for bank_note in sorted(pocket.keys())[::-1]:
        banks_available = pocket.get(bank_note, 0)
        bank_value = int(bank_note)

        if banks_available == 0:
            continue

        if bank_value < amount:
            remove_count = min(banks_available, amount // bank_value)
            removed[bank_note] = remove_count
            amount -= remove_count * bank_value

    #if there is any money left over, that means that we cant pay in an exact value
    if amount != 0:
        return {}

    #remove money from pocket if we can pay an exact amount
    for bank_note in removed:
        pocket[bank_note] -= removed[bank_note]
    return removed

exec(input().strip())
```
