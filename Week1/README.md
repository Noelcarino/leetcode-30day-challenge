# Week 1

### 1) Single Number

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

### 2) Happy Number

Write an algorithm to determine if a number is "happy".

A happy number is a number defined by the following process: Starting with any positive integer, replace the number by the sum of the squares of its digits, and repeat the process until the number equals 1 (where it will stay), or it loops endlessly in a cycle which does not include 1. Those numbers for which this process ends in 1 are happy numbers.

ex)
```
Input: 19
Output: true
Explanation: 
12 + 92 = 82
82 + 22 = 68
62 + 82 = 100
12 + 02 + 02 = 1
```

```
var isHappy = function(n) {
    console.log(n);
    if (n === 0 || n === 4) return false;
    if (n === 1) return true;
    else {
        var check = n.toString().split('');
        var pieces = [];
        var piecesSum = 0;
        for (var i = 0; i < check.length; i++){
            pieces.push(parseInt(check[i]) * parseInt(check[i]));
        }
        for (var j = 0; j < pieces.length; j++){
            piecesSum += pieces[j];
        }
        return isHappy(piecesSum);
    }
};
```

### 3) Maximum Subarray

Given an integer array nums, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum.

ex)
```
Input: [-2,1,-3,4,-1,2,1,-5,4],
Output: 6
Explanation: [4,-1,2,1] has the largest sum = 6.
```

```
var maxSubArray = function(nums) {
    
    var prev = 0;
    var max = -Number.MAX_VALUE;
    
    for (var i = 0; i < nums.length; i++){
        prev = Math.max(prev + nums[i], nums[i]);
        max = Math.max(max,prev);
    }
    return max;
}; 
```