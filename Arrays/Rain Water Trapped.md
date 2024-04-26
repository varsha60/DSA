**

Problem Description

Given a vector A of non-negative integers representing an elevation map where the width of each bar is 1, compute how much water it is able to trap after raining.

  
  
Problem Constraints

1 <= |A| <= 100000

  
  
Input Format

First and only argument is the vector A

  
  
Output Format

Return one integer, the answer to the question

  
  
Example Input

Input 1:

A = [0, 1, 0, 2]

  

Input 2:

A = [1, 2]

  

  
  
Example Output

Output 1:

1

  

Output 2:

0

  

  
  
Example Explanation

Explanation 1:

1 unit is trapped on top of the 3rd element.

  

Explanation 2:

No water is trapped.

  

#### Approach Building

1. Can water be stored on start and end buildings? And why?
    
2. To find total water trapped - Can we figure out water trapped on one building and then just add to get total? 
    
3. Now think - what is it dependent on? Is it dependent on immediate left-right buildings? 
    
4. Once you figure out what it is dependent on left and right? Can you think what is the common boundary that it can have to store the water on a building ? 
    

  

Solution 

- Water can be stored only when we have 2 boundaries - one on left and one on right. 
    
- Now, whatever is minimum out of it (let’s say we have 6 on left and 5 on right) so water stored will be till 5. Right? 
    
- So, we need to find maximum on left and maximum on right - then whatever is minimum will be our common boundary that will support our water storage on that building. 
    

  

Complexities

- Time O(n2) and space O(n). 
    
- Can we do it better than n2? Instead of calculating maxLeft and maxRight for every i again and again. Can we pre compute it ? 
    
- TC - O(n) and space O(n). 
    

  
  

Can we optimize space as well ? 

- Think if we have precomputed maxRight… Can we calculate maxLeft on the go ? But that still is O(n) space, isn’t it? 
    
- What if we calculate both on the go ? 
    
- But wait, how ? 
    
- Refer Class notes for detailed understanding.
    

**

```java
**

public class Solution {

   // DO NOT MODIFY THE ARGUMENTS WITH "final" PREFIX. IT IS READ ONLY

   public int trap(final int[] A) {

  

       //Optimized approach - with space constant and time N

  

       int N = A.length;

  

       int i =0;

       int j = N-1;

  

        int lmax = A[i];

        int rmax = A[j];

  

        int water_trapped = 0;

        int total_water_trapped = 0;

  

        //idea here is to move away from smaller values of lmax or rmax - because we are 100% sure that rmax is correct and lmax is not reliable if lmax is taller. And even if lmax is more than the current value it will not affect our answer. 

       while(i<j) {

           if(lmax<=rmax) {

               i++;

               water_trapped = lmax - A[i];

               //update lmax if we get maximum ith bar

               lmax = Math.max(lmax,A[i]);

  

           }

           else {

               j--;

               water_trapped = rmax - A[j];

               rmax = Math.max(rmax, A[j]);

           }

  

           if(water_trapped>0)

               total_water_trapped = total_water_trapped + water_trapped;

       }

  

       return total_water_trapped;

  

       // /*

       //     Water trapped on each unit is nothing but

       //     Min(max_bar_on_left,max_bar_on_right) - ith bar's height

       // */

  

       // int number_of_bars = A.length;

  

  

       // //maximum_bar_left array will maintain all maximum bar's on left side of ith element

       // int [] maximum_bar_left = new int[number_of_bars];

  

       // //maximum_bar_right array will maintain all maximum bar's on right side of the ith element

       // int [] maximum_bar_right = new int[number_of_bars];

  

       // Arrays.fill(maximum_bar_left, 0);

       // Arrays.fill(maximum_bar_right, 0);

  

       // //water trapped for individual bar

       // int water_trapped = 0;

  

       // //total water trapped

       // int total_water_trapped = 0;

  

       // //iterate from left to right to find maximum_bar_left

       // for(int i=1; i<number_of_bars; i++) {

  

       //     maximum_bar_left[i] = Math.max(A[i-1],maximum_bar_left[i-1]);

  

       // }

  

  

       // //iterate from right to left to find maximum_bar_right

  

       //  for(int j=number_of_bars-2; j>=0; j--) {

  

       //       maximum_bar_right[j] = Math.max(A[j+1],maximum_bar_right[j+1]);

       // }

  

  

       // //iterate on all the bars and add to the total water trapped.

  

       // int k = 1;

  

       // //edge case where the first bar is 0 height. ignore the second bar at index 1 because no water will get trapped.

       // if(A[0] == 0) {

       //     k = 2;

       // }

  

       // for(k=k; k<number_of_bars-1;k++) {

       //     //minimum of both sides will give maximum height till which water can get trapped.

       //     int min = Math.min(maximum_bar_left[k],maximum_bar_right[k]);

  

       //     //to get effective trapped water

       //     water_trapped = min - A[k];

  

       //     //we can only trap water if min is greater than current bar height

       //     if(water_trapped > 0)

       //     {

       //         total_water_trapped = total_water_trapped + water_trapped;

       //     }

       // }

  

       // return total_water_trapped;

   }

}

  


**
```