Dynamic Programing - Java
###########################
:date: 2012-12-14 00:13
:category: Programing
:tags: Java
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

Now this issue with this program is pretty
      
