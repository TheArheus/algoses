658. Find K Closest Elements
```
class Solution {
public:
    vector<int> findClosestElements(vector<int>& arr, int k, int x)
    {
        int l = -1;
        int r = arr.size() - k;
        while(r - l > 1)
        {
            int m = l + (r - l) / 2;
            if(arr[m] - x < x - arr[m + k])
                l = m;
            else
                r = m;
        }
        return vector<int>(arr.begin() + r, arr.begin() + r + k);
    }
};
```
```
class Solution {
public:
    vector<int> findClosestElements(vector<int>& arr, int k, int x)
    {
        int l = k - 1;
        int r = arr.size();
        while(r - l > 1)
        {
            int m = l + (r - l) / 2;
            if(arr[m] - x < x - arr[m - k])
                l = m;
            else
                r = m;
        }
        return vector<int>(arr.begin() + l - k + 1, arr.begin() + l + 1);
    }
};
```

Description:
Given a sorted integer array arr, two integers k and x, return the k closest integers to x in the array. The result should also be sorted in ascending order.

An integer a is closer to x than an integer b if:

|a - x| < |b - x|, or
|a - x| == |b - x| and a < b
 
Examples:
Example 1:
Input: arr = [1,2,3,4,5], k = 4, x = 3
Output: [1,2,3,4]

Example 2:
Input: arr = [1,1,2,3,4,5], k = 4, x = -1
Output: [1,1,2,3]

Constraints:
1 <= k <= arr.length
1 <= arr.length <= 104
arr is sorted in ascending order.
-104 <= arr[i], x <= 104


  2  1  0 -1 -2
[ 1, 2, 3, 4, 5], k=4, x=3
              | |

 -2 -2 -3 -4 -5 -6
[ 1, 1, 2, 3, 4, 5], k=4, x=-1
              |    |

  2  2  1  1  1  1  1  0  0
[ 1, 1, 2, 2, 2, 2, 2, 3, 3], k=3, x=3
                          | |
