# [1. Two Sum](https://leetcode.com/problems/two-sum/)

<code color=#4db0ad>Easy</code>

## Description

Return the <code color=green>indices</code> of two numbers that add up to <code color=green>target</code>

## Example

<table>
    <tr>
        <th> Input: </th>
        <td> <code>nums = [2,7,11,15], target = 9</code> </th>
    <tr>
        <th> Output: </th>
        <td> <code>[0,1]</code> </th>
    </tr>
</table>

## Intuition

The answer requires finding two elements (the indices), so introduce a hashmap that holds onto already-encountered potential complements to the current number, eliminating the need for nested traversal.

## Algorithm

1. **<ins>Declare</ins>** dict to store previously encountered numbers in the list with their indices
2. **<ins>Traverse</ins>** the list. At each step:
     - **<ins>Calculate</ins>** <code color=darkred>complement</code> of the current <code color=darkred>number</code> with the <code color=green>target</code>
     - **<ins>If</ins>** the <code color=darkred>complement</code> was previously encountered:
          - **<ins>Return</ins>** list with current  <code color=green>index</code> and the <code color=green>complement’s index</code> 
     - **<ins>Insert</ins>** current <code color=darkred>number</code> with the current <code color=green>index</code> as previously encountered

## Complexity
<table>
    <tr>
        <th> Time: </th>
        <td> <code>O(n)</code> </th>
        <td> Traverse whole list in worst case </th>
    <tr>
        <th> Space: </th>
        <td> <code>O(n)</code> </th>
        <td> Store whole list in dictionary in worst case </th>
    </tr>
</table>

## Code

```python
def twoSum(self, nums: List[int], target: int) -> List[int]:
   seen_nums = {}

   for i, num in enumerate(nums):
       complement = target - num
       if complement in seen_nums:
           return [i, seen_nums[complement]]
       seen_nums[num] = i
```
