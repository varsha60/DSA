
Problem Description

Given an integer array A of size N and an integer B, you have to return the same array after rotating it B times towards the right.

  
  
Problem Constraints

1 <= N <= 105

1 <= A[i] <=109

1 <= B <= 109

  
  
Input Format

The first argument given is the integer array A.

The second argument given is the integer B.

  
  
Output Format

Return the array A after rotating it B times to the right

  
  
Example Input

Input 1:

A = [1, 2, 3, 4]

B = 2

Input 2:

A = [2, 5, 6]

B = 1

  
  
Example Output

Output 1:

[3, 4, 1, 2]

Output 2:

[6, 2, 5]

  
  
Example Explanation

Explanation 1:

Rotate towards the right 2 times - [1, 2, 3, 4] => [4, 1, 2, 3] => [3, 4, 1, 2]

Explanation 2:

Rotate towards the right 1 time - [2, 5, 6] => [6, 2, 5]

**

```java

public class Solution {

   public int[] solve(int[] A, int B) {

  

       /* Brute Force

       loop from 1 to B

       Store last element in temp

       loop from last to first and keep on shifting j-1 to jth place

       TC - N*B

  

       int N = A.length;

       int temp;

  

       for(int i=1; i<=B; i++)

       {

           temp = A[N-1];

           for(int j=N-1; j>=1; j--)

           {

               A[j] = A[j-1];

           }

           A[0]=temp;

       }

  

       Optimized Solution

       1. Reverse 0 to N-1

       2. Reverse 0 to K%N-1

       3. Reverse K%N to N-1

  

       Mod N isiliye kyuki if K>=N toh reverse stages will repeat itself

       let's say N is 5 and K is 5

       so K=0 ho ya K=5 ho answer same ayega rotate array ka.

       Effective rotation will be K%N , 5%5 - 0 10%5 - 0

  

       TC - N

        */

  

        int N = A.length;

  

        reverse(A,N,0,N-1);

        reverse(A,N,0,B%N-1);

        reverse(A,N,B%N,N-1);

  

       return A;

   }

  

   public void reverse(int[] A,int N,int i, int j)

   {

       int temp = A[0];

       while(i<j)

       {

           temp = A[i];

           A[i] = A[j];

           A[j] = temp;

           i++;

           j--;

       }

   }

}

  

  
**
```