11. Container With Most Water
```
#include <algorithm>
class Solution
{
public:
    int maxArea(vector<int>& height)
    {
        int p1 = 0;
        int p2 = height.size() - 1;
        int result = 0;
        while(p1 < p2)
        {
            int height1 = height[p1];
            int height2 = height[p2];
            int area = std::min(height1, height2) * (p2 - p1);
            result = std::max(result, area);

            if(height1 < height2) p1++;
            else p2--;
        }

        return result;
    }
};
```

Description:
You are given an integer array height of length n. There are n vertical lines drawn such that the two endpoints of the ith line are (i, 0) and (i, height[i]).

Find two lines that together with the x-axis form a container, such that the container contains the most water.

Return the maximum amount of water a container can store.

Notice that you may not slant the container.

Examples
Example 1:
Input: height = [1,8,6,2,5,4,8,3,7]
Output: 49
Explanation: The above vertical lines are represented by array [1,8,6,2,5,4,8,3,7]. In this case, the max area of water (blue section) the container can contain is 49.

Example 2:
Input: height = [1,1]
Output: 1

Constraints:
n == height.length
2 <= n <= 105
0 <= height[i] <= 104
