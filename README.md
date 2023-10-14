# HackerRank-Python-Practice
Record some more challenging and typical python problem on HackerRank for future review

# Caesar Cipher
Julius Caesar protected his confidential information by encrypting it using a cipher. Caesar's cipher shifts each letter by a number of letters. If the shift takes you past the end of the alphabet, just rotate back to the front of the alphabet. In the case of a rotation by 3, w, x, y and z would map to z, a, b and c.  

---------------------------------------
**Solution**
```python
# The function is expected to return a STRING.
# The function accepts following parameters:
#  1. STRING s
#  2. INTEGER k
#

def caesarCipher(s, k):
    shifted_string = ''

    for char in s:
        # For lowercase characters
        if 'a' <= char <= 'z':
            shifted_char = chr((ord(char) - ord('a') + k) % 26 + ord('a'))
            shifted_string += shifted_char
        # For uppercase characters
        elif 'A' <= char <= 'Z':
            shifted_char = chr((ord(char) - ord('A') + k) % 26 + ord('A'))
            shifted_string += shifted_char
        # For non-alphabetic characters
        else:
            shifted_string += char

    return shifted_string

```

# Sherlock and the Valid String
Sherlock considers a string to be valid if all characters of the string appear the same number of times. It is also valid if he can remove just  character at  index in the string, and the remaining characters will occur the same number of times. Given a string , determine if it is valid. If so, return YES, otherwise return NO.

---------------------------------------
**Solution**
```python
def isValid(s):
    char_dict = {}

    for char in s:
        char_dict[char] = char_dict.get(char, 0) + 1

    count_dict = {}
    for count in char_dict.values():
        count_dict[count] = count_dict.get(count, 0) + 1

    if len(count_dict) == 1:
        return 'YES'
    elif len(count_dict) == 2:
        key1, key2 = count_dict.keys()
        if count_dict[key1] == 1:
            if key1 - 1 == key2 or key1 == 1:
                return 'YES'
        if count_dict[key2] == 1:
            if key2 - 1 == key1 or key2 == 1:
                return 'YES'
    return 'NO'


```
