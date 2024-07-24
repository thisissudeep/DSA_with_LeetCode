### Nearest Meeting Cell
### Problem Description :
You are given a maze with N cells. Each cell may have multiple entry points but not more than one
exit (i.e. entry/exit points are unidirectional doors like valves). The cells are named with an integer
from 0 to N-1.
You have to find :
Nearest meeting cell : Given any two cells - C1, C2, find the closest cell Cm that can be reached
from both C1 and C2.
### INPUT FORMAT :
1. The first line contains the number of cells N.
2. The second line has a list of N values of the edge[ ] array, where edge[i] conatins the cell
number that can be reached from cell 'i' in one step. edge[i] is -1 if the ith doesn't have an
exit.
3. Third line for each testcase contains two cell numbers whose nearest meeting cell needs to
be found. (return -1 if there is no meeting cell from two given cells)
### OUTPUT FORMAT :
Output a single line that denotes the nearest meeting cell (NMC).
### Sample Input :
23

4 4 1 4 13 8 8 8 0 8 14 9 15 11 -1 10 15 22 22 22 22 22 21

9 2
### Sample Output :
4
### Code :
``` java
public int nearestMeetingCell(int c1,int c2,int[] Edge)  //or Shortest Meeting Point
    {
        int[] c1Nodes=new int[Edge.length];
        int[] c2Nodes=new int[Edge.length];

        nearestMeetingCell(c1, Edge,c1Nodes,0);
        nearestMeetingCell(c2, Edge,c2Nodes,0);

        int minSteps=Integer.MAX_VALUE;
        int minNode=-1;  //if no meeting points are present
        for(int i=0;i<Edge.length;i++)
        {
            if(c1Nodes[i]>0 && c2Nodes[i]>0) 
            {
                int totSteps=c1Nodes[i]+c2Nodes[i];
                if(totSteps<minSteps)
                {
                minSteps=totSteps;
                minNode=i;
                }
            }
        }   
        return minNode;
    }
    private void nearestMeetingCell(int vertix,int[] Edge,int[] path,int steps)
    {
        if(vertix==-1 || path[vertix]>0) return;
        path[vertix]=steps;
        nearestMeetingCell(Edge[vertix],Edge,path,steps+1);
    }

```
