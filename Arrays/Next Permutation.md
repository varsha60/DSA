 **Problem Description

Implement the next permutation, which rearranges numbers into the numerically next greater permutation of numbers for a given array A of size N.

If such an arrangement is not possible, it must be rearranged as the lowest possible order, i.e., sorted in ascending order.

NOTE:

- The replacement must be in-place, do not allocate extra memory.
    
- DO NOT USE LIBRARY FUNCTION FOR NEXT PERMUTATION. Use of Library functions will disqualify your submission retroactively and will give you penalty points.
    

  
  
Problem Constraints

1 <= N <= 5 * 105

1 <= A[i] <= 109

  
  
Input Format

The first and the only argument of input has an array of integers, A.

  
  
Output Format

Return an array of integers, representing the next permutation of the given array.

  
  
Example Input

Input 1:

A = [1, 2, 3]

Input 2:

A = [3, 2, 1]

  
  
Example Output

Output 1:

[1, 3, 2]

Output 2:

[1, 2, 3]

  
  
Example Explanation

Explanation 1:

Next permutation of [1, 2, 3] will be [1, 3, 2].

Explanation 2:

No arrangement is possible such that the numbers are arranged into the numerically next greater permutation of numbers.

 So will rearrange it in the lowest possible order.

  

Approach Building : 

  

Brute Force 

1. Generate all possible permutations. 
    
2. Linear Search given input. 
    
3. If the next index is present then return that permutation (i.e next permutation in line for your input) else return sorted input array as answer because higher permutation is not possible. 
    

Time Complexity - N! - which is huge !! 

  

Supposed we have input as, 

1,2 then next possible permutation is 2 1 

1,2,3 then next possible permutation is 1 3 2 

1,3,2 then next possible permutation is 2 1 3

1,2,3,4,5 then next possible permutation is 1,2,3,5,4 - 1,2,4,3,5 - 1,2,4,5,3 - 1,2,5,3,4

  

💡Can you observe some patterns? Think and Pause !

  

Eg: - 7 2 5 3 1 

  

Let’s say we have, 7 5 3 2 1. This is the highest possible permutation. 

  

If we have, 7 2 5 3 1 - now if you see, 5 3 1 is the highest possible permutation of 5 3 1, right? 

So, we can say 5 is the inflation point and 2 is the next possible element that should be swapped with the next greater element to go on to the next higher permutation.  Eg: 1 2 4 5 3 ->>> 1 2 5 3 4 - Our aim is to go to the next possible permutation which will be higher in order. So, here 1 2 4 - next higher is 1 2 5 - Just like Raj → Rak. 

  

7 2 5 3 1 - Inflation point is 5 and 2 should be swapped with the next greater element after 2 which is 3. 

After swapping, 7 3 5 2 1. 

Next higher possible permutation will be 7 3 1 2 5. Here we sorted, 5 2 1 - because next in line is 1 2 5 then next higher and so on. 

  

Time Complexity is O(NLOGN)

Space Complexity is O(1)**

```java
  **int N = A.length-1;

  

   //Look for inflation points - eg: 1 2 4 5 3 - so 5 is the inflation point because 5 3 is the highest possible combination of 5 and 3.

       for(int i=N; i>0; i--) {

           if(A[i]>A[i-1]) {

               inflationPoint = i;

               break;

           }

       }

  

       // System.out.println("Inflation Point is: "+A[inflationPoint]);

  

       if(inflationPoint == 0) {

           //we are already at highest possible nextPermutation

           Arrays.sort(A);

       } else {

           int toSwap = inflationPoint-1;

           int minDifference = A[inflationPoint] - A[toSwap];

           int nextGreaterElementToSwapWith = inflationPoint;

           // System.out.println("Minimum minDifference: "+ minDifference);

           // System.out.println("To Swap before is: "+A[toSwap]);

           for(int i=inflationPoint+1; i<=N; i++) {

  

               if(A[i]-A[toSwap] > 0 && A[i]-A[toSwap]<minDifference) {

                     nextGreaterElementToSwapWith = i;

                   //   System.out.println("Minimum minDifference: "+ minDifference);

                   //   System.out.println("Next element to swap with is: "+A[i]);

               }

  

           }

                   int temp = A[nextGreaterElementToSwapWith];

                   A[nextGreaterElementToSwapWith] = A[toSwap];

                   A[toSwap] = temp;

                   // System.out.println("To Swap after is: "+A[toSwap]);

           }

  

           // System.out.println("Sort from "+A[inflationPoint]+" till "+A[N]);

           // System.out.println("Inflation point index is "+inflationPoint);

  

           Arrays.sort(A,inflationPoint,N+1);

  

           // System.out.println("Inflation element now is "+A[inflationPoint]);

  

        return A;

   }

}**
```