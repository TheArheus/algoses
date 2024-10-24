200. Number of Islands
```
class Solution {
    void visit(vector<vector<char>>& grid, int x, int y)
    {
        if(x < 0 || y < 0 || x >= grid[0].size() || y >= grid.size()) return;
        if(grid[y][x] == '0') return;
        grid[y][x] = '0';
        visit(grid, x - 1, y);
        visit(grid, x, y - 1);
        visit(grid, x + 1, y);
        visit(grid, x, y + 1);
    }
public:
    int numIslands(vector<vector<char>>& grid) {
        int result = 0;
        for(int y = 0; y < grid.size(); y++)
        {
            for(int x = 0; x < grid[0].size(); x++)
            {
                if(grid[y][x] == '1')
                {
                    result++;
                    visit(grid, x, y);
                }
            }
        }
        return result;
    }
};
```
```
class Solution {
    void visit(vector<vector<char>>& grid, int x, int y)
    {
        if(grid[y][x] == '0') return;

        stack<std::pair<int, int>> graphStack;
        graphStack.push({x, y});
        
        while(!graphStack.empty())
        {
            pair<int, int> point = graphStack.top();
            graphStack.pop();

            if(point.first < 0 || point.second < 0 || point.first >= grid[0].size() || point.second >= grid.size()) continue;
            if(grid[point.second][point.first] == '0') continue;

            grid[point.second][point.first] = '0';
            graphStack.push({point.first - 1, point.second});
            graphStack.push({point.first, point.second - 1});
            graphStack.push({point.first + 1, point.second});
            graphStack.push({point.first, point.second + 1});
        }
    }
public:
    int numIslands(vector<vector<char>>& grid) {
        int result = 0;
        for(int y = 0; y < grid.size(); y++)
        {
            for(int x = 0; x < grid[0].size(); x++)
            {
                if(grid[y][x] == '1')
                {
                    result++;
                    visit(grid, x, y);
                }
            }
        }
        return result;
    }
};
```

Description:
Given an m x n 2D binary grid grid which represents a map of '1's (land) and '0's (water), return the number of islands.
An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are all surrounded by water.

Examples:
Example 1:
Input: grid = [
  ["1","1","1","1","0"],
  ["1","1","0","1","0"],
  ["1","1","0","0","0"],
  ["0","0","0","0","0"]
]
Output: 1

Example 2:
Input: grid = [
  ["1","1","0","0","0"],
  ["1","1","0","0","0"],
  ["0","0","1","0","0"],
  ["0","0","0","1","1"]
]
Output: 3
 
Constraints:
m == grid.length
n == grid[i].length
1 <= m, n <= 300
grid[i][j] is '0' or '1'.
