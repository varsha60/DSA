**Problem Description

Given an array of integers A and an integer B, find and return the minimum number of swaps required to bring all the numbers less than or equal to B together.

Note: It is possible to swap any two elements, not necessarily consecutive.

  
  

Problem Constraints

1 <= length of the array <= 100000  
-109 <= A[i], B <= 109

  
  

Input Format

The first argument given is the integer array A.  
The second argument given is the integer B.

  
  

Output Format

Return the minimum number of swaps.

  
  

Example Input

Input 1:

A = [1, 12, 10, 3, 14, 10, 5]

 B = 8

Input 2:

A = [5, 17, 100, 11]

 B = 20

  
  

Example Output

Output 1:

2

Output 2:

1

  
  

Example Explanation

Explanation 1:

A = [1, 12, 10, 3, 14, 10, 5]

 After swapping  12 and 3, A => [1, 3, 10, 12, 14, 10, 5].

 After swapping  the first occurence of 10 and 5, A => [1, 3, 5, 12, 14, 10, 10].

 Now, all elements less than or equal to 8 are together.

  

Explanation 2:

A = [5, 17, 100, 11]

 After swapping 100 and 11, A => [5, 17, 11, 100].

 Now, all elements less than or equal to 20 are together.

  

Can you think of what can be window size here?**

```java
**

public class Solution {

   public int solve(int[] A, int B) {

  

       /*

       1. Find how many elements are less than B - this will give window size.

       2. Use sliding window approach and for every window find how many bad elements are there.

       3. Bad elements is nothing but how many numbers in given window are greater than B.

       4. Greater the bad elements greater swap will be required so choose the one with minimum number.

       */

  

//TLE ERROR FOR BELOW SOLUTION.

       // int N = A.length;

       // int K = 0;

       // int E = 0;

       // int minimum_swaps = Integer.MAX_VALUE;

  

       // for(int i=0;i<N;i++) {

  

       //     if(A[i]<=B) {

       //         K++;

       //     }

       // }

  

  

       // for(int S=0; S<=N-K; S++) {

  

       //     E = S + K - 1;

  

       //     int bad_element_count = 0;

  

       //     for(int j=S; j<=E; j++) {

       //         if(A[j] > B) {

       //             bad_element_count++;

       //         }

       //     }

  

       //     if(bad_element_count < minimum_swaps) {

       //         minimum_swaps = bad_element_count;

       //     }

  

       // }

  

       // return minimum_swaps;

  

  

       int N=A.length;

  

       int window_size=0; // count the number of elements which is <=B

  

       for(int i=0;i<N;i++){

           if(A[i]<=B){

               window_size++;

           }

       }

       // Edge Case : for single element we do not need swaps so return 0

       if(window_size<=1){

           return 0;

       }

  

       // First window: from 0 to window_size-1

  

       int bad_element_count=0; //jinko swap krna hai.

  

       for(int i=0;i<window_size;i++){

           if(A[i]>B){

               bad_element_count++;

           }

       }

  

       int minimum_swaps=bad_element_count; //Initializing with first window element count. jaise apan sum main krte hai

  

       // window from 1 to n-1

       int i=1,j=window_size;

  

//Jabtak J less than N hai - end of window is less than N - within array range.

       while(j<N){

  

           //Checking - agar previous element <=B hai toh it is not contributing to bad_element_count

           if(A[i-1] <= B && A[j] > B){

               bad_element_count++; //Naya vala element bad hai

           }

  

           //Checking - agar previous element >B hai toh it was contributing to bad_element_count in previous window.

           if(A[i-1] > B && A[j] <= B){

               bad_element_count--; //Naya vala element good hai

           }

  

           minimum_swaps=Math.min(minimum_swaps,bad_element_count);

           i++;

           j++;

       }

       return minimum_swaps;

  

   }

}

**
```