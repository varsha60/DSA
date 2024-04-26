**

Problem Description

Given a collection of intervals, merge all overlapping intervals.

  
  
Problem Constraints

1 <= Total number of intervals <= 100000.

  
  
Input Format

First argument is a list of intervals.

  
  
Output Format

Return the sorted list of intervals after merging all the overlapping intervals.

  
  
Example Input

Input 1:

[1,3],[2,6],[8,10],[15,18]

  
  
Example Output

Output 1:

[1,6],[8,10],[15,18]

  
  
Example Explanation

Explanation 1:

Merge intervals [1,3] and [2,6] -> [1,6].

so, the required answer after merging is [1,6],[8,10],[15,18].

No more overlapping intervals present.

  
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

import java.util.*;

public class Solution {

   public ArrayList<Interval> merge(ArrayList<Interval> intervals) {

  

  

//Given list is not sorted as per start points. sort first to get TC - O(NLOGN)

//Else another approach takes N^N complexity.

//We need to take each interval and check against all intervals for overlapping condition.

     Collections.sort(intervals, new Comparator<Interval>() {

           public int compare(Interval a, Interval b) {

              return a.start - b.start;

           }

       });

  

       ArrayList<Interval> mergedOverlappedIntervals = new ArrayList<>();

  

       int numberOfIntervals = intervals.size();

  

  

       //first interval

       Interval newInterval = intervals.get(0);

  

  

       //Iterate over all intervals starting from index 1 and merge if overlaps

       for(int i=1; i<numberOfIntervals; i++) {

  

           //current interval

           Interval currentInterval = intervals.get(i);

  

           //Check if overlaps firstInterval ---- currentInterval

  

           if(newInterval.end >= currentInterval.start) {

  

               //Keep merging overlapped intervals

               newInterval.end = Math.max(newInterval.end, currentInterval.end);

  

           } else {

  

               //Encountered non overlapped interval

  

               //Insert overlapped intervals uptill now

               mergedOverlappedIntervals.add(newInterval);

  

               //Update to keep on checking for another overlapped interval

               newInterval = currentInterval;

           }   

  

       }

  

       //You kept on merging - insert full one big overlapped interval

       //OR insert last interval if it is non overlapped one because we inserted overlapped interval in else

       //we need to insert non overlapped if it is at the end.

       mergedOverlappedIntervals.add(newInterval);

  

       return mergedOverlappedIntervals;

  

   }

}

**
```