
**

Problem Description

You are given a character string A having length N, consisting of only lowercase and uppercase latin letters.

You have to toggle case of each character of string A. For e.g 'A' is changed to 'a', 'e' is changed to 'E', etc.

  
  
Problem Constraints

1 <= N <= 105

A[i] ∈ ['a'-'z', 'A'-'Z']

  
  
Input Format

First and only argument is a character string A.

  
  
Output Format

Return a character string.

  
  
Example Input

Input 1:

A = "Hello"

Input 2:

A = "tHiSiSaStRiNg"

  
  
Example Output

Output 1:

hELLO

Output 2:

ThIsIsAsTrInG

  
  
Example Explanation

Explanation 1:

'H' changes to 'h'

 'e' changes to 'E'

 'l' changes to 'L'

 'l' changes to 'L'

 'o' changes to 'O'

Explanation 2:

"tHiSiSaStRiNg" changes to "ThIsIsAsTrInG".

**

```java
**

public class Solution {

  

   public String solve(String A) {

  

       char [] charArray = A.toCharArray();

  

       int N = charArray.length;

  

       for(int i=0; i<N;i++) {

  

           //Check if lower or upper

           if(charArray[i]>='A'&& charArray[i]<='Z')

           {

               //toggle to lower case

               charArray[i] = (char)(charArray[i]+32);

           }

           else

               //toggle to upper case

           charArray[i] = (char)(charArray[i]-32);

       }

  

       return String.copyValueOf(charArray);

   }

}

  


**
```