**

Problem Description

You are given a 2D integer matrix A, make all the elements in a row or column zero if the A[i][j] = 0. Specifically, make entire ith row and jth column zero.

  
  
Problem Constraints

1 <= A.size() <= 103

1 <= A[i].size() <= 103

0 <= A[i][j] <= 103

  
  
Input Format

First argument is a 2D integer matrix A.

  
  
Output Format

Return a 2D matrix after doing required operations.

  
  
Example Input

Input 1:

[1,2,3,4]

[5,6,7,0]

[9,2,0,4]

  
  
Example Output

Output 1:

[1,2,0,0]

[0,0,0,0]

[0,0,0,0]

  
  
Example Explanation

Explanation 1:

A[2][4] = A[3][3] = 0, so make 2nd row, 3rd row, 3rd column and 4th column zero.

**

```java
**

public class Solution {

   public int[][] solve(int[][] A) {

  

       /*

  

To Understand approaches in depth refer below:

       https://takeuforward.org/data-structure/set-matrix-zero/       

       */

  

       //Better approach with extra space.

  

       // int N = A.length; //Number of Rows

       // int M = A[0].length; //Number of Columns

  

       // int [] rowToMark = new int [N];

       // int [] colToMark = new int [M];

  

  

       // //What to be made 0 later on

       // for(int i=0;i<N;i++) {

       //     for (int j=0; j<M; j++) {

       //         if(A[i][j] == 0)

       //         {

       //             rowToMark[i] = 1;

       //             colToMark[j] = 1;

       //         }

       //     }

       // }

  

       // //Now check marked to be 0 or not

       // for(int i=0; i<N; i++) {

       //     for(int j=0;j<M; j++) {

       //         if(rowToMark[i] == 1 || colToMark[j] == 1) {

       //             A[i][j] = 0;

       //         }

       //     }

       // }

  

  

      //Optimal Approach with No Extra Space

  

       int N = A.length; //Number of Rows

       int M = A[0].length; //Number of Columns

  

  

       int col0ToMark = 1;

  

       //int [] rowToMark = new int [N]; --- A[..][0]

       //int [] colToMark = new int [M]; --- A[0][..]

  

  

       //What to be made 0 later on

       for(int i=0;i<N;i++) {

           for (int j=0; j<M; j++) {

               if(A[i][j] == 0)

               {

                   //mark ith row

                   A[i][0] = 0;

  

                   if(j!= 0) {

                       //mark jth col

                       A[0][j] = 0;

                   }

                   else {

                       //mark jth col

                       //extra col variable taken for this purpose.

                       col0ToMark = 0;

                   }

               }

           }

       }

  

       //Now check marked to be 0 or not

  

       //first row and first col determines what do we need to do so leave them alone for a while.

       //mark other rows and columns

       for(int i=1; i<N; i++) {

           for(int j=1;j<M; j++) {

               if(A[i][0] == 0 || A[0][j] == 0) {

                   A[i][j] = 0;

               }

           }

       }

  

       //now mark first row.

       if(A[0][0] == 0) {

           for (int j=0; j<M; j++) {

               A[0][j] = 0;

           }

       }

  

       //now mark first col.

       if(col0ToMark == 0) {

           for (int i=0; i<N; i++) {

               A[i][0] = 0;

           }

       }

  

  

       return A;

  

  

   }

}

  


**
```