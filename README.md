class Solution:
    # Function to find the sum of contiguous subarray with maximum sum.
    def maxSubarraySum(self, arr):
        # Initialize max_so_far with the first element
        # Initialize current_max with the first element
        max_so_far = arr[0]
        current_max = arr[0]
        
        # Iterate from the second element to the end
        for i in range(1, len(arr)):
            # Decision: Should we start a new subarray or extend the current one?
            current_max = max(arr[i], current_max + arr[i])
            
            # Update the overall maximum found    max_so_far = m
