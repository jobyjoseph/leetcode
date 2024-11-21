# Pascal's Triangle II

Given an integer `rowIndex`, return the `rowIndex`<sup>th</sup> (**0-indexed**) row of the Pascal's triangle.

In Pascal's triangle, each number is the sum of the two numbers directly above it as shown:

<img src="./pascals-triangle.gif" style="width: 260px" alt="Pascal triangle"/>

**Example 1:**

Input: `rowIndex = 3`

Output: `[1,3,3,1]`

**Example 2:**

Input: `rowIndex = 0`

Output: `[1]`

**Example 3:**

Input: `rowIndex = 1`

Output: `[1,1]`


**Constraints:**

- `0 <= rowIndex <= 33`

 
**Follow up:** Could you optimize your algorithm to use only `O(rowIndex)` extra space?

# Solutions

## Using recursion

```javascript
var generate = function (numRows) {
    if (numRows === 1) {
        return [[1]];
    }
    const prevRows = generate(numRows - 1);
    const newRow = new Array(numRows).fill(1);

    for (let i = 1; i < numRows - 1; i++) {
        newRow[i] = prevRows[numRows - 2][i - 1] + prevRows[numRows - 2][i];
    }
    prevRows.push(newRow);
    return prevRows;
};

var getRow = function (rowIndex) {
    const numRows = rowIndex + 1;
    return generate(numRows)[rowIndex];
};
```

Time complexity **O(n<sup>2</sup>)**.

Space complexity **O(n<sup>2</sup>)**.

<img src="./performance.png" style="width: 600px" alt="Recursion"/>