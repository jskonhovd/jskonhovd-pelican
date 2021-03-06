CLRS - Dynamic Programming - Java
#################################
:date: 2013-04-17 22:43
:category: Programming
:tags: Java, CLRS, Dynamic Programming
:author: Jeffrey Skonhovd
:excerpt: Dynamic Programming


Hey again, This blog post with cover the topic of dynamic programming. According to Wikipedia,
Dynamic Programming is a method for solving complex problems by breaking them down into simpler sub-problems.
That doesn't help to much. So lets start a simple example with a program that doesn't use Dynamic Programming,
and the performance issues associated with it.

This problem is a classic. We want to write a function that calculates the value of the nth member of the Fibonacci.

.. code-block:: java

      public class DynamicPrograming {
     
          public Integer fib(int n)
          {
              if(n == 0)
              {
              return 0;
              }
              if(n == 1)
              {
              return 1;
              }
              return fib(n-1) + fib(n-2);
          }
        public static void main(String[] args) {
        // TODO Auto-generated method stub
        DynamicPrograming foo = new DynamicPrograming();
        System.out.println(foo.fib(0));
        System.out.println(foo.fib(15));
        }
    }

Now the issue with this program is pretty obvious right? We are recalculating fib multiple times while we go down the call
stack. This becomes an issue when N becomes larger. This solution is an exponential time algorithm.

Now using dynamic programming, We can come up with a much better solution. The idea of Dynamic Programming is to break down your
program into smaller sub-problems. This way you can reuse the information from each sub-problem to build your answer. The following
is my solution to the creating a function that calculates the value of the nth member of the Fibonacci, using Dynamic Programming.

.. code-block:: java
     
      public class DynamicPrograming {
     
            public Integer fib2(int n)
            {
                  int[] arr = new int[n+1];   
                  int foo = 0;
                  if(n <= 0)
                  {
                        return foo;
                  }
                  arr[0] = 0;
                  arr[1] = 1;
                  for(int i = 1; i<=(n-1); i++)
                  {
                 
                        foo = arr[i-1] + arr[i];
                        arr[i+1] = foo;
                  }
                 
                  return foo;
            }

            public static void main(String[] args) {
            // TODO Auto-generated method stub
            DynamicPrograming foo = new DynamicPrograming();
            System.out.println(foo.fib2(0));
            System.out.println(foo.fib2(0));
            }
      }

Now I am sure you are asking. Jeff, This seems simple enough. But can you use this technique to solve
more nontrivial problems? Well, Yes we can. There are a large number of good problems you can solve with Dynamic Programming.
The difficulty I have is understanding when you can use Dynamic Programming, or understanding when to use it.

This next problem is another classic problem you can solve using Dynamic Programming. The longest common sub-string problem is
a classic in Computer Science. the longest common sub-string problem is to find the longest string that is a sub-string
of two or more strings.

.. code-block:: java
     
      public class LongestCommonSubString {

            public String getLongestCommonSubString(String a, String b)
            {
            int z = 0;
            int[][] l = new int[a.length()][b.length()];
            String ret = "";
            int index = 0;
           
            for(int i =0; i< a.length(); i++)
            {
                  for(int j = 0; j < b.length(); j++)
                  {
                 
                        if(a.charAt(i) == b.charAt(j))
                        {
                              if( i == 0 || j == 0)
                              {
                                    l[i][j] = 1;
                              }
                              else
                              {
                                    l[i][j] = l[i-1][j-1] + 1;
                              }
                              if(l[i][j] > z)
                              {
                                    z = l[i][j];
                                    index = i;
                              }
                        }
                        else
                        {
                              l[i][j] = 0;
                        }
            }
           
            }
            ret = a.substring(index - z + 1, index+1);
            return ret;
           
           
            }
           
            public static void main(String[] args) {
            // TODO Auto-generated method stub
            LongestCommonSubString LCSS = new LongestCommonSubString();
            System.out.println(LCSS.getLongestCommonSubString("abcd2323", "131313abcc"));
            System.out.println(LCSS.getLongestCommonSubString("123456789", "123456789"));
            System.out.println(LCSS.getLongestCommonSubString("12345", "123456789"));
            System.out.println(LCSS.getLongestCommonSubString("12345", "1234c56789"));
            }
           
      }

Now, That's going to bring this blog post to an end. Thanks for reading.
