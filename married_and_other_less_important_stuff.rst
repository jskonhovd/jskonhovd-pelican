Married!!! and other less important stuff
#########################################
:date: 2013-3-19 19:22
:category: Programing
:tags: Racket  
:author: Jeffrey Skonhovd

So, I am married!!!!!!!!!!  I told you guys I have been busy for a
reason. On a very important date in February, My
wife and I got married in front of family and friends in Memphis,
Tennessee. I have never been more happy in my life.

I still remember the day I met Megan. It was six years ago at the
University of Memphis. My brother and I were commuter students. I
don't exactly remember why, but we started to hang out in the honors
student lounge on campus between classes. Since, we had no where else to
go. That's were I met Megan. It took awhile, but eventually I got over
being a introvert for a moment and I asked her out.  I remember how
nervous I was before our first date.  That was the most important time
of my life, so far. That semester I meet the love of my life, and I
switch majors to Computer Engineering.

The wedding was beautiful. We had an exciting honeymoon at Universal
Orlando, Florida. The only issue was driving from Memphis to Orlando,
which I don't recommend to anyone ever. Universal is a lot of fun and
the weather was great for February. I did spend extravagantly more
money on Harry Potter merchandise than anyone should ever, but Megan was
cool with it.

.. image:: http://i.imgur.com/3R07GFG.jpg

On to the less important stuff, I am behind on my Coursera Programming
Language class by about two weeks. I still have the section on Ruby to
finish, and I need to take the final. I knew I was going to have to
take about three weeks off for the wedding before I started the class.
Even if I will not get a statement of accomplishment, I still am happy
that I took the class.

Since I feel I learned so much from this last course, I am planning to
continue taking more Coursera courses. The next class I plan on taking
is Martin Odersky class on Functional Programming in Scala. Coursera
is a wonderful site, because the range of different classes available.
I plan on taking more classes in the future, but I also would like to
start finishing up my backlog of books I need to read.

So what is one of my blog posts without random programs I have written!!!! I
honestly don't know. The following samples of code is Fizzbuzz and Quicksort
written in Racket, and a Topcoder problem I completed about a month
ago in C#. 


The following is my version of Fizzbuzz in Racket. This is simlar to the SML version I posted earlier, because
it uses recursion. I know most of the bindings are not used. I made the mistake of trying to 
bind those variables earlier. That was a little awkward. 

.. code-block:: scheme
	
	#lang racket
	(define (fizzbuzz i)
	(letrec (
		   [modthree (remainder i 3)]
		   [modfive (remainder i 5)]
		   [modthreeandfive (remainder i 15)]
		   [f (lambda (x lst)
		        (cond[(> x 100) (print lst)]
		             [(eq? (remainder x 15) 0) (f (+ x 1) (append lst (cons "fizzbuzz" null)))]
		             [(eq? (remainder x 3) 0) (f (+ x 1) (append lst (cons "fizz" null))) ]
		             [(eq? (remainder x 5) 0) (f (+ x 1) (append lst (cons "buzz" null)))]
		             [#t (f (+ x 1) (append lst (cons x null)))]))]
		   
		   )
	(f i '())))


The next problem is quicksort in Racket. This is pretty basic, refer to CLRS if you don't 
understand any part of it.

.. code-block:: scheme
	
	#lang racket
	(define (quicksort xs)
	  (letrec (
		       [pivot (if (empty? xs) xs (car xs))]
		       [tail (if (empty? xs) '() (cdr xs))]
		       [grt (filter (lambda(x) (> x pivot)) tail)]
		       [lst (filter (lambda(x) (<= x pivot)) tail)])
		(if (empty? xs)
		      xs
		     (append (quicksort lst) (list pivot) (quicksort grt) ))
		 )
	  )


Finally, This is the only topcoder problem I have done in the past month. I need to do more, but with work and 
Coursera I haven't had time.

.. code-block:: csharp

	using System;
	using System.Text;
	using System.Text.RegularExpressions;
	using System.Collections;
	using System.Collections.Generic;
	// BEGIN CUT HERE
	namespace topcoder
	{
	// END CUT HERE
	public class Chopsticks {
		public int getmax(int[] length) {
		    int res = 0;

		    Dictionary<int, int> k =new Dictionary<int,int>();

		    for (int i = 0; i < length.Length; i++)
		    {
		        if(!k.ContainsKey(length[i]))
		        {
		            k.Add(length[i], 1);
		        }
		        else
		        {
		            k[length[i]]++;
		        }

		    }

		    foreach (KeyValuePair<int, int> j in k)
		    {
		        if (j.Value % 2 == 0)
		        {
		            res += j.Value / 2;
		        }
		        else
		        {
		            res += (j.Value - 1) / 2;
		        }
		    }
		    return res;
		}
	}

Well, I hope you guys enjoyed this blog post. Good night!!
