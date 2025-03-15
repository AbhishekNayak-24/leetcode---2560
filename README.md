# leetcode---2560
House Robber IV
//code in java
public class Solution {
    public int minCapability(int[] nums, int k) {
        int left = 0, right = (int) 1e9;
        while (left < right) {
            int mid = (left + right) >> 1;
            if (canRobAtLeastK(nums, k, mid)) {
                right = mid;
            } else {
                left = mid + 1;
            }
        }
        return left;
    }

    private boolean canRobAtLeastK(int[] nums, int k, int capability) {
        int count = 0;
        int i = 0;
        while (i < nums.length) {
            if (nums[i] <= capability) {
                count++;
                i++; // Skip the next house to avoid adjacent robbery
            }
            i++;
        }
        return count >= k;
    }
}
