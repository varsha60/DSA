**

Problem Description

Given an array A of length N where all the elements are distinct and are in the range [1, N+2].

Two numbers from the range [1, N+2] are missing from the array A. Find the two missing numbers.

  
  
Problem Constraints

1 <= N <= 105

1 <= A[i] <= N+2

The elements of array A are distinct

  
  
Input Format

Only argument A is an array of integers

  
  
Output Format

Return a sorted array of size 2 denoting the missing elements.

  
  
Example Input

Input 1:

A = [3, 2, 4]

  

Input 2:

A = [5, 1, 3, 6]

  
  
Example Output

Output 1:

[1, 5]

  

Output 2:

[2, 4]

  

  
  
Example Explanation

For Input 1:

The missing numbers are 1 and 5.

  

For Input 2:

The missing numbers are 2 and 4.

  

Think and Pause - It is on similar lines as single number III

**

```java
**

public class Solution {

  

   boolean checkBit(int i, int A) {

       if((A&(1<<i))!=0) return true;

  

   return false;

  

   }

  

   public int[] solve(int[] A) {

  

       int N = A.length;

  

       int resultantXor = 0;

  

       int [] result = new int [2];

       Arrays.fill(result,0);

  

       for(int i=1; i<=N+2; i++) {

           resultantXor = resultantXor ^ i;

       }

  

       for(int i=0; i<N; i++) {

           resultantXor = resultantXor ^ A[i];

       }

  

       int pos = 0; //position where bit is set

       for(pos=0; pos<32; pos++) {

           if(checkBit(pos,resultantXor))

               break;

       }

  

       for(int i=0; i<N; i++) {

           if(checkBit(pos,A[i])) {

               //bit is set

               result[0] = result[0] ^ A[i];

           }

           else

               //bit is unset

               result[1] = result[1] ^ A[i];

       }

  

       for(int i=1; i<=N+2; i++) {

           if(checkBit(pos,i)) {

               //bit is set

               result[0] = result[0] ^ i;

           }

           else

               //bit is unset

               result[1] = result[1] ^ i;

       }

  

       if(result[0]>result[1]) {

           int temp = result[0];

           result[0] = result[1];

           result[1] = temp;

       }

  

  

       return result;

   }

}

  


**
```