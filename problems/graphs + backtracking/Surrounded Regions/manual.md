130. Surrounded Regions
```
class Solution {
    void visit(vector<vector<char>>& grid, int x, int y)
    {
        if(x < 0 || y < 0 || x >= grid[0].size() || y >= grid.size()) return;
        if(grid[y][x] == 'X' || grid[y][x] == 'E') return;
        grid[y][x] = 'E';
        visit(grid, x - 1, y);
        visit(grid, x, y - 1);
        visit(grid, x + 1, y);
        visit(grid, x, y + 1);
    }
public:
    void solve(vector<vector<char>>& board) {
        if (board.empty() || board[0].empty()) return;
        for(int y = 0; y < board.size(); y++)
        {
            visit(board, 0, y);
            visit(board, board[0].size() - 1, y);
        }
        for(int x = 0; x < board[0].size(); x++)
        {
            visit(board, x, 0);
            visit(board, x, board.size() - 1);
        }
        for(int y = 0; y < board.size(); y++)
        {
            for(int x = 0; x < board[0].size(); x++)
            {
                if(board[y][x] == 'E')
                    board[y][x] = 'O';
                else if(board[y][x] == 'O')
                    board[y][x] = 'X';
            }
        }
    }
};
```

Description:
You are given an m x n matrix board containing letters 'X' and 'O', capture regions that are surrounded:

Connect: A cell is connected to adjacent cells horizontally or vertically.
Region: To form a region connect every 'O' cell.
Surround: The region is surrounded with 'X' cells if you can connect the region with 'X' cells and none of the region cells are on the edge of the board.
A surrounded region is captured by replacing all 'O's with 'X's in the input matrix board.

Examples:
Example 1:
Input: board = [["X","X","X","X"],["X","O","O","X"],["X","X","O","X"],["X","O","X","X"]]
Output: [["X","X","X","X"],["X","X","X","X"],["X","X","X","X"],["X","O","X","X"]]
Explanation:
In the above diagram, the bottom region is not captured because it is on the edge of the board and cannot be surrounded.

Example 2:
Input: board = [["X"]]
Output: [["X"]]

 
Constraints:
m == board.length
n == board[i].length
1 <= m, n <= 200
board[i][j] is 'X' or 'O'.
