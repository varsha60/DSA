**

Given an integer array A containing N distinct integers, you have to find all the leaders in array A. An element is a leader if it is strictly greater than all the elements to its right side.

  

NOTE: The rightmost element is always a leader.

  
  
Problem Constraints

1 <= N <= 105

1 <= A[i] <= 108

  
  
Input Format

There is a single input argument which a integer array A

  
  
Output Format

Return an integer array denoting all the leader elements of the array.

  
  
Example Input

Input 1:

A = [16, 17, 4, 3, 5, 2]

Input 2:

A = [5, 4]

  
  
Example Output

Output 1:

[17, 2, 5]

Output 2:

[5, 4]

  
  
Example Explanation

Explanation 1:

Element 17 is strictly greater than all the elements on the right side to it.

Element 2 is strictly greater than all the elements on the right side to it.

Element 5 is strictly greater than all the elements on the right side to it.

So we will return these three elements i.e [17, 2, 5], we can also return [2, 5, 17] or [5, 2, 17] or any other ordering.

Explanation 2:

Element 5 is strictly greater than all the elements on the right side to it.

Element 4 is strictly greater than all the elements on the right side to it.

So we will return these two elements i.e [5, 4], we can also any other ordering.

**

```java
**

public class Solution {

   public int[] solve(int[] A) {

       /* Brute Force - O(n2)

       ith element ke liye check kro jth element (i+1 to N-1)

       jaise hi koi element bada mil gaya ith element se vaise hi break kr lo

       loop and check for another ith element.

  

       Optimized approach - O(N)

       Carry Forward the leader element or maximum element from rhs.

       */

  

       int N = A.length;

       List<Integer> ansList = new ArrayList<>();

       ansList.add(A[N-1]);

       int max = A[N-1];

  

       for(int i=N-2; i > -1; i--)

       {

        if(A[i]>max)

               {

                   ansList.add(A[i]);

                   max = A[i];

               }

       }

       return ansList.toArray();

  

  

   }

}

**
```