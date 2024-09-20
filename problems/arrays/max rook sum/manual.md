Max Rook Sum
```
#define MAX(a, b) (a > b ? a : b)
class solution
{
public:
	int MaxRookSum(std::vector<std::vector<int>> Table)
	{
		std::vector<int> PrefixRowsSum(Table.size(), 0);
		std::vector<int> PrefixColsSum(Table.size(), 0);
		for(int r = 0; r < Table.size(); r++)
		{
			for(int c = 0; c < Table[r].size(); c++)
			{
				PrefixRowsSum[r] += Table[r][c];
				PrefixColsSum[c] += Table[r][c];
			}
		}

		int MaxSum = INT_MIN;
		for(int r = 0; r < Table.size(); r++)
		{
			for(int c = 0; c < Table[r].size(); c++)
			{
				MaxSum = MAX(MaxSum, PrefixRowsSum[r] + PrefixColsSum[c] - Table[r][c]);
			}
		}

		return MaxSum;
	}

	int MaxBishopSum(std::vector<std::vector<int>> Table)
	{
		std::unordered_map<int, int> PrimoryDiag;
		std::unordered_map<int, int> SecondaryDiag;
		for(int r = 0; r < Table.size(); r++)
		{
			for(int c = 0; c < Table[r].size(); c++)
			{
				PrimaryDiag[r - c] += Table[r][c];
				SecondaryDiag[r + c] += Table[r][c];
			}
		}

		int MaxSum = INT_MIN;
		for(int r = 0; r < Table.size(); r++)
		{
			for(int c = 0; c < Table[r].size(); c++)
			{
				MaxSum = MAX(MaxSum, PrimaryDiag[r - c] + SecondaryDiag[r + c] - Table[r][c]);
			}
		}

		return MaxSum;
	}


	int MaxQueenSum(std::vector<std::vector<int>> Table)
	{
		std::unordered_map<int, int> PrimoryDiag;
		std::unordered_map<int, int> SecondaryDiag;
		std::vector<int> PrefixRowsSum(Table.size(), 0);
		std::vector<int> PrefixColsSum(Table.size(), 0);
		for(int r = 0; r < Table.size(); r++)
		{
			for(int c = 0; c < Table[r].size(); c++)
			{
				PrefixRowsSum[r] += Table[r][c];
				PrefixColsSum[c] += Table[r][c];
				PrimaryDiag[r - c] += Table[r][c];
				SecondaryDiag[r + c] += Table[r][c];
			}
		}

		int MaxSum = INT_MIN;
		for(int r = 0; r < Table.size(); r++)
		{
			for(int c = 0; c < Table[r].size(); c++)
			{
				MaxSum = MAX(MaxSum, PrefixRowsSum[r] + PrefixColsSum[c] + PrimaryDiag[r - c] + SecondaryDiag[r + c] - 3 * Table[r][c]);
			}
		}

		return MaxSum;
	}
};
```
