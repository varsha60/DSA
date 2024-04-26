**

Problem Description

Given an array A of length N. Also given are integers B and C.

Return 1 if there exists a subarray with length B having sum C and 0 otherwise

  
  
Problem Constraints

1 <= N <= 105

1 <= A[i] <= 104

1 <= B <= N

1 <= C <= 109

  
  
Input Format

First argument A is an array of integers.

The remaining arguments B and C are integers

  
  
Output Format

Return 1 if such a subarray exist and 0 otherwise

  
  
Example Input

Input 1:

A = [4, 3, 2, 6, 1]

B = 3

C = 11

  

Input 2:

A = [4, 2, 2, 5, 1]

B = 4

C = 6

  

  
  
Example Output

Output 1:

1

  

Output 2:

0

  

  
  
Example Explanation

Explanation 1:

The subarray [3, 2, 6] is of length 3 and sum 11.

  

Explanation 2:

There are no such subarray.

  
  
**

```java
**

public class Solution {

   public int solve(int[] A, int B, int C) {

  

       int N = A.length;

       //B is length of sliding window.

       int sum = 0;

       //Calculate sum of first window

       for(int i=0; i<=B-1; i++) {

           sum = sum + A[i];

       }

       //Best case first window ka sum hi == C hai

       if(sum == C)

           return 1;

       int i = 1;

       int j = B;

       //I and J are 2 pointers starting from 1 and B index. J will go out of loop when J becomes N

       //last possible J ka value is N-1 obviously.

       while (j<N) {

           //First window main se subtract out of window item and add element just came inside window

           sum = sum - A[i-1] + A[j];

           //Check kya yeh subarray ka sum == C hai ?

           if(sum == C)

               return 1;

           //Agge bado increment kro dusre window par jaou

           i++;

           j++;

       }

   return 0;

   }

}

**
```