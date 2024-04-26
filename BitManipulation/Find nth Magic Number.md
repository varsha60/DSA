**

Problem Description

Given an integer A, find and return the Ath magic number.

A magic number is defined as a number that can be expressed as a power of 5 or a sum of unique powers of 5.

First few magic numbers are 5, 25, 30(5 + 25), 125, 130(125 + 5), ….

  
  
Problem Constraints

1 <= A <= 5000

  
  
Input Format

The only argument given is integer A.

  
  
Output Format

Return the Ath magic number.

  
  
Example Input

Example Input 1:

A = 3

Example Input 2:

A = 10

  
  
Example Output

Example Output 1:

30

Example Output 2:

650

  
  
Example Explanation

Explanation 1:

Magic Numbers in increasing order are [5, 25, 30, 125, 130, ...]

 3rd element in this is 30

Explanation 2:

In the sequence shown in explanation 1, 10th element will be 650.

  

  
  

Think and Pause - 3 - binary representation is 1 1 - final answer is 52 + 51.

**

```java
**

public class Solution {

   public int solve(int A) {

  

       int ans = 0;

       int power = 5;

       int remainder = 0;

  

       while(A>0) {

           remainder = A%2;

           A = A/2;

           ans = ans + remainder*power;

           power = power * 5;

       }

  

       return ans;

   }

}

**
```