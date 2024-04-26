**

Problem Description

You are given an integer array C of size A. Now you need to find a subarray (contiguous elements) so that the sum of contiguous elements is maximum.

But the sum must not exceed B.

  
  
Problem Constraints

1 <= A <= 103

1 <= B <= 109

1 <= C[i] <= 106

  
  
Input Format

The first argument is the integer A.

The second argument is the integer B.

The third argument is the integer array C.

  
  
Output Format

Return a single integer which denotes the maximum sum.

  
  
Example Input

Input 1:

A = 5

B = 12

C = [2, 1, 3, 4, 5]

  

Input 2:

A = 3

B = 1

C = [2, 2, 2]

  

  
  
Example Output

Output 1:

12

  

Output 2:

0

  

  
  
Example Explanation

Explanation 1:

We can select {3,4,5} which sums up to 12 which is the maximum possible sum.

  

Explanation 2:

All elements are greater than B, which means we cannot select any subarray.

Hence, the answer is 0.

**

```java
**

public class Solution {

   public int maxSubarray(int A, int B, int[] C) {

  

       //Approach One - Brute Force - O(n3) - Generate all subarrays ane one by one calculate the sum. This will give TLE because of constraints

  

       //Optimized Approach - O(n2) - Instead of generating and calculating sum again and again for each subarray. Can we pre calculate the sum and store it in prefix array?

  

       //Prefix Array

       //  int [] P = new int[A];

       //  P[0] = C[0];

       //  int max = Integer.MIN_VALUE;

       //  int sum;

  

       //  for(int i=1; i<A; i++)

       //  {

       //      P[i] = P[i-1] + C[i];

       //  }

  

       //  for(int i=0; i<A; i++)

       //  {

       //      sum = 0;

       //      for(int j=i; j<A; j++)

       //      {

       //         if(i==0)

       //         {

       //           sum = P[j];

       //         }

       //         else

       //         {

       //            sum = P[j] - P[i-1];

       //         }

  

       //         if(sum > max && sum <= B)

       //             max = sum;

       //      }

  

       //  }

  

       //  if(max > Integer.MIN_VALUE)

       //     return max;

       // else

       //     return 0;

  

       //Can we optimize it further? Can we do it O(1) space?

       int max = Integer.MIN_VALUE;

       for(int i=0; i<A; i++) {

           int sum = 0;

           for(int j=i; j<A; j++) {

               sum = sum + C[j];

               if(sum>max && sum<=B) {

                   max = sum;

               }

  

           }

       }

  

      if(max > Integer.MIN_VALUE)

           return max;

       else

           return 0;

   }

}

  


**
```