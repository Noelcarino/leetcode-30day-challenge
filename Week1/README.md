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

solution)
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

solution)
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

### 4) Move Zeroes

Given an array nums, write a function to move all 0's to the end of it while maintaining the relative order of the non-zero elements.

ex)
```
Input: [0,1,0,3,12]
Output: [1,3,12,0,0]
```

note)

- You must do this in-place without making a copy of the array.
- Minimize the total number of operations.

solution)
```
function moveZeroes(nums) {
  var idx = 0;
  for (var i = 0; i < nums.length; i++) {
    if (nums[i] !== 0) {
      nums[idx] = nums[i];
      nums[i] = idx === i ? nums[i] : 0;
      idx++;
    }
  }
}
```

### 5) Best Time to Buy and Sell Stock II

Say you have an array for which the ith element is the price of a given stock on day i.

Design an algorithm to find the maximum profit. You may complete as many transactions as you like (i.e., buy one and sell one share of the stock multiple times).

Note: You may not engage in multiple transactions at the same time (i.e., you must sell the stock before you buy again).

ex1)
```
Input: [7,1,5,3,6,4]
Output: 7
Explanation: Buy on day 2 (price = 1) and sell on day 3 (price = 5), profit = 5-1 = 4.
             Then buy on day 4 (price = 3) and sell on day 5 (price = 6), profit = 6-3 = 3.
```

ex2)
```
Input: [1,2,3,4,5]
Output: 4
Explanation: Buy on day 1 (price = 1) and sell on day 5 (price = 5), profit = 5-1 = 4.
             Note that you cannot buy on day 1, buy on day 2 and sell them later, as you are
             engaging multiple transactions at the same time. You must sell before buying again.
```

ex3)
```
Input: [7,6,4,3,1]
Output: 0
Explanation: In this case, no transaction is done, i.e. max profit = 0.
```

solution)
```
var maxProfit = function(prices) {
    if (prices === null || prices.length === 0) {
        return 0;
    }
    
    var profit = 0;
    
    for (var i = 0; i < prices.length - 1; i++){
        if (prices[i+1] > prices[i]) {
            profit += prices[i+1] - prices[i];
        }
    }
    
    return profit;
};
```

### 6) Group Anagrams

Given an array of strings, group anagrams together.

ex)
```
Input: ["eat", "tea", "tan", "ate", "nat", "bat"],
Output:
[
  ["ate","eat","tea"],
  ["nat","tan"],
  ["bat"]
]
```

solution)
```
var groupAnagrams = function(strs) {
    let map = new Map()
	
    for(str of strs) {
        let key = 0;
        for (let char of str) {
            const i = char.charCodeAt(0) 
            key += Math.pow(i, 4)
        }

        !map.has(key) 
            ? map.set(key, [str])
            : map.set(key, map.get(key).concat(str))
    }
    
    return Array.from(map.values())
};
```