CLRS - Dynamic Programing - Java
###########################
:date: 2012-12-14 00:13
:category: Programing
:tags: Java CLRS
:author: Jeffrey Skonhovd
:excerpt: Dynamic Programing


Hey again, This blog post with cover the topic of dynamic programming. According to Wikipedia, 
Dynamic Programing is a method for solving complex problems by breaking them down into simpler subproblems. 
That doesn't help to much. So lets start a simple example with a program that doesn't use Dynamic Programing, 
and the performance issues associted with it. 

This problem is a classic. We want to write a function that calculates the value of the nth memeber of the Fibonacci.

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
        DynamicPrograming a = new DynamicPrograming();
        System.out.println(a.fib(0));
        System.out.println(a.fib(15));
        }
    }

Now the issue with this program is pretty obvious right? We are recalculating fib mutliple times while we go down the call 
stack. This becomes an issue when N becomes larger. This solution is an exponential time algorithm.

Now using dynamic programing, We can come up with a much better solution. The idea of Dynamic Programing is to break down your
program into smaller sunproblems. This way you can reuse the infomation from each subproblem to build your answer. The following
is my solution to the creating a function that calculates the value of the nth memeber of the Fibonacci, using Dynamic Programing.

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
            DynamicPrograming a = new DynamicPrograming();
            System.out.println(a.fib2(0));
            System.out.println(a.fib2(0));
            }
      }

Now I am sure you are asking. Jeff, This seems simple enough. But can you use this techinque to solve 
more nontrival problems? Well, Yes we can. There are a large number of good problems you can solve with Dynamic Programing.
The difficulty I have is understanding when you can use Dynamic Programing, or understanding when to use it.

This next problem is another classic problem you can solve using Dynamic Programing. The longest common substring problem is
a classic in Computer Science. the longest common substring problem is to find the longest string that is a substring 
of two or more strings. 

