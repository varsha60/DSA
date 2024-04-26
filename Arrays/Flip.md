**

Problem Description

You are given a binary string A(i.e., with characters 0 and 1) consisting of characters A1, A2, ..., AN. In a single operation, you can choose two indices, L and R, such that 1 ≤ L ≤ R ≤ N and flip the characters AL, AL+1, ..., AR. By flipping, we mean changing character 0 to 1 and vice-versa.

Your aim is to perform ATMOST one operation such that in the final string number of 1s is maximized.

If you don't want to perform the operation, return an empty array. Else, return an array consisting of two elements denoting L and R. If there are multiple solutions, return the lexicographically smallest pair of L and R.

NOTE: Pair (a, b) is lexicographically smaller than pair (c, d) if a < c or, if a == c and b < d.

  
  
Problem Constraints

1 <= size of string <= 100000

  
  
Input Format

First and only argument is a string A.

  
  
Output Format

Return an array of integers denoting the answer.

  
  
Example Input

Input 1:

A = "010"

Input 2:

A = "111"

  
  
Example Output

Output 1:

[1, 1]

Output 2:

[]

  
  
Example Explanation

Explanation 1:

A = "010"

  

Pair of [L, R] | Final string

_______________|_____________

[1 1]          | "110"

[1 2]          | "100"

[1 3]          | "101"

[2 2]          | "000"

[2 3]          | "001"

  

We see that two pairs [1, 1] and [1, 3] give same number of 1s in final string. So, we return [1, 1].

  

Explanation 2:

No operation can give us more than three 1s in final string. So, we return empty array [].

  

  
  
**

```java
**

public class Solution {

   public int[] flip(String A) {

       /*

       Approaches - O(N3) - Generate all substrings and check if the frequency of 1 os maximum.

       - If you are thinking of choosing substring with maximum 0s then in that case beware of 1s in that substring.

       eg:- 1 1 0 0 0 0 1 1 1 0 0 1

       If you choose

           0 0 0 0 1 1 1 0 0 - you will get 6 wins but 3 loss - so total you will get 9 1s.

       Ideally, you should choose

           0 0 0 0 - you will get 4 wins and no loss - so total you will get 10 1s.

  

       So, you should look for maximum net profit or net 1s you can get.

  

       You can consider - 0 - +1 and 1 as -1. which indicates profit and loss of 1s.

  

       if you pre compute the sum - using prefix sum - then complexity will be O(N2) and space will be O(N).

  

       Let's optimize space as well, calculate sum on fly using carry forward technique.

       Space will be O(1) and TC will be O(N2).

  

       Most optimal way with TC - O(N) and space O(1). using Kaden's algorithm.

       */

  

       // return carryForwardFlip(A); - Gives TLE

       return kadensFlip(A);

  

   }

  

   public int[] kadensFlip(String A) {

  

       int N = A.length();

       int maxNet1s = Integer.MIN_VALUE;

       int [] ans = new int [2];

       int currentNet1s = 0;

       int l=0;

       int r=0;

  

       for(int i=0; i<N; i++) {

  

           int c = Character.getNumericValue(A.charAt(i));

           if(c==1) {

               c = -1;

           } else {

               c = 1;

           }

  

           currentNet1s = currentNet1s + c;

  

           if(currentNet1s > maxNet1s) {

               maxNet1s = currentNet1s;

               ans[0] = l+1;

               ans[1] = r+1;

           }

  

           if(currentNet1s < 0) {

               currentNet1s = 0;

               l = i + 1;

               r = i + 1;

           } else {

               r++;

           }

  

       }

  

       if(maxNet1s<=0) {

           int emptyArray [] = {};

           return emptyArray;

       } else {

           return ans;

       }

  

  

   }

  

   public int[] carryForwardFlip(String A) {

  

       int N = A.length();

       int maxNet1s = Integer.MIN_VALUE;

       int [] ans = new int [2];

  

       for(int i=0; i<N; i++) {

  

           int net1s = 0;

  

           for(int j=i; j<N; j++) {

               int c = Character.getNumericValue(A.charAt(j));

                   if(c==1) {

                       c = -1;

                    } else {

                        c = 1;

                   }

               net1s = net1s + c;

               if(net1s > maxNet1s) {

                   maxNet1s = Math.max(net1s,maxNet1s);

                   ans[0] = i+1;

                   ans[1] = j+1;

               }

           }

       }

  

       if(maxNet1s<=0) {

           int emptyArray [] = {};

           return emptyArray;

       }

  

       return ans;

   }

}

**
```