# moves_zero-leetcode_problem-no.283-
# Move Zeroes Algorithm - Two Pointer Approach

## Problem Statement
Given an integer array, move all zeros to the end while maintaining the relative order of non-zero elements. The operation must be performed in-place.

## Algorithm Overview
**Technique**: Two Pointer Approach
**Time Complexity**: O(n)
**Space Complexity**: O(1)

## Implementation Strategy

### Phase 1: Locate First Zero
```java
for(int i = 0; i < n; i++) {
    if(nums[i] == 0) {
        j = i;
        break;
    }
}
```
**Objective**: Identify the first zero element's position to establish the swap target.

### Phase 2: Sequential Swapping
```java
for(int k = j + 1; k < n; k++) {
    if(nums[k] != 0) {
        swap(nums[k], nums[j]);
        j++;
    }
}
```
**Objective**: Replace zeros with non-zero elements found later in the array.

## Step-by-Step Execution Example

**Input Array**: `[1, 0, 2, 3, 2, 0, 0, 4, 5, 1]`

### Phase 1: Initial Setup
- Scan array to find first zero at index 1
- Initialize pointer `j = 1`

### Phase 2: Iterative Swapping Process

| Iteration | Index k | Element | Action | Array State | j Position |
|-----------|---------|---------|---------|-------------|------------|
| 1 | 2 | 2 | Swap with j=1 | `[1,2,0,3,2,0,0,4,5,1]` | j=2 |
| 2 | 3 | 3 | Swap with j=2 | `[1,2,3,0,2,0,0,4,5,1]` | j=3 |
| 3 | 4 | 2 | Swap with j=3 | `[1,2,3,2,0,0,0,4,5,1]` | j=4 |
| 4 | 5 | 0 | Skip (zero element) | `[1,2,3,2,0,0,0,4,5,1]` | j=4 |
| 5 | 6 | 0 | Skip (zero element) | `[1,2,3,2,0,0,0,4,5,1]` | j=4 |
| 6 | 7 | 4 | Swap with j=4 | `[1,2,3,2,4,0,0,0,5,1]` | j=5 |
| 7 | 8 | 5 | Swap with j=5 | `[1,2,3,2,4,5,0,0,0,1]` | j=6 |
| 8 | 9 | 1 | Swap with j=6 | `[1,2,3,2,4,5,1,0,0,0]` | j=7 |

**Final Result**: `[1, 2, 3, 2, 4, 5, 1, 0, 0, 0]`

## Algorithm Properties

### Key Invariants
1. **Pointer j**: Always references a zero element or the next position where a zero should be placed
2. **Pointer k**: Scans for non-zero elements to relocate
3. **Order Preservation**: Non-zero elements maintain their relative sequence

### Operational Rules
- **Non-zero Element Found**: Perform swap operation and advance j pointer
- **Zero Element Found**: Skip processing, continue iteration
- **Swap Operation**: Exchange elements at positions j and k, then increment j

## Complexity Analysis
- **Time**: O(n) - Single pass through the array
- **Space**: O(1) - Only uses constant extra variables (j, k)
- **Swaps**: At most n-1 swap operations in worst case

## Edge Cases Handled
- Array with no zeros: Algorithm terminates after Phase 1
- Array with only zeros: No swaps performed
- Single element array: Returns unchanged
- Empty array: No operations required
