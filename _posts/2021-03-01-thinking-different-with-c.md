---
layout: post
title: "Problem solving with The C Programming Language"
---
Most of my development career, I have been working with higher 
level programming languages.


I wanted to learn a new programming language, that would help me 
grow as a developer. I landed on C since it is a middle level language. I started working through 
[The C Programming Language][c-programming] by Brian Kernighan and Dennis Ritchie.     

One of the problems illustrated the simplicity of the way that C makes you think:

`Write a program to print a histogram of the frequencies of the lengths of words in its input`

My usual approach in a higher level language would be to create a dictionary with the word length as the key and increment the value when a word of the same length is repeated. 


Here is an example in C#

{% highlight C# %}


using System;
using System.Collections.Generic;
using System.Linq;
					
public class Program
{
	public static void Main()
	{
		
		Dictionary<int, int> wordLengths = new Dictionary<int, int>();
		string input = Console.ReadLine();
		
		List<string> words = input.Split().ToList();
		
		foreach(string word in words)
		{
			int key = word.Length;
			if( word.Length > 0)
			{				
				if( !wordLengths.ContainsKey(key)) 
				{
					wordLengths.Add(key, 1);
				}
				else
				{
					wordLengths[key] = wordLengths[key] + 1;
				}
			}
		}
		
		foreach(KeyValuePair<int, int> entry in wordLengths)
		{
			Console.Write(entry.Key);
			for(int i = 0; i < entry.Value; i++)
			{
				Console.Write("-");
			}
			Console.WriteLine();
		}
	}
}
{% endhighlight %}


In C it seemed better to have an array of the length of the longest word
and for each letter you incremented the value at the index of 
the length of the word.  

Here is an example in C:
{% highlight C %}

  #define LONGESTWORD 45

  int main()
  {
    int i, j, c;
    int letterCount; 
    int wordLengths[LONGESTWORD];

    letterCount = 0;
    for(i = 0; i < LONGESTWORD; i++) {
      wordLengths[i] = 0;
    }

    while((c = getchar()) != EOF){\
      if( c == ' ' || c == '\n' || c == '\t') {
        ++wordLengths[letterCount];
        letterCount = 0;       
      }
      else {
        ++letterCount;
      }
    }

    ++wordLengths[letterCount];
    printf("\n");
    
    for ( i = 0; i < LONGESTWORD; i++){
      if(wordLengths[i] > 0){
        printf("%d", i);
        for(j = 0; j < wordLengths[i]; j++){
          printf("-");
        }
        printf("\n");
      }
    }
    printf("\n");
  }

{% endhighlight %}


Conclusion:  
Despite these solutions being possible in both languagues.
The restrictions of C push you to find different solutions that 
you would usually reach for in higher level languages. 


[c-programming]:https://en.wikipedia.org/wiki/The_C_Programming_Language
