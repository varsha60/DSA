**Problem Description

Given an array A of size N, find the subarray of size B with the least average.

  
  
Problem Constraints

1 <= B <= N <= 105

-105 <= A[i] <= 105

  

  
  
Input Format

First argument contains an array A of integers of size N.

Second argument contains integer B.

  
  
Output Format

Return the index of the first element of the subarray of size B that has least average.

Array indexing starts from 0.

  
  
Example Input

Input 1:

A = [3, 7, 90, 20, 10, 50, 40]

B = 3

  

Input 2:

A = [3, 7, 5, 20, -10, 0, 12]

B = 2

  

  
  
Example Output

Output 1:

3

  

Output 2:

4

  

  
  
Example Explanation

Explanation 1:

Subarray between indexes 3 and 5

The subarray {20, 10, 50} has the least average 

among all subarrays of size 3.

  

Explanation 2:

Subarray between [4, 5] has minimum average

  

Isn’t this similar to the maximum sum problem ? Instead of the maximum sum, let's slide the minimum average.**

```java
**

public class Solution {

   public int solve(int[] A, int B) {

  

       int N = A.length;

  

       int result_index = 0;

       //B is length of sliding window.

       int minimum_average = Integer.MAX_VALUE;

  

       int average = 0;

       //Calculate average of first window

       for(int i=0; i<=B-1; i++) {

           average = average + A[i];

       } 

  

      //agar apna average first window ka kam hai minimum_average se toh minimum_average = average hojayega.

       if(average < minimum_average) {

           minimum_average = average;

       }

       int i = 1;

       int j = B;

       //I and J are 2 pointers starting from 1 and B index. J will go out of loop when J becomes N

       //last possible J ka value is N-1 obviously.

       while (j<N) {

           //First window main se subtract out of window item and add element just came inside window

           average = average - A[i-1] + A[j];

           //Check kya yeh minimum_average hai kya?

           if(average < minimum_average) {

               result_index = i;

               minimum_average = average;

  

           }

           //Agge bado increment kro dusre window par jaou

           i++;

           j++;

       }

   return result_index;

   }

   }

  


**
```