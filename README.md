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

# Climbing the Leaderboard  
An arcade game player wants to climb to the top of the leaderboard and track their ranking. The game uses Dense Ranking, so its leaderboard works like this:

The player with the highest score is ranked number 1 on the leaderboard.
Players who have equal scores receive the same ranking number, and the next player(s) receive the immediately following ranking number.

---------------------------------------
**Solution**
```python
def climbingLeaderboard(ranked, player):
    unique_ranked = sorted(set(ranked), reverse=True)
    result = []
    i = len(unique_ranked) - 1  # Start from the lowest rank

    for p in player:
        while i >= 0 and p >= unique_ranked[i]:
            i -= 1
        if i == -1:
            result.append(1)
        else:
            result.append(i + 2)

    return result
```

# Max Profit Trading Stocks [Google Python Interview Question] (Greedy)
# Stock Price Profit Calculator

You are given a list of stock `prices`, where the stock's price on the `i`th day is stored as the `i`th element of the prices list. You want to maximize your profit trading the stock, but are only allowed to buy the stock once and sell it once on a future day. Write a function called `max_profit` which takes in this list of stock prices, and computes the max profit possible. Return `0` if you can't make any profit.

## Example 1:
Input: `prices = [9, 1, 3, 6, 4, 8, 3, 5, 5]`
Output: `7`
Explanation: Buy on day 2 (price = 1) and sell on day 6 (price = 8), `profit = 8 - 1 = 7`.

Note that buying on day 2 and selling on day 1 is not allowed because you have to buy the stock BEFORE you can sell it (unless you're a time-traveller in which case just trade bitcoin).

## Example 2:
Input: `prices = [6, 4, 3, 3, 2]`
Output: `0`
Explanation: In this case, no trades should be made since the stock is tanking like a brick. The max profit here is `0`.


---------------------------------------
**Solution**
```python
def max_subarray_sum(prices):
  min_price = prices[0]
  max_profit = 0
  for i in range(1, len(prices)):
    min_price = min(prices[i], min_price)
    max_profit = max(max_profit, prices[i] - min_price)
    
  return max_profit

```

# Max Profit Trading Stocks [Google Python Interview Question] (Greedy)
Given an integer array, find the sum of the largest contiguous subarray within the array.

For example, if the input is [−1, −3, 5, −4, 3, −6, 9, 2], then return 11 (because of [9, 2]).

Note that if all the elements are negative, you should return 0.

---------------------------------------
**Solution**
```python
def max_subarray_sum(input):
	if all(x<0 for x in input):
	  return 0
	  
	current_sum = 0
	max_sum = 0
	
	for x in input:
	  current_sum = max(x, current_sum+x)
	  max_sum = max(current_sum, max_sum)
	  
	return max_sum

```

# Two Sum [Amazon Python Interview Question]

Given an list of integers called input, and an integer target, return the index of the two numbers which sum up to the target. Do not use the same list element twice.

Clarifications:

Assume there aren't multiple valid solutions.
In case there is no valid solution, return [-1, -1].
Return the indexes in increasing order (i.e. [1,3], NOT [3,1]).

Example #1
Input: input = [1, 4, 6, 10], target = 10

Output: [1, 2]

Example #2
Input: input = [1, 4, 6, 10], target = 11

Output: [0, 3]


Example #3
**Input: **input = [1, 4, 6, 10], target = 2

Output: [-1, -1]

---------------------------------------
**Solution**
```python
def two_sum(input: list[int], target: int) -> list[int]:
    # Create a list of tuples with element and its original index
    indexed_input = [(val, idx) for idx, val in enumerate(input)]
    # Sort this list of tuples by the elements
    indexed_input.sort(key=lambda x: x[0])

    i = 0
    j = len(indexed_input) - 1
    while i < j:
        current_sum = indexed_input[i][0] + indexed_input[j][0]
        if current_sum > target:
            j -= 1
        elif current_sum < target:
            i += 1
        else:  # current_sum == target
            # Return the original indices in sorted order
            return sorted([indexed_input[i][1], indexed_input[j][1]])
    return [-1, -1]
```
