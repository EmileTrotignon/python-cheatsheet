# Python cheatsheet

## Control structures 1

### If

The syntax for the if control structure is the following :

```python
if condition:
  code
```

If the expression `condition` evaluates to `True`, then the bloc `code` is run.
If it evaluates to `False`, then nothing is done.

Example :

```python
x = 15000
if x < 20000:
  print('x is smaller than 20000')
```

### If-else

The syntax for the if-else control structure is the following :

```python
if condition:
  code1
else:
  code2
```

If the expression `condition` evaluates to `True`, then the bloc `code1` is run.
If it evaluates to `False`, then the bloc `code2` is run.

```python
x = 15000
if x < 20000:
  print('x is smaller than 20000')
else:
  print('x is greater or equal than 20000')
```

### While

The syntax for the while control structure is the following :

```python
while condition:
  code1
```

While `condition` evaluates to True, `code1` is executed repeadly.

Example :

```python
i = 0
while i < 5:
  print(i)
  i = i + 1
```

Executing the above will print

```text
0
1
2
3
4
```

## Lists

### List definition

A list is defined the following way :

```python
# Empty list
my_list_1 = []

# List with a few elements
my_list_2 = [4, 7, 8]

# List of strings

my_list_3 = ['hey', 'how', 'are', 'you']
```

### List access

You can access a list with the following syntax :

```python
# First element, here worth 4
my_list_2[0]

# Second element here worth 7
my_list_2[1]

# Third element, here worth 8
my_list_2[2]
```

The integer used to access the list is called an "indice".
We can say that the list `my_list_3` associates the value `'are'` to the indice
`2`.

### List utilities

#### Append

An alternative way to construct the same list as `my_list_3` is to append
elements to an empty list.

```python
alt_my_list_3 = []

alt_my_list_3.append('hey')
alt_my_list_3.append('how')
alt_my_list_3.append('are')
alt_my_list_3.append('you')
```

To construct a list, this is not a very nice syntax, the first one above is
more practical.
However this one has the advantage of being dynamic, that is we can put it
inside some control structure:

```python

greeting_list = ['hey', 'good']

if is_morning():
  greeting_list.append('morning')
else:
  greeting_list.append('')
```

#### Length

To get the length of a list, use the `len` function :

```python
greeting_list = ['hey', 'how', 'are', 'you']
print(len(greeting_list))
```

The above prints `4`.

### List iterating

If you have a list and you want to use its content, you may use a while loop :

```python
greeting_list = ['hey', 'how', 'are', 'you']

i = 0
while i < len(greeting_list):
  value = greeting_list[i]
  print(value)
  i = i + 1
```

The above will print :

```text
hey
how
are
you
```

This is quite useful, but we can do simpler.

## Control structures 2

### For

The basic syntax of a for loop is the following :

```python
for variable in iterator:
  code
```

Here, `iterator` has to evaluate to something that is "list-like". Then `code`
will be executed `n` times, where `n` is the length of `iterator` and each time,
`variable` will have for value an element of `iterator`.

Let us look at an exemple :

We can use a for loop to automatically iterate through a list :

```python
greeting_list = ['hey', 'how', 'are', 'you']

for value in greeting_list:
  print(value)
```

The above is equivalent to the previous example, it also prints :

```text
hey
how
are
you
```

#### Range

I have previously mentioned that lists are not the only thing that you can use a
for loop on.

Let us look at the following code :

```python
greeting_list = ['hey', 'how', 'are', 'you']

i = 0
while i < len(greeting_list):
  value = greeting_list[i]
  print(i, value)
  i = i + 1
```

This will print the following :

```text
0 hey
1 how
2 are
3 you
```

We cannot replicate this behaviour with a for loop.
We can however use the range function to simulate it :

```python
greeting_list = ['hey', 'how', 'are', 'you']

n = len(greeting_list)
for i in range(n):
  value = greeting_list[i]
  print(i, value)
```

will print the same text.

To describe range more precisly, `range(n)` is a list-like value, this is
analogous to `[0, 1, ..., n - 1]`. It does not include `n` because it starts at
0 and has `n` elements.

## Dictionnaries

We can see a list as something that given a indice will give you a value.
However, the indice is always an integer between `0` and the length of the list.
A dictionnary allow you to use all sort of values as "indices". Since this is
not always an integer, we will use word "key" to describe it.

```python
# Empty dictionnary:
empty_dict = {}

# Dictionnary with values :
greetings = { 'morning': 'good morning',
              'noon': 'bon appetit',
              'afternoon':'good afternoon'}
```

You can access the value associated to a key with the same syntax as for lists:

```python
# The below will print 'bon appetit'
print(greetings['noon'])
```

You can add a `key: value` pair by the following :

```python
greetings['night'] = 'sleep well'

# The below will print 'sleep well'
print(greetings['night'])
```

### Iterating through dictionnaries

Contrary to lists, you cannot use a while loop through dictionnaries, because
you have no way of knowing what the keys are. However you can use a for loop :

```python
for key in greetings:
  value = greetings[key]
  print('The greeting for the', key, 'is :', value)
```

The above will print:

```text
The greeting for the morning is : good morning
The greeting for the noon is : bon appetit
The greeting for the afternoon is : good afternoon
The greeting for the night is : sleep well
```

You can also iterate directly through keys and value using the following:

```python
for key, value in items(greetings):
  print('The greeting for the', key, 'is :', value)
```

### Deleting an entry

To delete an entry in a dictionnary, simply use the `del` keyword :

```python
del my_dict[key]
```
