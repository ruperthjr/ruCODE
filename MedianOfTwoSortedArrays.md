## Median of Two Sorted Arrays
### JS
```
/**
 * @param {number[]} nums1
 * @param {number[]} nums2
 * @return {number}
 */
const findMedianSortedArrays = (nums1, nums2) => {
  // Merge the two arrays
  const merged = [...nums1, ...nums2].sort((a, b) => a - b);

  // Find the median of the merged array
  const mid = Math.floor(merged.length / 2);
  return merged.length % 2 === 1 ? merged[mid] : (merged[mid - 1] + merged[mid]) / 2;
};
```

### Test Data
```
const nums1 = [1, 3];
const nums2 = [2];
const expected = 2.00000;

const nums3 = [1, 2];
const nums4 = [3, 4];
const expected2 = 2.50000;
```

### Test Cases
```
it("should return the median of two sorted arrays", () => {
  const result = findMedianSortedArrays(nums1, nums2);
  expect(result).toBeCloseTo(expected, 5);
});

it("should return the median of two sorted arrays", () => {
  const result = findMedianSortedArrays(nums3, nums4);
  expect(result).toBeCloseTo(expected2, 5);
});
```

### Explanation
This code merges the two input arrays into a single sorted array. 
It then finds the median of the merged array by getting the middle element if the length of the array is odd,
or the average of the two middle elements if the length of the array is even.

