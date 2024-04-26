**

Problem Description

Given the array of strings A, you need to find the longest string S, which is the prefix of ALL the strings in the array.

The longest common prefix for a pair of strings S1 and S2 is the longest string S which is the prefix of both S1 and S2.

Example: the longest common prefix of "abcdefgh" and "abcefgh" is "abc".

  
  
Problem Constraints

0 <= sum of length of all strings <= 1000000

  
  
Input Format

The only argument given is an array of strings A.

  
  
Output Format

Return the longest common prefix of all strings in A.

  
  
Example Input

Input 1:

A = ["abcdefgh", "aefghijk", "abcefgh"]

Input 2:

A = ["abab", "ab", "abcd"];

  
  
Example Output

Output 1:

"a"

Output 2:

"ab"

  
  
Example Explanation

Explanation 1:

Longest common prefix of all the strings is "a".

Explanation 2:

Longest common prefix of all the strings is "ab".

  


**

```java
**

public class Solution {

   public String longestCommonPrefix(ArrayList<String> A) {

  

       StringBuilder longestCommonPrefix = new StringBuilder(A.get(0));

       int N = A.size();

  

       for(int i=1; i<N; i++) {

  

           int s1Iterator = 0;

           int s2Iterator = 0;

  

           String s1 = longestCommonPrefix.toString();

           String s2 = A.get(i);

  

           while(s1Iterator<s1.length() && s2Iterator<s2.length() && Character.compare(s1.charAt(s1Iterator),s2.charAt(s2Iterator))==0) {

               // System.out.println("end: "+ s1Iterator);

               // System.out.println("end: "+ s1.length());

               s1Iterator++;

               s2Iterator++;

           }

  

           // System.out.println("end: "+ s2Iterator);

  

       longestCommonPrefix = new StringBuilder(longestCommonPrefix.substring(0, s1Iterator));

  

       // System.out.println("longestCommonPrefix is :" +longestCommonPrefix);

  

       }

  

       return longestCommonPrefix.toString();

   }

}

  


**
```