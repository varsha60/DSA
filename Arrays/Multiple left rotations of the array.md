
Problem Description

Given an array of integers A and multiple values in B, which represents the number of times array A needs to be left rotated.

Find the rotated array for each value and return the result in the from of a matrix where ith row represents the rotated array for the ith value in B.

  
  
Problem Constraints

1 <= length of both arrays <= 2000 -10^9 <= A[i] <= 10^9 0 <= B[i] <= 2000

  
  
Input Format

The first argument given is the integer array A.

The second argument given is the integer array B.

  
  
Output Format

Return the resultant matrix.

  
  
Example Input

Input 1:

  

    A = [1, 2, 3, 4, 5]

    B = [2, 3]

  

  
Input 2:

    A = [5, 17, 100, 11]

    B = [1]

  

  
  
Example Output

Output 1:

  

    [ [3, 4, 5, 1, 2]

     [4, 5, 1, 2, 3] ]

  

  

  

Output 2:

  

  

    [ [17, 100, 11, 5] ]

  

  

  

  
  
Example Explanation

for input 1 -> B[0] = 2 which requires 2 times left rotations

1: [2, 3, 4, 5, 1]

2: [3, 4, 5, 1, 2]

B[1] = 3 which requires 3 times left rotation

1: [2, 3, 4, 5, 1]

2: [3, 4, 5, 1, 2]

2: [4, 5, 1, 2, 4]

**

```java
**

public class Solution {

   public ArrayList<ArrayList<Integer>> solve(ArrayList<Integer> A, ArrayList<Integer> B) {

  

       int n = A.size();

       int m = B.size();

       ArrayList<ArrayList<Integer>> result = new ArrayList<ArrayList<Integer>>();

  

       for(int i=0; i<m; i++) {

           int k = B.get(i); //number of rotations for ith B.

           k = k%n;

           ArrayList<Integer> temp = new ArrayList<Integer>(A);

           //System.out.println("Effective number of rotations are: "+k);

           temp = reverse(temp,0,n-1);

           temp = reverse(temp,n-k,n-1);

           temp = reverse(temp,0,n-k-1);

           //System.out.println("Array becomes :");

           // for(int x: temp) {

           //     System.out.print(x);

           // }

           //System.out.println();

           result.add(temp);

        }

  

       return result;

   }

  

   private ArrayList<Integer> reverse(ArrayList<Integer> A, int start, int end) {

  

           while(start<end) {

  

           int temp = A.get(start);

           A.set(start,A.get(end));

           A.set(end,temp);

           start++;

           end--;

  

       }

  

   return A;

   }

}

**
```