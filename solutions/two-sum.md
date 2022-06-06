layout: page
title: "Two Sum Problem"
permalink: /solutions/two-sum

# Two Sum Problem

Given an array of integers and an integer target, return indices of the two numbers such that they add up to target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.

### Solution

```
function twoSum(nums: number[], target: number): number[] {   
    // Map to act as memory for numbers seen so far.
    // Maps number to their indices.
    const memory = new Map<number,number>();
    for(let i = 0; i < nums.length; i++){
        if(memory.get(target - nums[i]) != undefined){ // remember 0 is falsy
            return [memory.get(target - nums[i]), i]
        }
        memory.set(nums[i], i);
    }
    return [];
};
```
