Intersection Of Sorted Arrays
```
/**
 * @input A : Read only ( DON'T MODIFY ) Integer array
 * @input n1 : Integer array's ( A ) length
 * @input B : Read only ( DON'T MODIFY ) Integer array
 * @input n2 : Integer array's ( B ) length
 * 
 * @Output Integer array. You need to malloc memory, and fill the length in len1
 */
#define min(a, b) (a<b?a:b)
int* intersect(const int* A, int n1, const int* B, int n2, int *len1)
{
    int p1 = 0;
    int p2 = 0;
    int i = 0;
    int* result = (int*)calloc(sizeof(int), min(n1, n2));
    while(p1 < n1 && p2 < n2)
    {
        if(A[p1] < B[p2])
        {
            p1++;
        }
        else if(A[p1] > B[p2])
        {
            p2++;
        }
        else
        {
            result[i] = A[p1];
            p1++;
            p2++;
            i++;
        }
    }

    *len1 = i;
    return result;
}
```

Description:
Find the intersection of two sorted arrays OR in other words, given 2 sorted arrays, find all the elements which occur in both arrays.
NOTE: For the purpose of this problem ( as also conveyed by the sample case ), assume that elements that appear more than once in both arrays should be included multiple times in the final output.

Input Format
The first argument is an integer array A.
The second argument is an integer array B.

Output Format
Return an array of intersection of the two arrays.

Examples:
Example 1:
A: [1 2 3 3 4 5 6]
B: [3 3 5]
1: [3 3 5]

Example 2:
A: [1 2 3 3 4 5 6]
B: [3 5]
2: [3 5]

Example Explanation
Explanation 1:
3, 3, 5 occurs in both the arrays A and B
Explanation 2:
Only 3 and 5 occurs in both the arrays A and B

Constraints:
1 <= |A| <= 106
1 <= |B| <= 106
