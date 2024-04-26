**Problem Description

Given a decimal number A and a base B, convert it into its equivalent number in base B.

  
  
Problem Constraints

0 <= A <= 512

2 <= B <= 10

  
  
Input Format

The first argument will be decimal number A.

The second argument will be base B.

  
  
Output Format

Return the conversion of A in base B.

  
  
Example Input

Input 1:

A = 4

B = 3

Input 2:

A = 4

B = 2

  
  
Example Output

Output 1:

11

Output 2:

100

  
  
Example Explanation

Explanation 1:

Decimal number 4 in base 3 is 11.

Explanation 2:

Decimal number 4 in base 2 is 100.

  
  

HINT - Solve on pen and paper and then code step by step. 

Main trick here is how would you reverse? Zoom in on that.**

```java
**

public class Solution {

   public int DecimalToAnyBase(int A, int B) {

  

       //

  

//Yaha sawal sirf reverse krne ka hai

       // 123 - ko reverse kaise karegi?

       //123 reverse is nothing but 321 ~~ 300 + 21 + 1 ~~ 3*100 + 2*10 + 1*1 ~~ 3*10^2 + 2*10^1 + 1*10^0

       // so in first iteration let's say you get remainder as 1 ~~ 1*10^0 + 0 = 1

       //Second iteration, you get remainder as 2 ~~ 2*10^1 + 1 = 21

       //Third iteration, you get remainder 3 ~~ 3*10^2 + 21 = 321

  

       int result=0;

       int multiplicationNumber= 1;

       while(A>0) {

  

          int remainder = A%B;

           result += remainder*multiplicationNumber;

           multiplicationNumber *=10;

           A /=B;

       }

       return result;

   }

}

**
```