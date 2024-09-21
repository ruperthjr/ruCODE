## Time Complexity
```cpp O(n^2) ```
### JS
```
/**
 * @param {string} s
 * @return {string}
 */
const longestPalindrome = (s) => {
  let start = 0;
  let end = 0;
  let maxLength = 0;

  for (let i = 0; i < s.length; i++) {
    for (let j = i + 1; j < s.length; j++) {
      if (s[i] === s[j] && j - i + 1 > maxLength && isPalindrome(s.substring(i, j + 1))) {
        start = i;
        end = j;
        maxLength = j - i + 1;
      }
    }
  }

  return s.substring(start, end + 1);
};

const isPalindrome = (s) => {
  for (let i = 0; i < s.length / 2; i++) {
    if (s[i] !== s[s.length - i - 1]) {
      return false;
    }
  }

  return true;
};
```

### Test Data
```
"babad"
"cbbd"
"a"
"bb"
"deed"
```

### Test Cases
```
const testCases = [
  {
    input: "babad",
    expected: "bab"
  },
  {
    input: "cbbd",
    expected: "bb"
  },
  {
    input: "a",
    expected: "a"
  },
  {
    input: "bb",
    expected: "bb"
  },
  {
    input: "deed",
    expected: "deed"
  }
];
```

### Explanation
The code uses a double loop to find the longest palindrome in the string. 
The outer loop iterates over the string, 
and the inner loop checks if the substring starting at the current position is a palindrome. 
If the substring is a palindrome and its length is greater than the current maximum length, 
the start and end indices of the palindrome are updated.

The isPalindrome function checks if a string is a palindrome by comparing the first and last characters, 
the second and second-to-last characters, and so on. 
If the string is a palindrome, the function returns true; otherwise, it returns false.

The code returns the substring from the start index to the end index, which is the longest palindrome in the string.
