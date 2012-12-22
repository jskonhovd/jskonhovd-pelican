CF - Dividing Orange - Python
#############################
:date: 2012-11-18 16:47
:category: Programing
:tags: Python
:author: Jeffrey Skonhovd
:excerpt: Codeforces

This problem was alright. I had trouble with it, but I evenutally got it. It's kinda simple. Build your list, I called mine foo, of possible numbers without the numbers in a. Then start your answers with a[i] + whatever is foo, while removing the used numbers in foo.

.. code-block:: python

	#!/usr/bin/python
	n, k = map(int, raw_input().split())
	a = map(int, raw_input().split())
	foo = range(1, n*k+1)
	for i in range(len(a)):
    		foo.remove(a[i])

	A = [[x] for x in a]

	for j in range(k):
    		for h in range(n-1):
        		A[j].append(foo.pop())
    		print ' '.join(map(str,A[j]))

Anyway, I listened to Belle & Sebastian radio on Pandora while performing this problem. I must say i miss 2002, when I first heard of this band. I am forever getting older, but it seems my interests are the same as they where 10 years ago. Wow.
