
**

Problem Description

Given a string A of size N, find and return the longest palindromic substring in A.

Substring of string A is A[i...j] where 0 <= i <= j < len(A)

Palindrome string:  
A string which reads the same backwards. More formally, A is palindrome if reverse(A) = A.

Incase of conflict, return the substring which occurs first ( with the least starting index).

  
  
Problem Constraints

1 <= N <= 6000

  
  
Input Format

First and only argument is a string A.

  
  
Output Format

Return a string denoting the longest palindromic substring of string A.

  
  
Example Input

Input 1:

A = "aaaabaaa"

Input 2:

A = "abba

  
  
Example Output

Output 1:

"aaabaaa"

Output 2:

"abba"

  
  
Example Explanation

Explanation 1:

We can see that longest palindromic substring is of length 7 and the string is "aaabaaa".

Explanation 2:

We can see that longest palindromic substring is of length 4 and the string is "abba".

  
**

```java
**

public class Solution {

  

   // public boolean checkPalindrome(int s, int e, String S) {

   //     while(s<=e) {

   //         if(S.charAt(s) != S.charAt(e)) {

   //             return false;

   //         }

  

   //         s++;

   //         e--;

   //     }

  

   //     return true;

   // }

  

   // int N = A.length();

       // int max_length_of_palindrome = 1;

       // int end_index_of_longest_palindrome = 0;

       // int start_index_of_longest_palindrome = 0;

  

       // //Iterate over all substring starting from index i and check if palindrome of not.

  

       // for(int i=0; i<N; i++) {

       //     //For each sub string starting from index i - 00 01 02

       //     for(int j=i; j<N; j++) {

       //         int length_of_palindrome = 0;

  

       //         // System.out.println(i);

       //         // System.out.println(j);

       //         if(checkPalindrome(i,j,A)) {

       //             length_of_palindrome = j - i + 1;

       //             if(length_of_palindrome > max_length_of_palindrome) {

       //                 max_length_of_palindrome = length_of_palindrome;

       //                 start_index_of_longest_palindrome = i;

       //                 end_index_of_longest_palindrome = j;

       //             }

  

       //         }

  

  

       //     }

       // }

  

       // return A.substring(start_index_of_longest_palindrome, end_index_of_longest_palindrome+1);

  

  

       int max_length = 1;

       int start_index_of_longest_palindrome = 0;

       int end_index_of_longest_palindrome = 0;

       int length = 0;

   public String longestPalindrome(String A) {

  

  

       int N = A.length();

       for(int i=0;i<N;i++) {

  

           //Odd length palindrome case - take one char as centre and expand across

         expand(A,i,i);

  

       //Even length palindrome case - take two consecute char as centres and expand across.

         expand(A,i,i+1);

       }

  

       return A.substring(start_index_of_longest_palindrome, end_index_of_longest_palindrome+1);

  

   }

  

    public void expand(String S, int ci, int cj) {

  

       int i = ci;

       int j = cj;

  

       while(i>=0 && j<S.length() && S.charAt(i) == S.charAt(j)) {

           i--;

           j++;

       }

  

       length = j-i+1;

  

       if( length > max_length) {

               max_length = length;

               start_index_of_longest_palindrome = i+1;

               end_index_of_longest_palindrome = j-1;

           }     

  

   }

  

}

  


**
```