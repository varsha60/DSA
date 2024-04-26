**

Problem Description

Give a N * N square matrix A, return an array of its anti-diagonals. Look at the example for more details.

  
  
Problem Constraints

1<= N <= 1000

1<= A[i][j] <= 1e9

  
  
Input Format

Only argument is a 2D array A of size N * N.

  
  
Output Format

Return a 2D integer array of size (2 * N-1) * N, representing the anti-diagonals of input array A.

The vacant spaces in the grid should be assigned to 0.

  
  
Example Input

Input 1:

1 2 3

4 5 6

7 8 9

  

Input 2:

1 2

3 4

  

  
  
Example Output

Output 1:

1 0 0

2 4 0

3 5 7

6 8 0

9 0 0

  

Output 2:

1 0

2 3

4 0

  

  
  
Example Explanation

For input 1:

The first anti diagonal of the matrix is [1 ], the rest spaces shoud be filled with 0 making the row as [1, 0, 0].

The second anti diagonal of the matrix is [2, 4 ], the rest spaces shoud be filled with 0 making the row as [2, 4, 0].

The third anti diagonal of the matrix is [3, 5, 7 ], the rest spaces shoud be filled with 0 making the row as [3, 5, 7].

The fourth anti diagonal of the matrix is [6, 8 ], the rest spaces shoud be filled with 0 making the row as [6, 8, 0].

The fifth anti diagonal of the matrix is [9 ], the rest spaces shoud be filled with 0 making the row as [9, 0, 0].

  

For input 2:

The first anti diagonal of the matrix is [1 ], the rest spaces shoud be filled with 0 making the row as [1, 0, 0].

The second anti diagonal of the matrix is [2, 4 ], the rest spaces shoud be filled with 0 making the row as [2, 4, 0].

The third anti diagonal of the matrix is [3, 0, 0 ], the rest spaces shoud be filled with 0 making the row as [3, 0, 0].

  
  

Hint - how would you do it If I ask you to print only 1 diagonal?

**

```java
**

public class Solution {

   public ArrayList<ArrayList<Integer>> diagonal(ArrayList<ArrayList<Integer>> A) {

  

        /*

  

       AntiDiagonal - all diagonals starting from Right to Left.

       1. Somehow find start points of all diagonals.

       2. Iterate starting points and print diagonals one by one.

       3. Store in the new Matrix.

  

       Tip - Use dynamic array instead of array (very very tricky to think index of new ans array)

       */

  

       int N = A.size();

       ArrayList<ArrayList<Integer>> antiDiagonals = new ArrayList<ArrayList<Integer>>();

  

       int row,col = 0;

  

       int i=0;

       for(int j=0;j<N;j++) {

  

           row=i; //row iterator

           col=j; //col iterator

  

           //List which will store individual antidiagonal

           ArrayList<Integer> antiDiagonal = new ArrayList<Integer>();

  

           while(row<N && col>-1) {

  

               antiDiagonal.add(A.get(row).get(col));

               row++;

               col--;

           }

  

           //Fill empty space with 0 in List - Observation longest diagonal 0 to N-1 row will be each list size

           while(antiDiagonal.size()<A.size())

            {

                antiDiagonal.add(0);

            }

  

            antiDiagonals.add(antiDiagonal);     

  

       }

  

       int j=N-1;

  

       for(i=1;i<N;i++) {

  

           //List which will store individual antidiagonal

           ArrayList<Integer> antiDiagonal = new ArrayList<Integer>();

  

           row=i; //row iterator

           col=j; //col iterator

  

           while(row<N && col>-1) {

  

               antiDiagonal.add(A.get(row).get(col));

               row++;

               col--;

           }

  

           while(antiDiagonal.size()<A.size())

            {

                antiDiagonal.add(0);

            }

  

            antiDiagonals.add(antiDiagonal);   

       }

  

       return antiDiagonals;

   }

   }

  


**
```