# leet-day46

# Rotate Image

## Problem Description

You are given an `n x n` 2D matrix representing an image. Your task is to rotate the image by 90 degrees clockwise. You need to perform this rotation in-place, which means modifying the input 2D matrix directly. You are not allowed to allocate another 2D matrix to perform the rotation.

## Example

### Input

```
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]
```

### Output

```
rotated_matrix = [
    [7, 4, 1],
    [8, 5, 2],
    [9, 6, 3]
]
```

## Approach

To rotate the given matrix by 90 degrees clockwise, you can follow these steps:

1. **Transpose the Matrix**: Swap each element at position `(i, j)` with the element at position `(j, i)`. This operation effectively transposes the matrix.

2. **Reverse Rows**: After transposing, each row of the matrix is essentially in the same position as a column in the original matrix. To achieve the clockwise rotation, reverse each row.

## Pseudocode

```plaintext
function rotate(matrix):
    n = matrix.size
    
    // Step 1: Transpose the matrix
    for i = 0 to n - 1:
        for j = i + 1 to n - 1:
            swap(matrix[i][j], matrix[j][i])

    // Step 2: Reverse rows
    for i = 0 to n - 1:
        reverse(matrix[i].begin(), matrix[i].end())
```

## Complexity Analysis

- **Time Complexity**: The algorithm goes through the entire matrix twice. Transposing the matrix takes `O(n^2)` time, and reversing each row takes `O(n)` time. Thus, the overall time complexity is `O(n^2)`.

- **Space Complexity**: The algorithm performs all operations in-place, without using any additional space. Hence, the space complexity is `O(1)`.

## Implementation

```cpp
class Solution {
public:
    void rotate(vector<vector<int>>& matrix) {
        int n = matrix.size();

        // Step 1: Transpose the matrix
        for (int i = 0; i < n; i++) {
            for (int j = i + 1; j < n; j++) {
                swap(matrix[i][j], matrix[j][i]);
            }
        }

        // Step 2: Reverse rows
        for (int i = 0; i < n; i++) {
            reverse(matrix[i].begin(), matrix[i].end());
        }
    }
};
```

This solution effectively rotates the given matrix by 90 degrees clockwise in-place.
