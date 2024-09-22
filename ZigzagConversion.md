## Zigzag Conversion
### Time Complexity **O(n)**
### JS
```
/**
 * Zigzag Conversion
 *
 * @param {string} s
 * @param {number} numRows
 * @return {string}
 */
const convert = (s, numRows) => {
  if (numRows <= 1) {
    return s;
  }

  const rows = new Array(numRows).fill('');
  let row = 0;
  let goingDown = false;

  for (let i = 0; i < s.length; i++) {
    rows[row] += s[i];

    if (row === 0 || row === numRows - 1) {
      goingDown = !goingDown;
    }

    row += goingDown ? 1 : -1;
  }

  return rows.join('');
};
```
### Test Data
```
s = "PAYPALISHIRING"
numRows = 3
expectedOutput = "PAHNAPLSIIGYIR"

s = "PAYPALISHIRING"
numRows = 4
expectedOutput = "PINALSIGYAHRPI"

s = "A"
numRows = 1
expectedOutput = "A"
```

### Test Cases
```
const testCases = [
  {
    s: "PAYPALISHIRING",
    numRows: 3,
    expectedOutput: "PAHNAPLSIIGYIR",
  },
  {
    s: "PAYPALISHIRING",
    numRows: 4,
    expectedOutput: "PINALSIGYAHRPI",
  },
  {
    s: "A",
    numRows: 1,
    expectedOutput: "A",
  },
];

for (let i = 0; i < testCases.length; i++) {
  const testCase = testCases[i];
  const actualOutput = convert(testCase.s, testCase.numRows);
  console.log(`Test Case ${i + 1}:`);
  console.log(`Input: s = "${testCase.s}", numRows = ${testCase.numRows}`);
  console.log(`Expected Output: "${testCase.expectedOutput}"`);
  console.log(`Actual Output: "${actualOutput}"`);
  console.log(actualOutput === testCase.expectedOutput ? "Passed" : "Failed");
}
```
### Explanation
The code first checks if the number of rows is less than or equal to 1.
If it is, the original string is returned as there is no need for zigzag conversion.
Otherwise, an array of strings is created to represent the different rows. 
The row variable keeps track of the current row being worked on,
and the goingDown variable indicates whether the current movement is going down or up in the zigzag pattern.
The code then iterates over each character in the input string and appends it to the appropriate row in the rows array. 
If the current row is at the top or bottom of the zigzag pattern, the goingDown variable is flipped to indicate a change in direction.
Once all characters have been processed, the rows array is joined together to form the final zigzag converted string, which is then returned.
