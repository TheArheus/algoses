Fail:
Fail 1:
```
class Solution {
public:
    bool isValidSudoku(vector<vector<char>>& board) {
        std::unordered_map<std::string, bool> cols;
        std::unordered_map<std::string, bool> rows;
        std::unordered_map<std::string, bool> blocks;
        for(int y = 0; y < 9; y++)
        {
            for(int x = 0; x < 9; x++)
            {
                char val = board[y][x];
                if(val == '.') continue;
                std::string col_key = "x" + std::to_string(x) + val;
                std::string row_key = "y" + std::to_string(y) + val;
                std::string block_key = "x" + std::to_string(x) + "y" + std::to_string(y) + " " + val; // Wrong block indexation
                if(cols[col_key] || rows[row_key] || blocks[block_key]) return false;

                cols[col_key] = true;
                rows[row_key] = true;
                blocks[block_key] = true;           
            }
        }
        return true;
    }
};
```
