Post in February 2013
#######################
:date: 2013-2-11 22:12
:category: Programming
:author: Jeffrey Skonhovd
:excerpt: What is this for?

It's been a good start to 2013. I am not directly making progress on all my goals for 2013 yet, but I am making progress in spirit.

I am currently taking an online course over at Coursera on `Programming Languages_`. The course is an interesting introduction to functional programming, at least first part of the course. I never had exposure to Functional Programming at my University, and I have found this course to be an interesting substitute.

I think I am doing well considering my schedule. I try to complete the homework on my weekends, when I am not travelling. But I have been travelling quite a bit on the weekends, for a pretty good reason.

The first part of this course is going over the Standard ML language. I am pretty sure I will never have to program in this Language as a professional, but I find it interesting :). The following is a quick example of Fizzbuzz, which is written in SML.

.. code-block:: SMLLexer

    fun fizzbuzz() =
            let fun helper(i : int, acc : string list) =
                if i < 100
                then case (i mod 3 = 0, i mod 5 = 0) of
                 (true, false) => helper(i+1, acc@["Fizz"])
               | (false, true) => helper(i+1, acc@["Buzz"])
               | (true, true) => helper(i+1, acc@["FizzBuzz"])
               | (false, false)  => helper(i+1, acc@[Int.toString i])
                else acc
        in
            helper(1,[])
        end
   
    val x = fizzbuzz()

In addition to the course, I also finished chapter 1 of The C Programming Language back in January. I will continue that book once I feel like taking a break on Coursera. I also planed on taking another course on Coursera in March, but I will determine if I can based on my schedule.

Now to that pretty good reason for travelling so much. Well, That's going to have to wait for my next blog post. Lets just say, I am taking a big step forward in my life and I have never been happier. :)


.. _`Programming Languages`: https://www.coursera.org/course/proglang
