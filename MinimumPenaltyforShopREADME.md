# leet-day46

# Problem: Find the Best Closing Time for a Shop

Given a string representing customer visits to a shop over time, the task is to determine the earliest hour at which the shop should be closed to minimize the penalty. The penalty is incurred when the shop is open and no customers come or when the shop is closed and customers come. The goal is to find the closing hour that incurs the minimum penalty.

## Approach

The idea behind this approach is to simulate the effect of opening and closing the shop at different hours while calculating the penalty. We keep track of the current penalty and compare it with the minimum penalty encountered so far. The closing hour associated with the minimum penalty is the optimal closing time for the shop.

1. Initialize variables to keep track of the penalty, minimum penalty, and the corresponding closing hour.
2. Iterate through each hour from 1 to `n` (size of the string).
   - Calculate the penalty change based on whether a customer arrives ('Y') or not ('N') at the current hour.
   - Update the penalty by subtracting the penalty change.
   - Compare the current penalty with the minimum penalty encountered so far. If it's smaller, update the minimum penalty and the corresponding closing hour.
3. Return the closing hour with the minimum penalty.

## Implementation

```cpp
class Solution {
public:
    int bestClosingTime(string customers) {
        int n = customers.size();
    
        int penalty = 0; // Initialize penalty
        int minPenalty = penalty, minHour = 0;
        
        // Iterate through each hour
        for (int hour = 1; hour <= n; hour++) {
            int y = (customers[hour - 1] == 'Y') ? 1 : -1; // Calculate penalty change
            penalty -= y; // Update penalty
            
            // Check if current penalty is less than minimum penalty
            if (minPenalty > penalty) {
                minPenalty = penalty;
                minHour = hour;
            }
        }
        
        return minHour;
    }
};
```

## Complexity Analysis

- Time Complexity: O(n), where n is the size of the input string.
- Space Complexity: O(1), as we only use a constant amount of extra space for variables.
