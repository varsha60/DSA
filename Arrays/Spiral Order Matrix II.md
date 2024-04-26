**Problem Description

Given an integer A, generate a square matrix filled with elements from 1 to A2 in spiral order and return the generated square matrix.

  
  
Problem Constraints

1 <= A <= 1000

  
  
Input Format

First and only argument is integer A

  
  
Output Format

Return a 2-D matrix which consists of the elements added in spiral order.

  
  
Example Input

Input 1:

1

  

Input 2:

2

  

Input 3:

5

  

  
  
Example Output

Output 1:

[ [1] ]

  

Output 2:

[ [1, 2],

 [4, 3] ]

  

Output 2:

[ [1,   2,  3,  4, 5],

 [16, 17, 18, 19, 6],

 [15, 24, 25, 20, 7],

 [14, 23, 22, 21, 8],

 [13, 12, 11, 10, 9] ]

  

  
  
Example Explanation

Explanation 1:

Only 1 is to be arranged.

Explanation 2:

1 --> 2

      |

      |

4<--- 3

  

Explanation 3:

![](https://lh7-us.googleusercontent.com/BH_mVA5ugPYlXCW1NfMjBgUqy2L1VfyIdqXyfOk0jDRz765HMM4PpemXLsyF0Xu8HQ8e4yVvqdkTDGbJiHEC9aZESbL8b9iFSJrw9y11XkABv4iVjMsmbRv7Bc4bpf6HlIIOBGG7PDkqqRH4zSbZzCA)

  

Can you think of a sliding window in the arrow directions?**

```java
**

public class Solution {

   public int[][] generateMatrix(int A) {

  

       //Size of Resultant Matrix - A*A

       int [][] result = new int [A][A];

  

       int element_to_fill = 1;

       int i = 0, j = 0;

       while(A > 1) {

  

           for(int k = 1; k <= A-1; k++) {

               result[i][j] = element_to_fill;

               element_to_fill++;

               j++;

           }

  

           for(int k = 1; k <= A-1; k++) {

               result[i][j] = element_to_fill;

               element_to_fill++;

               i++;

           }

  

           for(int k = 1; k <= A-1; k++) {

               result[i][j] = element_to_fill;

               element_to_fill++;

               j--;

           }

  

           for(int k = 1; k <= A-1; k++) {

               result[i][j] = element_to_fill;

               element_to_fill++;

               i--;

           }

  

           i++;

           j++;

           A = A - 2;

       }

  

       if(A == 1) {

               result[i][j] = element_to_fill;

           }

  

       return result;

  

   }

}

  


**
```