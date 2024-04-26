
**

Problem Description

Given two binary strings A and B. Return their sum (also a binary string).

  
  
Problem Constraints

1 <= length of A <= 105

1 <= length of B <= 105

A and B are binary strings

  
  
Input Format

The two argument A and B are binary strings.

  
  
Output Format

Return a binary string denoting the sum of A and B

  
  
Example Input

Input 1:

A = "100"

B = "11"

  

Input 2:

A = "110"

B = "10"

  

  
  
Example Output

Output 1:

"111"

  

Output 2:

"1000"

  

  
  
Example Explanation

For Input 1:

The sum of 100 and 11 is 111.

  

For Input 2:

  

The sum of 110 and 10 is 1000.

  
  
**

```java
**

public class Solution {

   public String addBinary(String A, String B) {

  

  

//Value too large - below approach does not work.

   //    int a = binaryToDecimal(Integer.parseInt(A));

   //    int b = binaryToDecimal(Integer.parseInt(B));

   //    int answer = decimalToBinary(a+b);

   //    return String.valueOf(answer);

  

   int carry = 0;

   int i = A.length()-1;

   int j = B.length()-1;

   String answer = "";

  

   while(i>=0 || j>=0 || carry>0) {

       int sum = 0;

       if(i>=0) {

           sum = sum + (A.charAt(i)-'0'); //to get integer

           i--;

       }

  

       if(j>=0) {

           sum = sum + (B.charAt(j)-'0');

           j--;

       }

  

       sum = sum + carry;

  

       int bit = sum%2; //modulo stays

       carry = sum/2; //carry goes

  

       answer = answer + (char) (bit + '0');

   }

  

   StringBuilder str = new StringBuilder(answer);

   return str.reverse().toString();

  

  

   }

  

   private int binaryToDecimal(int A) {

  

       int result = 0;

       int multiplicationNumber = 1;

  

       while(A>0) {

           //Extract last digit and multiply with multiplicationNumber

           result = result + (A%10)*multiplicationNumber;

           multiplicationNumber = multiplicationNumber * 2;

           A = A/10;          

       }

  

       return result;

   }

  

private int decimalToBinary(int A) {

  

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

  

          int remainder = A%2;

           result += remainder*multiplicationNumber;

           multiplicationNumber *=10;

           A /=2;

       }

       return result;

   }

}

  


**
```