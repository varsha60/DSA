**

Problem Description

You are given a string A of size N.

Return the string A after reversing the string word by word.

NOTE:

- A sequence of non-space characters constitutes a word.
    
- Your reversed string should not contain leading or trailing spaces, even if it is present in the input string.
    
- If there are multiple spaces between words, reduce them to a single space in the reversed string.
    

  
  
Problem Constraints

1 <= N <= 3 * 105

  
  
Input Format

The only argument given is string A.

  
  
Output Format

Return the string A after reversing the string word by word.

  
  
Example Input

Input 1:

A = "the sky is blue"

  

Input 2:

A = "this is ib"

  

  
  
Example Output

Output 1:

"blue is sky the"

  

Output 2:

"ib is this"    

  

  
  
Example Explanation

Explanation 1:

We reverse the string word by word so the string becomes "blue is sky the".

  

Explanation 2:

We reverse the string word by word so the string becomes "ib is this".

  
**

```java
**

public class Solution {

  

   public String reverse (String A) {

  

       char [] charArray = A.toCharArray();

      int N = charArray.length;

      char temp = 'a';

      int i=0;

      int j=N-1;

  

  

      while(i<j) {

  

          temp = charArray[i];

          charArray[i] = charArray[j];

          charArray[j] = temp;

  

          i++;

          j--;

  

      }

  

      return String.copyValueOf(charArray);

   }

  

   public String solve(String A) {

  

       int N = A.length();

       String ans = "";

  

       for(int i=N-1; i>=0;i--) {

  

           if(A.charAt(i) != ' ') {

  

               String currentWord = "";

               while(i>=0 && A.charAt(i) != ' ') {

                   currentWord = currentWord + A.charAt(i);

                   i--;

               }

  

               if(!ans.isEmpty()) {

                   ans = ans + ' ';

               }

  

               ans = ans + reverse(currentWord);

           }

       }

  

       return ans;

   }

}

  


**
```