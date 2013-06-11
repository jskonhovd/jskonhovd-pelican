CF - Heads or Tails - Python
############################
:date: 2012-11-11 18:20
:category: Programming
:tags: Python
:author: Jeffrey Skonhovd
:excerpt: Codeforces

I had trouble with this problem. The problem statement took me awhile to wrap my head around.

.. code-block:: python

    #! /usr/bin/python
    x,y,a,b = map(int, raw_input().split())

    ans = []
    for i in range(a,x+1):
        for j in range(b, y+1):
            if(i>j):
                ans.append((i,j))

    print len(ans)    
    for s in ans:
        print s[0], s[1]

Bye!!
