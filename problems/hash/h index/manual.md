H-Index
```
#include <algorithm>

class Solution {
public:
    int hIndex(std::vector<int>& citations) 
	{
        int size = citations.size();
        std::vector<int> cit_count(size + 1, 0);

        for(int num : citations) 
		{
            cit_count[std::min(size, num)]++;
        }

        int papers_count = 0;
        for(int h_index = size; h_index >= 0; h_index--) 
		{
            papers_count += cit_count[h_index];
            if(papers_count >= h_index) 
                return h_index;
        }
        return 0;
    }
};
```

Description:
Given an array of integers citations where citations[i] is the number of citations a researcher received for their ith paper, return the researcher's h-index.

According to the definition of h-index on Wikipedia: The h-index is defined as the maximum value of h such that the given researcher has published at least h papers that have each been cited at least h times.

Examples:
Example 1:

Input: citations = [3,0,6,1,5]
Output: 3
Explanation: [3,0,6,1,5] means the researcher has 5 papers in total and each of them had received 3, 0, 6, 1, 5 citations respectively.
Since the researcher has 3 papers with at least 3 citations each and the remaining two with no more than 3 citations each, their h-index is 3.
Example 2:

Input: citations = [1,3,1]
Output: 1

Constraints:
n == citations.length
1 <= n <= 5000
0 <= citations[i] <= 1000
