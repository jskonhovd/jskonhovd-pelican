TC - AlternateColors - Java
###########################
:date: 2012-12-19 21:00
:category: Programming
:tags: Java
:author: Jeffrey Skonhovd
:excerpt: topcoder

Topcoder!!! The following is my solution for the 500 point problem from SRM 564 DIV 2.


.. code-block:: java

    import java.util.*;
    public class AlternateColors {
    public String getColor(long r, long g, long b, long k) {
        String res[] = {"RED", "GREEN","BLUE"};
        Long v[] = {r,g,b};
        long m = Long.MAX_VALUE;
        int t = 3;
        while(t > 1)
        {
            m = v[0];
            for(int i =1; i < t; i++)
            {
                m = Math.min(v[i], m);         
            }
           
            if(k <= m*t)
            {
                return res[(int)((k-1) % t)];         
            }
           
            k -= t * m;
            int oldt = t;
            t = 0;
            for(int i = 0; i<oldt; i++)
            {
                if((v[i] - m) > 0)
                {
                    v[t] = v[i] - m;
                    res[t++] = res[i];   
                }
            }
        }       
        return res[0];
    }
   
Have a good day!!!

