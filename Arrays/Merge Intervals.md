**

Problem Description

You have a set of non-overlapping intervals. You are given a new interval [start, end], insert this new interval into the set of intervals (merge if necessary).

You may assume that the intervals were initially sorted according to their start times.

  
  
Problem Constraints

0 <= |intervals| <= 105

  
  
Input Format

First argument is the vector of intervals

second argument is the new interval to be merged

  
  
Output Format

Return the vector of intervals after merging

  
  
Example Input

Input 1:

Given intervals [1, 3], [6, 9] insert and merge [2, 5] .

  

Input 2:

Given intervals [1, 3], [6, 9] insert and merge [2, 6] .

  

  
  
Example Output

Output 1:

[ [1, 5], [6, 9] ]

  

Output 2:

[ [1, 9] ]

  

  
  
Example Explanation

Explanation 1:

(2,5) does not completely merge the given intervals

  

Explanation 2:

(2,6) completely merges the given intervals

**

```java
**

/**

* Definition for an interval.

* public class Interval {

*     int start;

*     int end;

*     Interval() { start = 0; end = 0; }

*     Interval(int s, int e) { start = s; end = e; }

* }

*/

public class Solution {

   public ArrayList<Interval> insert(ArrayList<Interval> intervals, Interval newInterval) {

  

       ArrayList<Interval> ansList = new ArrayList<>();

  

       int newStart = newInterval.start;

       int newEnd = newInterval.end; 

  

       int numberOfIntervals = intervals.size();

  

       for(int i=0; i<numberOfIntervals; i++) {

  

           Interval currentInterval = intervals.get(i);

           int currentStart = currentInterval.start;

           int currentEnd = currentInterval.end;

  

           //For every interval(current interval at hand check if new interval is overlapping or not)

  

           if(newStart > currentEnd) {

               //Assumption new interval is always going to start after current interval

               //First non overlapping condition - current ----- new (eg: 10--20 21--22)

               ansList.add(new Interval(currentStart,currentEnd));

           }

           else if(newEnd < currentStart) {

               //new Interval can end before even current interval starts

               //Second non overlapping condition - new ----- current (eg: 10--24 27--30)

  

               //New is non overlapping with current so insert new

               ansList.add(new Interval(newStart,newEnd));

               //Now Insert - all remaining non overlapping intervals starting from current

               while(i<numberOfIntervals) {

                   Interval remainingNonOverlappingIntervals = intervals.get(i);

                   ansList.add(remainingNonOverlappingIntervals);

                   i++;

               }

  

               return ansList;

           }

           else {

               //overlapping - so merge

               newStart = Math.min(newStart,currentStart);

               newEnd = Math.max(newEnd,currentEnd);

           }

  

       }

  

       //Case when every thing gets merged at the end so insert newly merged interval

       ansList.add(new Interval(newStart,newEnd));

  

       return ansList;

   }

}

  


**
```