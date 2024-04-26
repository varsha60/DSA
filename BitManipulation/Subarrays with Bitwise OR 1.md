**

Problem Description

Given an array B of length A with elements 1 or 0. Find the number of subarrays such that the bitwise OR of all the elements present in the subarray is 1.

Note : The answer can be large. So, return type must be long.

  
  
Problem Constraints

1 <= A <= 105

  
  
Input Format

The first argument is a single integer A.

The second argument is an integer array B.

  
  
Output Format

Return the number of subarrays with bitwise array 1.

  
  
Example Input

Input 1:

A = 3

B = [1, 0, 1]

Input 2:

A = 2

B = [1, 0]

  

  
  
Example Output

Output 1:

5

  

Output2:

2

  

  
  
Example Explanation

Explanation 1:

The subarrays are :- [1], [0], [1], [1, 0], [0, 1], [1, 0, 1]

Except the subarray [0] all the other subarrays has a Bitwise OR = 1

  

Explanation 2:

The subarrays are :- [1], [0], [1, 0]

Except the subarray [0] all the other subarrays has a Bitwise OR = 1

**

```java
**

public class Solution {

   public long solve(int A, int[] B) {

  

       /*

       We know,

       total number of sub arrays = n*(n+1)/2

       OR is false only when both are false.

       Find out number of subarrays jismein sab false hai 0 hai toh answer 0 ayega.

  

       So, consecutive zeroes ka count nikalo

  

       So, total_number_of_subarrays - total_number_of_subarrays_with_all_zeroes is our answer.  

       */

  

   //Conversion to long is important because A is int - so int * int is int even if you store in long

       long total_number_of_subarrays = (long)A*(long)(A+1)/2;

       long total_number_of_subarrays_with_all_zeroes = 0;

  

       long countOfConsecutiveZeroes = 0;

  

       for(int i=0;i<A;i++) {

           if(B[i]== 0)

           {

               countOfConsecutiveZeroes++;

           }

           if(B[i] == 1) {

               total_number_of_subarrays_with_all_zeroes += countOfConsecutiveZeroes * (countOfConsecutiveZeroes+1)/2;

               countOfConsecutiveZeroes = 0;

           }

  

       }

  

//To handle case 1 1 0 1 0 0 0 -- iss case main yeh loop complete hone par 1 usko mila nhi toh total_number_of_subarrays_with_all_zeroes update hi nhi hoga.

       total_number_of_subarrays_with_all_zeroes += countOfConsecutiveZeroes * (countOfConsecutiveZeroes+1)/2;

  

       return (long)(total_number_of_subarrays - total_number_of_subarrays_with_all_zeroes);

   }

}

  


**
```