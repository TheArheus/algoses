Fails
Fail 1:
```
class Solution 
{
public:
    vector<int> xorQueries(vector<int>& arr, vector<vector<int>>& queries)
	{
		std::vector<int> PrefixXor;
		int XorAccum = 0;
		PrefixXor.push_back(XorAccum);
		for(int i = 0; i < arr.size(); i++)
		{
			XorAccum ^= arr[i];
			PrefixXor.push_back(XorAccum);
		}

		std::vector<int> Result;
		for(int i = 0; i < queries.size(); i++)
		{
			Result.push_back(PrefixXor[queries[i][0] - 1] ^ PrefixXor[queries[i][1]]);
		}

		return Result;
    }
};
```
