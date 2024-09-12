Line reflections
```
#include <limits.h>
#define MAX(a, b) (a > b ? a : b)
#define MIN(a, b) (a < b ? a : b)
class Solution 
{
	struct pair_hash
	{
		template<class type1, class type2>
		size_t operator()(const std::pair<type1, type2>& Pair) const
		{
			return std::hash<type1>()(Pair.first) ^ std::hash<type2>()(Pair.second);
		}
	};
public:
    bool isReflected(vector<std::vector<int>>& points) 
	{
		int min_x = INT_MAX;
		int max_x = INT_MIN;
		std::unordered_set<std::pair<int, int>, pair_hash> points_hash;
		for(int i = 0; i < points.size(); i++)
		{
			min_x = MIN(min_x, points[i][0]);
			max_x = MAX(max_x, points[i][0]);
			points_hash.insert({points[i][0], points[i][1]});
		}

		int s_calc = min_x + max_x;
		for(int i = 0; i < points.size(); i++)
		{
			std::pair<int, int> point_check{s_calc - points[i][0], points[i][1]};
			if(points_hash.find(point_check) == points_hash.end()) return false;
		}

		return true;
    }
};
```
