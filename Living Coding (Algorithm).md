# Living Coding (Algorithm)

## 1. Find Maximum and Minimum Number

- Sort() Function

```python
def find_min_max(input):
  if input is None or len(input) == 0:
    return
  input.sort()
  print('min:{} and max:{}'.format(input[0], input[-1]))
```

- Index 放在第一个位置，Iteration list elements

```python
def find_min_max(input):
  if input is None or len(input) == 0:
    return
  min = input[0]
  max = input[0]
  for i in input:
    if i < min:
      min = i
    if i > max:
      max = i
	print('min:{} and max:{}'.format(min, max))
```

## 2.Word Frequency 出现频率

- 建立字典（Dict）

```python 
def find_freq(input):
  if input is None or len(input) == 0:
    return
  
  dict = {}
  for i in input:
    if dict[i] is None:
      dict[i] = 1
    else:
      dict[i] = dict[i] + 1
  
  for key, value in dict.items():
    for value > 1:
      print('Duplicate:{} and Frequency:{}'.format(key, value))
    print('Word: {} and Count: {}'.format(key, value))
```

- Remove Duplicates

```python
def remove_duplicates(input):
  if input is None or len(input) == 0:
    return
  
  dict = {}
  for i in input:
    if dict[i] is None:
      dict[i] = 1
    else:
      dict[i] = dict[i] + 1
  
  ## Method 1: keep value = 1
  for key, value in dict.items():
    for value > 1:
      dict.pop(key)
    print('Word: {} and Count: {}'.format(key, value))
	return dict


## Method 2: Two Pointers
class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:
        """
        Removes the duplicates from the sorted array `nums` and returns the number of unique elements.

        Args:
            nums: The sorted array.

        Returns:
            The number of unique elements in the array.
        """

        i = 0
        for j in range(1, len(nums)):
            if nums[j] != nums[i]:
                i += 1
                nums[i] = nums[j]
				return i + 1
  
```

## 3. TWO SUM (**) https://leetcode.com/problems/two-sum/

```python 
'''Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.
'''
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        if nums is None or len(nums) == 0:
            return

        temp = list(nums)
        temp.sort()
        i = 0
        j = len(nums) - 1

        while i < j:
            if temp[i] + temp[j] == target:
                a = nums.index(temp[i])
                b = nums.index(temp[j])
                if a == b:
                    b = nums.index(temp[j], a+1)
                return [a, b]
            elif temp[i] + temp[j] < target:
                i += 1
            else:
                j -= 1
```

## 4. Anagram (Dictionary Method) [242. Valid Anagram](https://leetcode.com/problems/valid-anagram/)

```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        if s is None or t is None or len(s) != len(t):
            return False
        
        count_s = {}
        count_t = {}

        for i in s:
            if i not in count_s.keys():
                count_s[i] = 1
            else:
                count_s[i] = count_s[i] + 1
        
        for i in t:
            if i not in count_t.keys():
                count_t[i] = 1
            else:
                count_t[i] = count_t[i] + 1

        if count_s == count_t:
            print(count_s, count_t)
            return True
        else:
            return False
```



## 5. 整除问题 ([412. Fizz Buzz](https://leetcode.com/problems/fizz-buzz/))

```python
class Solution:
    def fizzBuzz(self, n: int) -> List[str]:
        res = []
        for i in range(1, n+1):
            print(i)
            if i % 3 == 0 and i % 5 == 0:
                res.append("FizzBuzz")
            elif i % 3 == 0:
                res.append("Fizz")
            elif i % 5 == 0:
                res.append("Buzz")
            else:
                res.append(str(i))
        return res   
```



![Screenshot 2024-03-02 at 15.20.21](/Users/moonqj/Desktop/Screenshot 2024-03-02 at 15.20.21.jpeg)



1. **Create a Directory for the Module:** You need to create a directory with the same name as your module. This is because Python treats directories containing an `__init__.py` file as packages. In your case, you would create a directory named `fizzbuzz_math`.
2. **Add an `__init__.py` File:** Within the `fizzbuzz_math` directory, you need to create an empty file named `__init__.py`. This file indicates to Python that the directory should be treated as a package. It can be an empty file or it can contain valid Python code.



To use the `__init__.py` file to make the `is_odd` function directly accessible when importing the package, you'd modify the `__init__.py` file to import the desired functions from the modules within the package. Here's how it works:

Let's say you have the following structure:

```
markdownCopy code
fizzbuzz_math/
    __init__.py
    math_functions.py
```

And `math_functions.py` contains:

```
pythonCopy code
# math_functions.py
def is_odd(number):
    return number % 2 != 0
```

If you want to be able to import `is_odd` directly from `fizzbuzz_math` instead of having to import it from `fizzbuzz_math.math_functions`, you can edit the `__init__.py` file as follows:

```
pythonCopy code
# __init__.py
from .math_functions import is_odd
```

The `.` before `math_functions` indicates a relative import. It means "import `is_odd` from the `math_functions` module in the current package directory".

Now, when you do:

```
pythonCopy code
from fizzbuzz_math import is_odd
```

Python will look inside the `__init__.py` file of `fizzbuzz_math` to see if `is_odd` is defined or imported there. Since you've added the import statement in `__init__.py`, it will be available for use.

Without modifying the `__init__.py` file, if you attempt the above import, Python will not find an `is_odd` symbol in the `__init__.py` and will raise an ImportError.

In summary, the `__init__.py` file can be used to make certain functions available at the package level, simplifying the import path for more convenient usage in other scripts.
