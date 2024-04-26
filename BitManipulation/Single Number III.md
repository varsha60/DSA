**

Problem Description

Given an array of positive integers A, two integers appear only once, and all the other integers appear twice.  
Find the two integers that appear only once.

Note: Return the two numbers in ascending order.

  
  
Problem Constraints

2 <= |A| <= 100000  
1 <= A[i] <= 109

  
  
Input Format

The first argument is an array of integers of size N.

  
  
Output Format

Return an array of two integers that appear only once.

  
  
Example Input

Input 1:

A = [1, 2, 3, 1, 2, 4]

  

Input 2:

A = [1, 2]

  

  
  
Example Output

Output 1:

[3, 4]

Output 2:

[1, 2]

  
  
Example Explanation

Explanation 1:

3 and 4 appear only once.

  

Explanation 2:

1 and 2 appear only once.

**

```java
**

public class Solution {

  

   boolean checkBit(int i, int A) {

       if((A&(1<<i))!=0) return true;

  

       return false;

   }

   public int[] solve(int[] A) {

       //use XOR property - both bits should be different to get set bit.

       //a^a = 0

  

       int resultant_xor = 0;

  

       int N = A.length;

  

       int [] result = new int[2];

       Arrays.fill(result,0);

  

       //xor everything to get resultant xor - at the end you will have xor of 2 unique elements.

       for(int i=0;i<N;i++) {

           resultant_xor = resultant_xor ^ A[i];

       }

  

       //check at what position do we have bit set

       int pos = 0;

       for(pos=0; pos<32; pos++) {

           if(checkBit(pos,resultant_xor))

               break;

       }

  

       //now at this position check if bit is set or unset in array elements and separate out in pairs

       for(int i=0; i<N; i++) {

  

           if(checkBit(pos,A[i])) {

               //bit is set

               result[0] = result[0] ^ A[i];

           }

           else

           //bit is not set

                 result[1] = result[1] ^ A[i];

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