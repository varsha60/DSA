**

Problem Description

Akash likes playing with strings. One day he thought of applying following operations on the string in the given order:

Concatenate the string with itself.

Delete all the uppercase letters.

Replace each vowel with '#'.

You are given a string A of size N consisting of lowercase and uppercase alphabets. Return the resultant string after applying the above operations.

NOTE: 'a' , 'e' , 'i' , 'o' , 'u' are defined as vowels.

  
  
Problem Constraints

1<=N<=100000

  
  
Input Format

First argument is a string A of size N.

  
  
Output Format

Return the resultant string.

  
  
Example Input

Input 1:

A="aeiOUz"

Input 2:

A="AbcaZeoB"

  
  
Example Output

Output 1:

"###z###z"

Output 2:

"bc###bc###"

**

```java
**

public class Solution {

   public String solve(String A) {

  

       StringBuilder str = new StringBuilder("");

  

       for(int i=0; i<A.length(); i++) {

  

           if(A.charAt(i)=='a' || A.charAt(i)=='e' || A.charAt(i)=='i' || A.charAt(i)=='o' || A.charAt(i)=='u') {

               str.append('#');

           }

         else if(A.charAt(i)>='a' && A.charAt(i)<='z') {

               str.append(A.charAt(i));

          }       

   }

  

       str.append(str);

  

       return str.toString();

   }

}

  


**
```