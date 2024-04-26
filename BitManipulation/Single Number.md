**Problem Description

Given an array of integers A, every element appears twice except for one. Find that integer that occurs once.  
  
NOTE: Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?

  
  
Problem Constraints

- 1 <= |A| <= 2000000
    
- 0 <= A[i] <= INTMAX
    

  
  
Input Format

The first and only argument of input contains an integer array A.

  
  
Output Format

Return a single integer denoting the single element.

  
  
Example Input

Input 1:

A = [1, 2, 2, 3, 1]

Input 2:

A = [1, 2, 2]

  
  
Example Output

Output 1:

3

Output 2:

1

  
  
Example Explanation

Explanation 1:

3 occurs once.

  

Explanation 2:

1 occurs once.

  

HINT: Is there any property that you know of which cancels out numbers? And can you think why it is canceling out?**

```java
**

public class Solution {

   // DO NOT MODIFY THE ARGUMENTS WITH "final" PREFIX. IT IS READ ONLY

   public int singleNumber(final int[] A) {

  

       //Use XOR property. a^b^a^c^b -- c (a^a is 0 and 0^c is c)

  

       int N = A.length;

       int result = 0;

  

       for(int i=0; i<N; i++) {

  

           result = result ^ A[i];

  

       }

  

       return result;

   }

}

**
```