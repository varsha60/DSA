**

Problem Description

There are beggars sitting in a row outside a temple. Each beggar initially has an empty pot. When the devotees come to the temple, they donate some amount of coins to these beggars. Each devotee gives a fixed amount of coin(according to their faith and ability) to some K beggars sitting next to each other.

  

Given the amount P donated by each devotee to the beggars ranging from L to R index, where 1 <= L <= R <= A, find out the final amount of money in each beggar's pot at the end of the day, provided they don't fill their pots by any other means.

For ith devotee B[i][0] = L, B[i][1] = R, B[i][2] = P, given by the 2D array B

  
  
Problem Constraints

1 <= A <= 2 * 105

1 <= L <= R <= A

1 <= P <= 103

0 <= len(B) <= 105

  
  
Input Format

The first argument is a single integer A.

The second argument is a 2D integer array B.

  
  
Output Format

Return an array(0 based indexing) that stores the total number of coins in each beggars pot.

  
  
Example Input

Input 1:-

A = 5

B = [[1, 2, 10], [2, 3, 20], [2, 5, 25]]

  

  
  
Example Output

Output 1:-

10 55 45 25 25

  

  
  
Example Explanation

Explanation 1:-

First devotee donated 10 coins to beggars ranging from 1 to 2. Final amount in each beggars pot after first devotee: [10, 10, 0, 0, 0]

Second devotee donated 20 coins to beggars ranging from 2 to 3. Final amount in each beggars pot after second devotee: [10, 30, 20, 0, 0]

Third devotees donated 25 coins to beggars ranging from 2 to 5. Final amount in each beggars pot after third devotee: [10, 55, 45, 25, 25]

  

  

  

Hint - Think of the solution when only L is given and R is not given. You need to add from L to the N-1th index. Can you think of something which helps you to take the value ahead in range? 

Now for the original question - think of how you can modify this solution to complement addition?

**

```java
**

TC - O(N+Q) - SC - O(1)

public class Solution {

   public int[] solve(int A, int[][] B) {

  

  

       //Beggars Array

       int [] beggars_array = new int[A];

  

       //Initially all beggars have 0 coins

       Arrays.fill(beggars_array,0);

  

       //Final count

       // int [] ans = new int [A];

  

       //We will mark L with value and R+1 with -value;

       for(int i=0; i<B.length; i++) {

  

           //start of range

           int L = B[i][0];

  

           //end of range

           int R = B[i][1];

  

           //coins donated

           int coins = B[i][2];

  

  

           //start index +coins

           beggars_array[L-1] = beggars_array[L-1] + coins;

  

          //end+1 index -coins because we only want to distribute till R

          if(R<A)

               beggars_array[R] = beggars_array[R] - coins;

  

       }

  

       //constricting prefix array.

       for(int i=1;i<A;i++) {

           beggars_array[i] = beggars_array[i-1] + beggars_array[i];

       }

  

       return beggars_array;

   }

}

  

  
**
```