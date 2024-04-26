**Problem Description

Given an integer A, find and return the total number of digit 1 appearing in all non-negative integers less than or equal to A.

  
  
Problem Constraints

0 <= A <= 109

  
  
Input Format

The only argument given is the integer A.

  
  
Output Format

Return the total number of digit 1 appearing in all non-negative integers less than or equal to A.

  
  
Example Input

Input 1:

A = 10

Input 2:

A = 11

  
  
Example Output

Output 1:

2

Output 2:

4

  
  
Example Explanation

Explanation 1:

Digit 1 appears in 1 and 10 only and appears one time in each. So the answer is 2.

Explanation 2:

Digit 1 appears in 1(1 time) , 10(1 time) and 11(2 times) only. So the answer is 4.

  

TODO: Explanation.**

```java
**

public class Solution {

  

   //Gives TLE  - O(N) solution - constraints are 10^9

   // public int solve(int A) {

  

   //     if(A==0)

   //         return 0;

  

   //     int countOfOne = 0;

  

   //     for(int i=1; i<=A; i++) {

   //         //System.out.println("Checking for i: " + i);

  

   //         int j = i;

  

   //         while(j>=1) {

   //             int extractedDigit = j%10;

   //             //System.out.println(extractedDigit);

   //             if(extractedDigit == 1) {

   //                 countOfOne++;

   //             }

   //             //System.out.println(countOfOne);

   //             j=j/10;

   //             //System.out.println(j);

   //         }

   //     }

  

   //     return countOfOne;

   // }

  

   public int solve(int A) {

  

       if(A==0)

           return 0;

  

       int countOfOne = 0;

       int temp = A;

       int i = 1;

  

       while(temp/i > 0) {

           countOfOne = countOfOne + (temp/(i*10))*i + Math.min((Math.max((temp%(i*10))-(i-1),0)),i);

           i = i*10;

       }

  

       return countOfOne;

   }

}

**
```