
**
Problem Description

You are given an array A of integers of size N.

Your task is to find the equilibrium index of the given array

The equilibrium index of an array is an index such that the sum of elements at lower indexes is equal to the sum of elements at higher indexes.

If there are no elements that are at lower indexes or at higher indexes, then the corresponding sum of elements is considered as 0.

Note:

- Array indexing starts from 0.
    
- If there is no equilibrium index then return -1.
    
- If there are more than one equilibrium indexes then return the minimum index.
    

  
  
Problem Constraints

1 <= N <= 105

-105 <= A[i] <= 105

  

  
  
Input Format

First argument is an array A .

  
  
Output Format

Return the equilibrium index of the given array. If no such index is found then return -1.

  
  
Example Input

Input 1:

A = [-7, 1, 5, 2, -4, 3, 0]

  

Input 2:

A = [1, 2, 3]

  

  
  
Example Output

Output 1:

3

  

Output 2:

-1

  

  
  
Example Explanation

Explanation 1:

i   Sum of elements at lower indexes    Sum of elements at higher indexes

0                   0                                   7

1                  -7                                   6

2                  -6                                   1

3                  -1                                  -1

4                   1                                   3

5                  -3                                   0

6                   0                                   0

  

3 is an equilibrium index, because: 

A[0] + A[1] + A[2] = A[4] + A[5] + A[6]

  

Explanation 1:

i   Sum of elements at lower indexes    Sum of elements at higher indexes

0                   0                                   5

1                   1                                   3

2                   3                                   0

Thus, there is no such index.

**
```java
**

public class Solution {

   public int solve(int[] A) {

  

       int N = A.length;

       long l_sum,r_sum = 0;

       int ans = -1;

  

       //Calculate Prefix Array

  

       long[] P = new long[N];

       P[0] = A[0];

  

       for(int i=1; i<N; i++)

       {

           P[i] = P[i-1] + A[i];

       }

  

       for(int i=0; i<N; i++) {

  

           //Calculate Left Sum

           if(i==0)

               l_sum = 0;

           else

               l_sum = P[i-1];

  

           //Calculate Right Sum

           r_sum = P[N-1] - P[i];

  

           //Equate

           if(l_sum == r_sum)

           {

               ans = i;

               break;

           }

       }

  

       return ans;

   }

}

**
```