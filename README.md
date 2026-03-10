class Solution:
    def minJumps(self, arr):
        n = len(arr)
        
        # If the first element is 0 and there's more than one element, 
        # we can't move anywhere.
        if arr[0] == 0:
            return -1
        
        # If there's only one element, we are already at the end (0 jumps).
        if n <= 1:
            return 0
            
        max_reach = arr[0]
        end_of_current_jump = arr[0]
        jumps = 1
        
        # We don't need to process the last element because 
        # once we reach or cross it, we are done.
        for i in range(1, n - 1):
            # Update the farthest we can reach from the current index
            max_reach = max(max_reach, i + arr[i])
            
            # If we reach the end of our current jump's range
            if i == end_of_current_jump:
                jumps += 1
                end_of_current_jump = max_reach
                
                # If the current index is the farthest we can reach and it's 0,
                # we are stuck.
                if i >= max_reach:
                    return -1
        
        # Final check: if we couldn't reach the last index
        if end_of_current_jump < n - 1:
            return -1
            
        return jumps

