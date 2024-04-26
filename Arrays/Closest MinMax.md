**Problem Description

Given an array A, find the size of the smallest subarray such that it contains at least one occurrence of the maximum value of the array

and at least one occurrence of the minimum value of the array.

  
  
Problem Constraints

1 <= |A| <= 2000

  
  
Input Format

First and only argument is vector A

  
  
Output Format

Return the length of the smallest subarray which has at least one occurrence of minimum and maximum element of the array

  
  
Example Input

Input 1:

A = [1, 3, 2]

  

Input 2:

A = [2, 6, 1, 6, 9]

  

  
  
Example Output

Output 1:

2

  

Output 2:

3

  

  
  
Example Explanation

Explanation 1:

Take the 1st and 2nd elements as they are the minimum and maximum elements respectively.

  

Explanation 2:

Take the last 3 elements of the array.

  
  
  
  
  
  

Hint - Every Min will look for max and every max will look for min.**

```java
**

public class Solution {

   public int solve(int[] A) {

  

       int N = A.length;

       int ans = N; //Worst length of subarray possible

  

       int last_max_index = -1;

       int last_min_index = -1;

  

       int max_value = Integer.MIN_VALUE;

       int min_value = Integer.MAX_VALUE;

  

       for(int i=0;i<N;i++)

       {

           if(A[i]>max_value)

               max_value = A[i];

           if(A[i]<min_value)

               min_value = A[i];

       }

  

       for(int i=0;i<N;i++)

       {

           int length = 0;

  

           if(A[i] == min_value)

           {

               last_min_index = i;

  

               if(last_max_index != -1) {

                   length = i - last_max_index + 1;

                   if(length < ans )

                       ans = length;

               }

           }

  

           if(A[i] == max_value)

           {

               last_max_index = i;

  

               if(last_min_index != -1) {

                   length = i - last_min_index + 1;

                   if(length < ans )

                       ans = length;

               }

           }

       }

  

       return ans;

   }

}

**
```