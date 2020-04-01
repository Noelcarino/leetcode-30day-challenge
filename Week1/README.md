# Week 1

#### 1) Single Number

Given a non-empty array of integers, every element appears twice except for one. Find that single one.

Note:

Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?

ex1)
```
Input: [2,2,1]
Output: 1
```

ex2)
```
Input: [4,1,2,1,2]
Output: 4
```

solution )
```
var singleNumber = function(nums) {
    let sortedArray = nums.sort();
    for (var i = 0; i < sortedArray.length; i = i + 2) {
        if (sortedArray[i] !== sortedArray[i+1]) return sortedArray[i];
    }
};
```