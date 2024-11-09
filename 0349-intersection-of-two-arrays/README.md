# Intersection of Two Arrays

Given two integer arrays `nums1` and `nums2`, return an **array of their intersection**. Each element in the result must be **unique** and you may return the result in **any order**.

**Example 1:**

Input: `nums1 = [1,2,2,1]`, `nums2 = [2,2]`

Output: `[2]`

**Example 2:**

Input: `nums1 = [4,9,5]`, `nums2 = [9,4,9,8,4]`

Output: `[9,4]`

Explanation: `[4,9]` is also accepted.

 
**Constraints:**

- `1 <= nums1.length, nums2.length <= 1000`
- `0 <= nums1[i], nums2[i] <= 1000`

# Solutions

## Bruteforce approach

```javascript
var intersection = function(nums1, nums2) {
    // Bruteforce appraoch
    const output = new Set();
    for(let i = 0; i < nums1.length; i++) {
        for(let j = 0; j < nums2.length; j++) {
            if(nums1[i] == nums2[j]) {
                output.add(nums1[i]);
            }
        }
    }
    return Array.from(output);
};
```

Time complexity is **O(n<sup>2</sup>)** as there is a nested loop.

Space complexity is **O(n)** as variable `output` can grow linearly as input grows.

<img src="./brute-force.png" style="width: 600px" alt="Brute force"/>

## Using sets

```javascript
var intersection = function (nums1, nums2) {
    // Using sets
    const set1 = new Set();
    const output = new Set();
    for (let i = 0; i < nums1.length; i++) {
        set1.add(nums1[i]);
    }
    for (let j = 0; j < nums2.length; j++) {
        if (set1.has(nums2[j])) {
            output.add(nums2[j]);
        }
    }
    return Array.from(output);
};
```

Time complexity is **O(n)** as there are only 2 separate loops.

Space complexity is **O(n)** as the size of `set1` and `output` increases as input size increases.

<img src="./using-set.png" style="width: 600px" alt="Using set"/>