**

Problem Description

Given an array of integers, every element appears thrice except for one, which occurs once.  
  
Find that element that does not appear thrice.  
  
NOTE: Your algorithm should have a linear runtime complexity.  
  
Could you implement it without using extra memory?  
  

  
  
Problem Constraints

- 2 <= A <= 5*106
    
- 0 <= A <= INTMAX
    

  
  
Input Format

First and only argument of input contains an integer array A.

  
  
Output Format

Return a single integer.

  
  
Example Input

Input 1:

A = [1, 2, 4, 3, 3, 2, 2, 3, 1, 1]

Input 2:

A = [0, 0, 0, 1]

  
  
Example Output

Output 1:

4

Output 2:

1

  
  
Example Explanation

Explanation 1:

4 occurs exactly once in Input 1.

 1 occurs exactly once in Input 2.

  

Think and Pause - write the number in binary format and observe. 

Single Number was straight forward using xor but why were they canceling each other out? Can you think of that?

**

```java
**public class Solution {

   // DO NOT MODIFY THE ARGUMENTS WITH "final" PREFIX. IT IS READ ONLY

  

   boolean checkBit(int i, int A) {

       //bit is set

       if((A&(1<<i))!=0) return true;

       //bit is unset

       return false;

   }

   public int singleNumber(final int[] A) {

  

       int uniqueNumber = 0;

  

       for(int i=0; i<32; i++) {

  

           int countSetBit = 0;

  

           for(int j=0; j<A.length; j++) {

  

               if(checkBit(i,A[j]))

                   countSetBit++;

  

           }

  

           if(countSetBit % 3 !=0) {

               //not a multiple of 3

  

               //so set bit

               uniqueNumber = (uniqueNumber | (1<<i));

           }

  

       }

  

       return uniqueNumber;

   }

}

  

  

//Similar approach can be followed for single number question as well.**
```