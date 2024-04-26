**

Problem Description

Find the maximum sum of contiguous non-empty subarray within an array A of length N.

  
  
Problem Constraints

1 <= N <= 1e6  
-1000 <= A[i] <= 1000

  
  
Input Format

The first and the only argument contains an integer array, A.

  
  
Output Format

Return an integer representing the maximum possible sum of the contiguous subarray.

  
  
Example Input

Input 1:

A = [1, 2, 3, 4, -10]

Input 2:

A = [-2, 1, -3, 4, -1, 2, 1, -5, 4]

  
  
Example Output

Output 1:

10

Output 2:

6

  
  
Example Explanation

Explanation 1:

The subarray [1, 2, 3, 4] has the maximum possible sum of 10.

Explanation 2:

The subarray [4,-1,2,1] has the maximum possible sum of 6.

  

Kaden’s - Think of a relationship example. Temporary Down moments can come. But if you are all negative because of toxicity then you will reinvent yourself and walk away. 

  

In Interview - Give examples of cases 

1. All positive 
    
2. All negative 
    
3. All negatives - all positives 
    
4. All positives - all negatives 
    
5. All positives - all negatives - all positives - What should we do ? - Eg:- -2, 3, 4, -1, 5, -10, 7
    

  

[https://hackmd.io/@topics/Hy9mq6X-T#Problem-1---Find-Maximum-Subarray-Sum](https://hackmd.io/@topics/Hy9mq6X-T#Problem-1---Find-Maximum-Subarray-Sum)

**
```java
**

public class Solution {

   // DO NOT MODIFY THE ARGUMENTS WITH "final" PREFIX. IT IS READ ONLY

   public int maxSubArray(final int[] A) {

  

       /* Approach 1 - Generate all subarrays and calculate sum of each subarray and maintain max sum. O(N^3)

       Approach 2 - Use prefix sum array - o(N^2) and space O(N)

       Approach 3 - carry forward technique - O(N^2) and space O(1).

       Optimized Approach kadane's algorithm

  

       1. maintain 2 variables current_sum and max_sum.

           Idea here is, we don't wat to carry current sum if it is negative because it will obviously minimize our sum

       2. Iterate array

           add a[i] to current_sum

           update max_sum to max(current_sum,max_sum)

           update current_sum to 0 if current_sum is -ve

       */

  

       int current_sum = 0;

       int max_sum = Integer.MIN_VALUE;

  

       int size_of_array = A.length;

  

       //iterate over array

       for(int i=0; i<size_of_array; i++) {

  

           //add current element to current_sum

           current_sum = current_sum + A[i];

  

           //update the max sum

           if(current_sum>max_sum) {

               max_sum = current_sum;

           }

  

           //don't carry negative current_sum

           if(current_sum < 0) {

               current_sum = 0;

           }       

  

}

   return max_sum;

  

   }

}

**
```