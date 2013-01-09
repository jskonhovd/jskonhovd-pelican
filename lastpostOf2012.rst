Last Post of the Year
#####################
:date: 2012-12-30 16:44
:category: Programing
:tags: Java
:author: Jeffrey Skonhovd

This should be my last post of 2012. I have a couple of programming contest solutions, and some goals for the new year. I am going to start this post by going over a couple of goals for 2013.

Goals for 2013:

- Contribute to Open Source
- Improve my rating on Topcoder and CodeForces
- Continue to do CrossFit three days a week
- Make less, but longer, blog posts
- Continue to read 75 pages a week in technical related books
- Take my Knowledge of C to a different level
- Be Great at my Job
- Improve my github
- Study for Graduate School

By contributing to Open Source, I believe I can make a significant improvement in my overall skill as a software developer. This should be the hardest goal on my list, I don't know what project I want to work on, and where the time will come out of my schedule. I will blog when I finally come up with a plan to tackle this project.

I would also like to improve my rating on TopCoder and CodeForces. The only way I will improve this is by practising on problems and keep reading CLRS. I am going to block out sometime on Saturdays to work on this goal.

I also want to make fewer blog posts, and focus on the content of my blog. In the past I have worried about the numbers of times I post. I was worried about quitting. I had to show myself that I was improving in some tangible measurable way. For me, That way was counting the number of blog posts a month. I am over this, because of two reasons. The first was that it's just an awful way to measure yourself. Second, It created unproductive bad habits. I have be sticking to the easy programming problems on Topcoder and Codeforces so I would have more blog posts. I know I won't learn that way, I need to push myself.

I love programming in C, it is just fun. I did a lot of C programming in my EECE degree, but I am no good at it. I want C to become one of my better languages. I am currently reading a book called The C Programming Language, by Kernighan and Ritchie. I love this book so far, and I think I am relearning this language the right way. I have other items on my list. I might blog on those at a later date. I think these are some pretty intense goals for 2013, but you need to aim high right?

We can now begin with the first solution. The problem was GregsWorkOut, which is a A level problem from Codeforces. This problem is very simple, it's all really implementation and using modular arithmetic.

.. code-block:: java

    import java.util.Arrays;
    import java.util.Scanner;


    public class GregsWorkOut_A {

    public static void main(String args[])
    {
        Scanner sc = new Scanner(System.in);
        int a = sc.nextInt();
        int[] ans = new int[3];
        String[] sans = {"chest", "biceps", "back"};
        for(int i =0; i<a; i++)
        {
            ans[(i % 3)] += sc.nextInt();
        }
        int max = 0;
        int index = 0;
        for(int i = 0; i < 3; i++)
        {

            if(ans[i] > max)
            {
                max = Math.max(max, ans[i]);
                index = i;
            }

        }

        System.out.println(sans[index]);
        }

    }

The second problem was from Topcoder. I am getting pretty good with the easy implementation problems on Codeforces and Topcoder. This problem is call ValueHistogram and it can fall in that category.

.. code-block:: java

    import java.util.*;
    public class ValueHistogram {
   
        public String makeString(int h, int[] num)
        {
            String ret = "";
            for(int i = 0; i < num.length; i++)
            {
                if(h > num[i])
                {
               
                    ret = ret + ".";
                }
                else
                {
                    ret = ret + "X";
                }
           
            }
       
            return ret;
        }
   
   
        public int findLargest(int[] num)
        {
            int max = 0;
            for(int i =0; i < num.length; i++)
            {
                max = Math.max(max, num[i]);
            }
            return max;
        }

        public String[] build(int[] values) {
        String[] res = {""};
       
        int[] num = new int[10];
        for(int i = 0; i < values.length; i++)
        {
            num[values[i]]++;
        }
       
        int h = findLargest(num);
        h = h + 1;
       
        List<String> ret = new ArrayList<String>();
       
        while(h > 0)
        {
            ret.add(makeString(h, num));
            h--;
        }
        return ret.toArray(new String[0]);
        }
    }

In this problem, We build out an array called num[], which represents the numbers 0-9. We then count the number of times each number is called. Next, I find h, which is the number that occurs most in this new array and increment it by one. After that, We can easily build the strings needed for the solution by determining if h > num[i].

