Fails:
Fail 1:
The wrong placement of the bounds check(should've been first)
```
class Solution {
    void visit(vector<vector<char>>& grid, int x, int y)
    {
        if(grid[y][x] == '0') return;
        if(x < 0 || y < 0 || x >= grid[0].size() || y >= grid.size()) return;
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
