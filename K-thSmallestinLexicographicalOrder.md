## K-th Smallest in Lexicographical Order
### Space Complexity is O(1).
### JS
```
/**
 * @param {number} n
 * @param {number} k
 * @return {number}
 */
 var findKthNumber = function(n, k) {
    let cur = 1;
    k--;
    while (k > 0) {
        const steps = getSteps(cur, n);
        if (steps <= k) {
            cur++;
            k -= steps;
        } else {
            cur *= 10;
            k--;
        }
    }
    return cur;
};

const getSteps = (cur, n) => {
    let steps = 0;
    let next = cur + 1;
    while (cur <= n) {
        steps += Math.min(n + 1, next) - cur;
        cur *= 10;
        next *= 10;
    }
    return steps;
};
```

### Test Data
```
n	k	Output
13	2	10
1	1	1
10	3	12
25	10	16
99	100	99
```
### Test Cases
```
const testCases = [
  { n: 13, k: 2, output: 10 },
  { n: 1, k: 1, output: 1 },
  { n: 10, k: 3, output: 12 },
  { n: 25, k: 10, output: 16 },
  { n: 99, k: 100, output: 99 },
];

testCases.forEach(({ n, k, output }) => {
  const result = findKthNumber(n, k);
  console.log(`Input: n = ${n}, k = ${k}`);
  console.log(`Output: ${result}`);
  console.log(`Expected: ${output}`);
  console.log(`Result is ${result === output ? 'correct' : 'incorrect'}`);
  console.log('------------------');
});
```

### Explanation
The code uses a greedy approach to find the kth lexicographically smallest integer in the range [1, n]. 
We start with the smallest possible integer, 1, and increment it until we find the kth smallest integer.
To determine the number of steps to increment the current integer,
we use the function getSteps. 
This function calculates the number of integers in the range [cur, cur + 99...9]
(where the number of 9s depends on the current level of the recursion).
If the number of steps is less than or equal to k, we increment cur by 1 and subtract the number of steps from k.
Otherwise, we multiply cur by 10 and decrement k by 1.
This process continues until k becomes 0, at which point cur is the kth lexicographically smallest integer in the range [1, n].
