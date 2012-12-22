TC - FauxPalindromes - Java
###########################
:date: 2012-12-14 00:13
:category: Programing
:tags: Java
:author: Jeffrey Skonhovd
:excerpt: topcoder


I am happy to inform you all that I found sometime to work on Topcoder Problems!!!!! My big project at work has been completed. This was my first "real" software project outside of my university coursework. The rest of my tickets had been bug fixes before this. I could blog all day on what I learned, and I probably should, but that can come at a later date.  

On to the problem, FauxPalindromes is a simple 250 problem. 

.. code-block:: java

	import java.util.*;
	public class FauxPalindromes {
		
		public boolean isPalindrome(String str)
		{
			boolean ret = true;
			for(int i = 0; i < str.length(); i++)
			{
				int l = str.length();
				if(str.charAt(i) != str.charAt(l-i-1))
				{
					ret = false;
				}
			}

			return ret;
		}
		
		public boolean isFauxPalindrome(String str)
		{
			
			String retStr = str;
			
			retStr = this.buildFauxString(retStr);

			return this.isPalindrome(retStr);
		}
		
		public String buildFauxString(String str)
		{
			String ret = str;
			String temp = "";
			List<String> s = new ArrayList<String>();
			for(int i = 0; i < str.length(); i++)
			{
				if( i+1 < str.length()  && str.charAt(i) == str.charAt(i+1))
				{
					temp = temp + str.charAt(i);
				}
				else
				{
					if(temp != "")
						s.add(temp + str.charAt(i));
					temp = "";
				}
			}
			for(int j = 0; j < s.size(); j++)
			{
				char replaceString  = s.get(j).charAt(0);
				
				ret = ret.replaceFirst(s.get(j), String.valueOf(replaceString));
				
			}
			return ret;
		}
		
		public String classifyIt(String word) {
			
			if(isPalindrome(word))
				return"PALINDROME";
			
			if(isFauxPalindrome(word))
				return "FAUX";                       	        	
			 
			return "NOT EVEN FAUX";
		}

	}

The solution is pretty straight forward. However, I must say I failed verification. I used replace instead of replaceFirst. I felt terrible. Anyway, Goodnight.
