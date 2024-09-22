## Reverse Integer
### Time Complexity is O(log10(x))
### JS
```
var reverse = function(x) {
  if (x < 0) {
    let absX = Math.abs(x);
    let reversed = parseInt(absX.toString().split('').reverse().join(''));
    return reversed > 2 ** 31 ? 0 : -reversed;
  } else {
    let reversed = parseInt(x.toString().split('').reverse().join(''));
    return reversed > 2 ** 31 - 1 ? 0 : reversed;
  }
};
```

### Test Data
```
Input: x = 123
Output: 321

Input: x = -123
Output: -321

Input: x = 120
Output: 21
```

### Test Cases
```
const assert = require('assert');

describe('Reverse Integer', function() {
  it('should reverse a positive integer', function() {
    assert.strictEqual(reverse(123), 321);
  });

  it('should reverse a negative integer', function() {
    assert.strictEqual(reverse(-123), -321);
  });

  it('should reverse a zero', function() {
    assert.strictEqual(reverse(0), 0);
  });

  it('should handle overflows', function() {
    assert.strictEqual(reverse(2 ** 31), 0);
    assert.strictEqual(reverse(-2 ** 31), 0);
  });
});
```

### Explanation
The code first checks if the input integer x is negative.
If it is, the absolute value of x is taken and reversed.
The reversed integer is then checked to see if it is greater than 231 - 1.
If it is, 0 is returned, otherwise the negative of the reversed integer is returned.
If x is not negative, it is reversed and checked to see if it is greater than 231 - 1.
If it is, 0 is returned, otherwise the reversed integer is returned.
