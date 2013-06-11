Parition Problem, and other stuff in June
#########################################
:date: 2013-6-9 12:34
:category: Programing
:tags: Java, Dynamic Programming
:author: Jeffrey Skonhovd

I decided to break up my large post into two smaller posts. I am currently reading the first edition of The Algorithm Design Manual. I am currently on Chapter 3, which covers Dynamic Programming. The problem I just finshed is the Parition Problem. I solved this problem a while ago on TopCoder, its called FairWorkload on TopCoder, using Binary Search. You can read the problem statement on `Topcoder`_. This is an interesting problem with alot of different approachs to a solution.

.. _`Topcoder`: http://community.topcoder.com/stat?c=problem_statement&pm=1901&rd=4650



.. code-block:: java

    public class Partition {
    
      public int partitionProblem(int[] S, int k)
      {
    		int n = S.length;
    		int[] p = new int[n+1];
    		int[][] M = new int[n][k];
    		TestFramework test = new TestFramework();
    		for(int i = 1; i < n+1; i++)
    		{
    			if(i > 0)
    			{
    				p[i] = p[i-1] + S[i-1];
    			}
    			else
    			{
    				p[0] = 0;
    			}
    		}
    
    		
    		//init boundary conditions
    		
    		for(int i = 0; i < n; i++)
    		{
    			M[i][0] = p[i+1];		
    		}
    		
    		for(int j = 1; j < k; j++)
    		{
    			M[0][j] = S[0];
    		}
    		
    		for(int i = 1; i < n; i++)
    			for(int j = 1; j <k; j++)
    			{
    				M[i][j] = Integer.MAX_VALUE;
    				for(int x = 0; x < i; x++)
    				{
    					int s = Math.max(M[x][j-1],p[i+1] - p[x+1]);
    					M[i][j] = Math.min(s, M[i][j]);
    					
    				}
    			}
    		test.print(M);
    		return M[n-1][k-1];
    	}
    	public static void main(String[] args) {
    		// TODO Auto-generated method stub
    		TestFramework test = new TestFramework();
    		Partition part = new Partition();
    		int[] s = new int[] {1,2,3,4,5,6,7,8,9};
    		
    		int M = part.partitionProblem(s,3);
    		System.out.println("Done");
    		test.print(M);
    	}
    
    }

Now, The explaination of this problem is a little difficult. Remember, The goal is Partition S into K or fewer ranges, so as to minimize the maximum sum over all the ranges. This means that we want to return the largest sum of a range from the optimal solution. The optimal soultion is the one with the smallest maximum sum.  
To solve this problem, We want to consider a recursive exhaustive search approach. Notice that the kth partition starts right after we place the (k-1)st divider. Lets think about where we can place this last divider. Well, Obivously we can place it between some ith and (i+1)st element for some i, where 1<=i<=n. What would be the cost of placing this divider? The cost will be the larger of two quantities. The cost of the last partition, which is the sum of the range between i+1 and n and the cost of the largest partition form to the left of i. What is the size of this left parition?  To minimize our total, we would want to use the k-2 remaining dividers to partition the remainding elements as equally as possible. Therefore, We can define a function to find the minimum possible cost over all partitions of {s1, ... , sn} into k ranges, where the cost of a partition is the largest sum of elements in one of its parts.

M[n,k] = minimum of {1, ... ,n} of max(M[i,k-1], sum j = i+1 to n Sj).

We can then use this formula to built a table for the dynamic programing solution of this problem. Anyway, A better explantion is in the Algorthm Design Manual, and I urge you to look at it if you are interested.
