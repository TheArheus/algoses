Fails
Fail 1:

```
#include <limits.h>
#define MAX(a, b) (a > b ? a : b)
#define MIN(a, b) (a < b ? a : b)
class Solution 
{
public:
    bool isReflected(vector<std::vector<int>>& points) 
	{
		int min_x = INT_MAX;
		int max_x = INT_MIN;
		std::unordered_set<std::pair<int, int>> points_hash; // Forgot about non hashable std::pair
		for(int i = 0; i < points.size(); i++)
		{
			min_x = MIN(min_x, points[i][0]);
			max_x = MAX(max_x, points[i][0]);
			points_hash.insert({points[i][0], points[i][1]});
		}

		int s_calc = min_x + max_x;
		for(int i = 0; i < points.size(); i++)
		{
			std::pair<int, int> point_check{s_calc - points[i][0]}; // Not fully constructed std::pair point
			if(points_hash.find(point_check) == points_hash.end()) return false;
		}

		return true;
    }
};
```
