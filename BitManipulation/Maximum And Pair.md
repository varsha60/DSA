**Problem Description

Given an array A. For every pair of indices i and j (i != j), find the maximum A[i] & A[j].

  
  
Problem Constraints

1 <= len(A) <= 105

1 <= A[i] <= 109

  
  
Input Format

The first argument is an integer array A.

  
  
Output Format

Return a single integer that is the maximum A[i] & A[j].

  
  
Example Input

Input 1:-

A = [53, 39, 88]

  

Input 2:-

A = [38, 44, 84, 12] 

  

  
  
Example Output

Output 1:-

37

  

Output 2:-

36

  

  
  
Example Explanation

Explanation 1:-

53 & 39 = 37

39 & 88 = 0

53 & 88 = 16

Maximum among all these pairs is 37

  

Explanation 2:-

Maximum bitwise and among all pairs is (38, 44) = 36

  
  

Approach:

Main idea here is - we want overlapping 1s as left as possible (MSB bit side) to get maximum.**

```java
**

public class Solution {

   boolean checkBit(int i, int A) {

       if((A&(1<<i))!=0) return true;

  

       return false;

   }

  

   public int solve(int[] A) {

  

       int N = A.length;

       int result = 0;

  

       for(int i=31; i>=0; i--) {

           //for every bit check the set bits in all elements

           int countSetBits = 0;

  

           for(int j=0; j<N; j++) {

               if(checkBit(i,A[j])) countSetBits++;

           }

  

           //if we can make pair of 1s

           if(countSetBits>=2) {

               //we can make pairs of 1 and resultant bit will be 1

               result = (result | (1<<i));

  

               for(int k=0; k<N; k++) {

                   if(!checkBit(i,A[k])) A[k] = 0;

               }

           }

       }

  

       return result;

   }

}

**
```