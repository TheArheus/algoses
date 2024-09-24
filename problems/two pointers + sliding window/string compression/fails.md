Fails
Fail 1:
```
class Solution 
{
public:
    int compress(vector<char>& chars)
    {
		int l = 0;
		int r = 0;
		while(l < chars.size()) // Forgot that in my case r can go out of bounds
		{
			int  count = 1;
			char currentChar = chars[r];
			while(r + 1 < chars.size() && chars[r + 1] == currentChar)
			{
				count++;
				r++;
			}

			chars[l++] = currentChar;
			if(count > 1)
			{
				string countString = to_string(count);
				for(char numChar : countString)
				{
					chars[l++] = numChar;
				}
			}
			r += 1;
		}

		return l;
    }
};
```
