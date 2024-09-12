Fails:
Fail 1:
```
class Solution {
public:
    vector<int> findThePrefixCommonArray(vector<int>& A, vector<int>& B)
    {
        std::vector<int> commons(50, 0);
        std::vector<int> result;
        int common = 0;
        for(int i = 0; i < A.size(); i++)
        {
            int val_a = A[i];
            int val_b = B[i];
            commons[val_a]++;
            commons[val_b]++;
			// Wrong calculations of the common count:
            if(val_a == val_b) common++;
			if(commons[val_a] >= 2) common++;
			if(commons[val_b] >= 2) common++;
            result.push_back(common);
        }
        return result;
    }
};
```
Fail 2:
```
class Solution {
public:
    vector<int> findThePrefixCommonArray(vector<int>& A, vector<int>& B)
    {
        std::vector<int> commons(50, 0); // Wrong total ammounts of totals
        std::vector<int> result;
        int common = 0;
        for(int i = 0; i < A.size(); i++)
        {
            int val_a = A[i];
            int val_b = B[i];
            commons[val_a]++;
            commons[val_b]++;
            if(val_a == val_b)
			{
				common++;
			}
			else
			{
				if(commons[val_a] >= 2) common++;
				if(commons[val_b] >= 2) common++;
			}
            result.push_back(common);
        }
        return result;
    }
};
```
