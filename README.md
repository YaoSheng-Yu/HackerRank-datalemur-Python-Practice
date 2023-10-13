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
