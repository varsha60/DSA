**Problem Description

You are given an integer array A of size N.

You have to perform B operations. In one operation, you can remove either the leftmost or the rightmost element of the array A.

Find and return the maximum possible sum of the B elements that were removed after the B operations.

NOTE: Suppose B = 3, and array A contains 10 elements, then you can:

- Remove 3 elements from front and 0 elements from the back, OR
    
- Remove 2 elements from front and 1 element from the back, OR
    
- Remove 1 element from front and 2 elements from the back, OR
    
- Remove 0 elements from front and 3 elements from the back.
    

  
  
Problem Constraints

1 <= N <= 105

1 <= B <= N

-103 <= A[i] <= 103

  
  
Input Format

First argument is an integer array A.

Second argument is an integer B.

  
  
Output Format

Return an integer denoting the maximum possible sum of elements you removed.

  
  
Example Input

Input 1:

A = [5, -2, 3 , 1, 2]

 B = 3

  

Input 2:

A = [ 2, 3, -1, 4, 2, 1 ]

 B = 4

  

  
  
Example Output

Output 1:

8

  

Output 2:

9

  

  
  
Example Explanation

Explanation 1:

Remove element 5 from front and element (1, 2) from back so we get 5 + 1 + 2 = 8

  

Explanation 2:

Remove the first element and the last 3 elements. So we get 2 + 4 + 2 + 1 = 9

  
  
  

Hint - Can Prefix and Suffix Sum help here? Think and pause!**

```java
**public class Solution {

   public int solve(int[] A, int B) {

  

       //Approach One - TC - O(n) and SC - O(n)

       int N = A.length;

       int [] P = new int[N];

       int [] S = new int[N];

       int maximum_sum = Integer.MIN_VALUE;

  

       int prefix_index = 0;

       int suffix_index = 0;

  

  

       P[0] = A[0];

       S[N-1] = A[N-1];

  

       for(int i=1; i<N; i++) {

           P[i] = P[i-1] + A[i];

       }

  

       for(int i=N-2; i>=0; i--) {

           S[i] = S[i+1] + A[i];

       }

  

       for(int i=0; i<=B;i++) {

  

           int sum = 0;

  

           prefix_index = i - 1;

           suffix_index = N - (B-i);

  

           if(prefix_index > -1 && suffix_index < N)

           {

               sum = P[prefix_index] + S[suffix_index];

           }

  

           if(prefix_index == -1) {

               sum = S[suffix_index];

           }

  

           if(suffix_index >= N) {

               sum = P[prefix_index];

  

           }

  

           if(sum>maximum_sum) {

               maximum_sum = sum;

           }

  

       }

  

       return maximum_sum;

  

  

  

   }

}

  

  

For a space optimized approach refer carry forward technique.**
```