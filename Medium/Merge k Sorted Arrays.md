Given k sorted arrays arranged in the form of a matrix of size k * k. The task is to merge them into one sorted array. Return the merged sorted array ( as a pointer to the merged sorted arrays in cpp, as an ArrayList in java, and list in python).


Examples :

Input: k = 3, arr[][] = {{1,2,3},{4,5,6},{7,8,9}}
Output: 1 2 3 4 5 6 7 8 9
Explanation: Above test case has 3 sorted arrays of size 3, 3, 3 arr[][] = [[1, 2, 3],[4, 5, 6],[7, 8, 9]]. The merged list will be [1, 2, 3, 4, 5, 6, 7, 8, 9].

Input: k = 4, arr[][]={{1,2,3,4},{2,2,3,4},{5,5,6,6},{7,8,9,9}}
Output: 1 2 2 2 3 3 4 4 5 5 6 6 7 8 9 9 
Explanation: Above test case has 4 sorted arrays of size 4, 4, 4, 4 arr[][] = [[1, 2, 2, 2], [3, 3, 4, 4], [5, 5, 6, 6], [7, 8, 9, 9 ]]. The merged list will be [1, 2, 2, 2, 3, 3, 4, 4, 5, 5, 6, 6, 7, 8, 9, 9].

Expected Time Complexity: O(k2*Log(k))
Expected Auxiliary Space: O(k2)

Constraints:
1 <= k <= 100

## Code:
``` java

class Solution
{
    //Function to merge k sorted arrays.
    public static ArrayList<Integer> mergeKArrays(int[][] arr,int k) 
    {
        // Write your code here.
        ArrayList<Integer> list=new ArrayList<>();
        int[] indices=new int[k];
        int index=0;
        int totElements=k*k;

        while(index<totElements)
        {

            int smallArrI=-1;
            int smallElement=Integer.MAX_VALUE;
            for(int i=0;i<k;i++)
            {
                if(indices[i]<k)
                {
                  int curMatEle=arr[i][indices[i]];
                  if(curMatEle<smallElement)
                   {
                    smallElement=curMatEle;
                    smallArrI=i;
                   }
                } 
            }
            list.add(smallElement);
            indices[smallArrI]++;
            index++;
        }
        return list;
    }
}

```
