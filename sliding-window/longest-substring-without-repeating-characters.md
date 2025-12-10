# [3. Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/)

<code color=#fac82f>Medium</code>

## Description

Return <code color=green>length</code> of longest substring with no duplicate characters.

## Example

<table>
    <tr>
        <th> Input: </th>
        <td> <code>s = "abcabcbb"</code> </th>
    <tr>
        <th> Output: </th>
        <td> <code>3</code> </th>
    </tr>
</table>

## Intuition

Need to iterate over every substring with no duplicate characters in the string. Using a sliding window while storing each seen character allows us to nvaigate the whole string, ensuring the sliding window always exludes duplicates. The longest length found will be the answer.

## Algorithm

1. **<ins>Declare</ins>** dict to store the indices of each <code color=darkred>encountered character</code>
2. **<ins>Declare</ins>** a sliding window and the <code color=green>max-length</code>
3. **<ins>While</ins>** the <code color=darkred>window’s end</code> has not reached the end of <code color=green>s</code>:
     - **<ins>If</ins>** the char at the <code color=darkred>window’s end</code> was <code color=darkred>previously seen</code> and its <code color=darkred>index</code> is within the current window:
          - **<ins>Move</ins>** the <code color=darkred>window’s start</code> to the index immediately after the previously seen instance of the current <code color=darkred>char</code>.
     - **<ins>Add</ins>** the <code color=darkred>char</code> at the <code color=darkred>window’s end</code> to the dict of <code color=darkred>encountered chars</code> with its <code color=darkred>index</code>.
     - **<ins>Update</ins>** the <code color=green>max-length</code> to the maximum of itself or the current window length.

## Complexity
<table>
    <tr>
        <th> Time: </th>
        <td> <code>O(n)</code> </th>
        <td> Where <code>n</code> is the length of <code color=green>s</code> </th>
    <tr>
        <th> Space: </th>
        <td> <code>O(min(n, m))</code> </th>
        <td> Where <code>n</code> is the length of <code color=green>s</code> and <code>m</code> is length of the character set of <code color=green>s</code> </th>
    </tr>
</table>

## Code

```python
def lengthOfLongestSubstring(self, s: str) -> int:
   last_seen = {}
   l = 0
   max_length = 0
  
   for r, c in enumerate(s):
       if c in last_seen:
           l = last_seen[c] + 1
       last_seen[c] = right
       max_length = max(max_length, r - l + 1)
  
   return max_length
```
