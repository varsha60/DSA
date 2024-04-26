**
Given an array of integers A, find and return the product array of the same size where the ith element of the product array will be equal to the product of all the elements divided by the ith element of the array.

Note: It is always possible to form the product array with integer (32 bit) values. Solve it without using the division operator.

  
Input Format

The only argument given is the integer array A.

  

Output Format

Return the product array.

  

Constraints

2 <= length of the array <= 1000

1 <= A[i] <= 10

  

For Example

Input 1:

    A = [1, 2, 3, 4, 5]

Output 1:

    [120, 60, 40, 30, 24]

  

Input 2:

    A = [5, 1, 10, 1]

Output 2:

    [10, 50, 5, 50]

**

```java
**

public class Solution {

   public int[] solve(int[] A) {

  

  

//Note - we need to do without division operators. isiliye solution below is not acceptable.

       // int product = 1;

       // int N = A.length;

       // int [] ans = new int[N];

  

       // for (int i=0;i<N;i++)

       // {

       //     product = product * A[i];

       // }

  

       // for(int i=0; i<N; i++)

       // {

       //     ans[i] = product/A[i];

       // }

  

       // return ans;

  

       // Prefix and Suffix Approach

       // Apne ko basically saare elements ka product chahiye except that element

       // toh kisi tarah se right side of ith element ka product nikale

       // and left side of ith element ka product nikale toh bas left product * right product will be our ans.

  

  

       int N = A.length;

       int [] ans = new int[N];

       int [] prefix_product = new int[N];

       int [] suffix_product = new int[N];

  

       //prefix_product

       prefix_product[0] = 1;

  

       for(int i=1; i<N; i++) {

           prefix_product[i] = prefix_product[i-1] * A[i-1];

       }

  

  

       //suffix_product

       suffix_product[N-1] = 1;

       for(int j=N-2; j>-1;j--)

       {

           suffix_product[j] = suffix_product[j+1] * A[j+1];

       }

  

  

       for(int k=0; k<N; k++){

  

           ans[k] = prefix_product[k] * suffix_product[k];

  

       }   

  

  

       return ans;

}

}

**
```