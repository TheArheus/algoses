Palindrome Permutations
```
class Solution 
{
public:
    bool canPermutatePalindromic(std::string& s) 
	{
		char char_count[26] = {};
		for(char v : s)
		{
			char_count[v - 'a'] = (char_count[v - 'a'] + 1) % 2;
		}

		int odd_count = 0;
		for(int i = 0; i < 26; i++)
		{
			odd_count += char_count[i];
		}

		return odd_count <= 1;
    }
};
```
