Fails:
Fail 1:
```
class Solution {
public:
    int hIndex(std::vector<int>& citations) {
        int size = citations.size();
        std::vector<int> cit_count(size + 1, 0);

        for(int num : citations)
            cit_count[min(size, num)]++; // Forgot about there is no min max on leetcode

        int papers_count = 0;
        for(int h_index = size; h_index >= 0; h_index--) 
		{
            papers_count += cit_count[h_index];
            if(papers_count >= h_index) 
                return papers_count;
        }
        return 0;
    }
};
```
Fail 2:
```
#include <algorithm>

class Solution {
public:
    int hIndex(std::vector<int>& citations) {
        int size = citations.size();
        std::vector<int> cit_count(size + 1, 0);

        for(int num : citations) {
            cit_count[std::min(size, num)]++;
        }

        int papers_count = 0;
        for(int h_index = size; h_index >= 0; h_index--) {
            papers_count += cit_count[h_index];
            if(papers_count >= papers_count) 
                return papers_count; // Was returning the wrong thing here. Should've been returning the actual h-index
        }
        return 0;
    }
};
```
