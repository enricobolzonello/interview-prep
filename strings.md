# Strings

## String of unique characters

Trick to count the characters in a string of unique characters instead of using the dictionary.

```python
mask = 0
for c in word:
    mask |= (1 << (ord(c) - ord('a')))
```



## Get the next character

Given a character c in lowercase, get the next one. Can be adapted to next uppercase or even numbers (if for some absurd reasons you can't just increase it).

```python
next_char = chr((ord(c) - ord('a') + 1) % 26 + ord('a'))
```





