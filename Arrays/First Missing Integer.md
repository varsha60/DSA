**

Problem Description

Given an unsorted integer array, A of size N. Find the first missing positive integer.

Note: Your algorithm should run in O(n) time and use constant space.

  
  
Problem Constraints

1 <= N <= 1000000

-109 <= A[i] <= 109

  
  
Input Format

First argument is an integer array A.

  
  
Output Format

Return an integer denoting the first missing positive integer.

  
  
Example Input

Input 1:

[1, 2, 0]

Input 2:

[3, 4, -1, 1]

Input 3:

[-8, -7, -6]

  
  
Example Output

Output 1:

3

Output 2:

2

Output 3:

1

  
  
Example Explanation

Explanation 1:

A = [1, 2, 0]

First positive integer missing from the array is 3.

Explanation 2:

A = [3, 4, -1, 1]

First positive integer missing from the array is 2.

Explanation 3:

A = [-8, -7, -6]

First positive integer missing from the array is 1.

**

```java
**

public class Solution {

   public int firstMissingPositive(int[] A) {

  

       //Brute Force - N^2

       //Using hash set - N and space also N

       //Using boolean array to mark the presence of the elements - N and N

  

//Optimized approach - N and space 1

  

  

       //Edge case - duplicates - 2 3 1 2

  

       int N = A.length;

  

       for(int i=0; i<N; i++) {

           if(A[i]<=0) {

               //Mark all negative elements with N+2 as it can't be missing integer ever.

               A[i] = N+2;

           }

       }

  

       for(int i=0; i<N; i++) {

           int element = Math.abs(A[i]);

           if(element>=1 && element<=N) {

  

               //If we care - let's mark the presence

               A[element-1] = (-1) * (Math.abs(A[element-1])); //If duplicate - that's why math.abs

           }

       }

  

       for(int i=0; i<N; i++) {

  

           //First positive element encountered - that index is never been marked so i+1 is missing.

           if(A[i]>0) {

               return i+1;

           }

       }

  

//At max N+1 can be missing - if all elements from 1 to N are present in an array of size N.

       return N+1;

   }

}

  


**
```