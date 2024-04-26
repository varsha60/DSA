**

Problem Description

Given an array, arr[] of size N, the task is to find the count of array indices such that removing an element from these indices makes the sum of even-indexed and odd-indexed array elements equal.

  
  
Problem Constraints

1 <= N <= 105

-105 <= A[i] <= 105

Sum of all elements of A <= 109

  
  
Input Format

First argument contains an array A of integers of size N

  
  
Output Format

Return the count of array indices such that removing an element from these indices makes the sum of even-indexed and odd-indexed array elements equal.

  
  
Example Input

Input 1:

A = [2, 1, 6, 4]

  

Input 2:

A = [1, 1, 1]

  

  
  
Example Output

Output 1:

1

  

Output 2:

3

  

  
  
Example Explanation

Explanation 1:

Removing arr[1] from the array modifies arr[] to { 2, 6, 4 } such that, arr[0] + arr[2] = arr[1]. 

Therefore, the required output is 1. 

  

Explanation 2:

Removing arr[0] from the given array modifies arr[] to { 1, 1 } such that arr[0] = arr[1] 

Removing arr[1] from the given array modifies arr[] to { 1, 1 } such that arr[0] = arr[1] 

Removing arr[2] from the given array modifies arr[] to { 1, 1 } such that arr[0] = arr[1] 

Therefore, the required output is 3.

  
  

Hint - Observe what is happening to indices?

**

```java
**

public class Solution {

   public int solve(int[] A) {

  

  

       int N = A.length;

       int [] prefixArrayEvenSum = new int[N];

       int [] prefixArrayOddSum = new int [N];

  

       int specialIndexCount = 0;

       prefixArrayEvenSum[0] = A[0];

  

       //Construct prefix array for even indices

       for(int i=1;i<N;i++) {

           if(i%2 == 0) {

               //even index - add a[i] to previous sum

               prefixArrayEvenSum[i] = prefixArrayEvenSum[i-1] + A[i];

           }

       else {

           //odd index - store previous even sum only

           prefixArrayEvenSum[i] = prefixArrayEvenSum[i-1];

       }

  

   }

  

  

   //Construct prefix array for odd indices.

       prefixArrayOddSum[0] = 0; //even index should not affect odd index sum

  

       for(int i=1; i<N; i++) {

           if(i%2 != 0) { //odd index

               prefixArrayOddSum[i] = prefixArrayOddSum[i-1] + A[i];

           }

           else { //even index

               prefixArrayOddSum[i] = prefixArrayOddSum[i-1];

           }

       }

  

//Iterate through array and check sEven = sOdd

       for(int i=0; i<N; i++) {

  

           int sumOfEvenIndices = 0;

           int sumOfOddIndices = 0;

  

           sumOfEvenIndices = prefixArrayOddSum[N-1] - prefixArrayOddSum[i];

           if(i!=0) {

               //left part to removed index will exists

               sumOfEvenIndices = sumOfEvenIndices + prefixArrayEvenSum[i-1];

           }

  

  

           sumOfOddIndices = prefixArrayEvenSum[N-1] - prefixArrayEvenSum[i];

           if(i!=0) {

               //left part to removed index will exists

               sumOfOddIndices = sumOfOddIndices + prefixArrayOddSum[i-1];

           }

  

  

           if(sumOfEvenIndices == sumOfOddIndices) {

               specialIndexCount++;

           }

       }

  

       return specialIndexCount;

  

   }

}

  


**
```