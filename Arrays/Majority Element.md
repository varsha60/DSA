**

Problem Description

Given an array of size N, find the majority element. The majority element is the element that appears more than floor(n/2) times.

You may assume that the array is non-empty and the majority element always exists in the array.

  
  
Problem Constraints

1 <= N <= 5*105

1 <= num[i] <= 109

  
  
Input Format

Only argument is an integer array.

  
  
Output Format

Return an integer.

  
  
Example Input

Input 1:

[2, 1, 2]

  

Input 2:

[1, 1, 1]

  

  
  
Example Output

Input 1:

2

  

Input 2:

1

  

  
  
Example Explanation

For Input 1:

2 occurs 2 times which is greater than 3/2.

  

For Input 2:

1 is the only element in the array, so it is majority

  
  
  
  
  

Life and Candidate Game - ? Think and Pause !

  
  
**

```java
**

public class Solution {

   // DO NOT MODIFY THE ARGUMENTS WITH "final" PREFIX. IT IS READ ONLY

   //https://www.youtube.com/watch?v=U1-mSBZFvqw&ab_channel=CodewithAlisha

   public int majorityElement(final int[] A) {

  

       int N = A.length;

  

       int life = 0;

       int candidate = Integer.MIN_VALUE;

  

       for(int i =0;i<N;i++) {

  

          if(A[i] == candidate) {

              //Current player is in majority

              life++;

          }

          else if(life == 0) {

              //No player is in majority

              candidate = A[i];

              life = 1;

          }

          else

          //Majority element is overpowered or shooted by some other element

           life--;

       }

  

       return candidate;

   }

}

**
```