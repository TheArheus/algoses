One Edit Distance
```
#include <algorithm>
#include <cstdlib>
class Solution 
{
public:
    bool oneEditDistance(std::string& A, std::string& B)
    {
		int lengthA = A.length();
		int lengthB = B.length();
		int lengthDiff = std::abs(lengthA - lengthB);
		if(lengthDiff > 1) return false;

		int p1 = 0;
		int p2 = 0;
		int editCount = 0;
		while(p1 < lengthA && p2 < lengthB)
		{
			char sym_a = A[p1];
			char sym_b = B[p2];

			if(sym_a != sym_b)
			{
				editCount++;
				if(editCount > 1) return false;

				if(lengthA > lengthB){p1++;}
				else if(lengthA < lengthB){p2++;}
				else {p1++;p2++;}
			}
			else{p1++; p2++;}
		}

		return editCount == 1 || (editCount == 0 && lengthDiff == 1);
    }
};
```
