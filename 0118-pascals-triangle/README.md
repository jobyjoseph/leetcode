# Pascal's Triangle

Given an integer `numRows`, return the first numRows of **Pascal's triangle**.

In **Pascal's triangle**, each number is the sum of the two numbers directly above it as shown:

<img src="./pascals-triangle.gif" style="width: 260px" alt="Pascal triangle"/>

**Example 1:**

Input: `numRows = 5`

Output: `[[1],[1,1],[1,2,1],[1,3,3,1],[1,4,6,4,1]]`

**Example 2:**

Input: `numRows = 1`

Output: `[[1]]`


**Constraints:**

- `1 <= numRows <= 30`


# Solutions

## Using Recursion

```javascript
var generate = function(numRows) {
    if(numRows === 0) {
        return [];
    }
    if(numRows === 1) {
        return [[1]];
    }
    const prevRows = generate(numRows - 1);
    const newRow = new Array(numRows).fill(1);

    for(let i = 1; i < numRows - 1; i++) {
        newRow[i] = prevRows[numRows - 2][i - 1] + prevRows[numRows - 2][i];
    }
    prevRows.push(newRow);
    return prevRows;
};
```

Time complexity **O(n<sup>2</sup>)**.

Space complexity **O(n<sup>2</sup>)**.

<img src="./performance.png" style="width: 600px" alt="Recursion"/>