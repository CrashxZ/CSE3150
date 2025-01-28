# Programming Practice: Subset Sum

## Problem Description

Implement the function:
```cpp
bool ECSubsetSum(vector<int>& nums, int target);
```

Write a function `ECSubsetSum` that determines if there exists a subset of the given integer array `nums` whose sum equals the given `target`. The function should return `true` if such a subset exists, and `false` otherwise.

### Constraints:
- Each element of `nums` is a positive integer.
- The size of `nums` will not exceed 20.
- You may use recursion to solve the problem.

### Examples:

**Example 1:**
```cpp
Input: nums = [1, 2, 3, 7], target = 6
Output: true
Explanation: The subset {1, 2, 3} sums to 6.
```

**Example 2:**
```cpp
Input: nums = [1, 2, 7, 1, 5], target = 10
Output: true
Explanation: The subset {2, 7, 1} sums to 10.
```

**Example 3:**
```cpp
Input: nums = [1, 3, 4, 8], target = 6
Output: false
Explanation: There is no subset that sums to 6.
```

---

## Starter Code

### `ECSubsetSum.h`
```cpp
#ifndef ECSUBSETSUM_H
#define ECSUBSETSUM_H

#include <vector>
using namespace std;

namespace ECNumbers
{
    // Function declaration
    bool ECSubsetSum(vector<int>& nums, int target);
}

#endif
```

### `ECSubsetSum.cpp`
```cpp
#include "ECSubsetSum.h"
using namespace ECNumbers;

bool ECSubsetSumHelper(vector<int>& nums, int target, int index)
{
    // TODO: Implement this helper function
    return false; // Placeholder
}

bool ECSubsetSum(vector<int>& nums, int target)
{
    return ECSubsetSumHelper(nums, target, 0);
}
```

### `TestSubsetSum.cpp`
```cpp
#include <iostream>
#include "ECSubsetSum.h"

using namespace std;
using namespace ECNumbers;

int main()
{
    vector<int> nums1 = {1, 2, 3, 7};
    cout << "Subset Sum (nums1, target = 6): " << (ECSubsetSum(nums1, 6) ? "true" : "false") << endl;

    vector<int> nums2 = {1, 2, 7, 1, 5};
    cout << "Subset Sum (nums2, target = 10): " << (ECSubsetSum(nums2, 10) ? "true" : "false") << endl;

    vector<int> nums3 = {1, 3, 4, 8};
    cout << "Subset Sum (nums3, target = 6): " << (ECSubsetSum(nums3, 6) ? "true" : "false") << endl;

    return 0;
}
```

---

## Solution

### `ECSubsetSum.cpp`
```cpp
#include "ECSubsetSum.h"
using namespace ECNumbers;

// Helper function for recursion
bool ECSubsetSumHelper(vector<int>& nums, int target, int index)
{
    // Base case: target becomes 0, subset found
    if (target == 0)
        return true;

    // Base case: no numbers left or target is negative
    if (index >= nums.size() || target < 0)
        return false;

    // Include the current number in the subset and check
    if (ECSubsetSumHelper(nums, target - nums[index], index + 1))
        return true;

    // Exclude the current number from the subset and check
    return ECSubsetSumHelper(nums, target, index + 1);
}

bool ECSubsetSum(vector<int>& nums, int target)
{
    return ECSubsetSumHelper(nums, target, 0);
}
```

---

## Explanation

1. **Recursive Helper Function:**
   - The helper function `ECSubsetSumHelper` takes the current index and target as arguments.
   - It checks all combinations of including and excluding the current number to find a subset that sums to the target.

2. **Base Cases:**
   - If `target == 0`, it means we found a subset that satisfies the condition.
   - If `index >= nums.size()` or `target < 0`, no valid subset can be formed.

3. **Recursive Calls:**
   - Include the current number: `target - nums[index]` and move to the next index.
   - Exclude the current number: keep the same target but move to the next index.

4. **Complexity:**
   - Time Complexity: \(O(2^n)\), where \(n\) is the size of the input array.
   - Space Complexity: \(O(n)\) due to recursive stack.

---


