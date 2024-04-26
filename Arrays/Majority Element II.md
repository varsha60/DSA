**

Problem Description

You're given a read-only array of N integers. Find out if any integer occurs more than N/3 times in the array in linear time and constant additional space.

If so, return the integer. If not, return -1.

If there are multiple solutions, return any one.

Note: Read-only array means that the input array should not be modified in the process of solving the problem

  
  
Problem Constraints

1 <= N <= 7*105

1 <= A[i] <= 109

  
  
Input Format

The only argument is an integer array A.

  
  
Output Format

Return an integer.

  
  
Example Input

Input 1:

[1 2 3 1 1]

  

Input 2:

[1 2 3]

  

  
  
Example Output

Output 1:

1

  

Output 2:

-1

  

  
  
Example Explanation

Explanation 1:

1 occurs 3 times which is more than 5/3 times.

  

Explanation 2:

No element occurs more than 3 / 3 = 1 times in the array.

**

```java
**

public class Solution {

   public int repeatedNumber(int[] A) {

  

       int N = A.length;

  

       int life1 = 0;

       int candidate1 = Integer.MIN_VALUE;

  

       int life2 = 0;

       int candidate2 = Integer.MIN_VALUE;

  

       for(int i =0;i<N;i++) {

  

          if(A[i] == candidate1) {

              //Current player 1 is in majority

              life1++;

          }

          else if(A[i] == candidate2) {

              //Current player 2 is in majority

              life2++;

          }

          else if(life1 == 0) {

              //No player is in majority

              candidate1 = A[i];

              life1 = 1;

          }

           else if(life2 == 0) {

              //No player is in majority

              candidate2 = A[i];

              life2 = 1;

          }

          else {

              //Majority element is overpowered or shooted by some other element

           life1--;

           life2--;

  

          }

       }

  

       int countOfCandidate1 = 0;

       int countOfCandidate2 = 0;

  

       for(int i=0; i<N; i++) {

  

           if(A[i] == candidate1)

           {countOfCandidate1++;}

           if(A[i] == candidate2)

           {countOfCandidate2++;}

  

       }

       if(countOfCandidate1>N/3)

           return candidate1;

       if(countOfCandidate2>N/3)

           return candidate2;

  

  

return -1;

   }

}

**
```