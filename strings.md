# Strings

## String of unique characters

Trick to count the characters in a string of unique characters instead of using the dictionary.

```python
mask = 0
for c in word:
    mask |= (1 << (ord(c) - ord('a')))
```

