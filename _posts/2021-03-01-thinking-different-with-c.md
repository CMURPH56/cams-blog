---
layout: post
title: "Problem solving with The C Programming Language"
---
Most of my development career I have been working with higher 
level programming languages. Recently I have started working
through [The C Programming Language][c-programming] by Kernighan and 
Ritchie.  

One of the problems illustrated the simplicity of the way that C makes you think:

`Write a program to print a histogram of the frequencies of the lengths of words in its input`

My usual approach in a higher level language would be to create a dictionary with the word length as the key and increment the value when a word of the same length is repeated. 


Here is an example in C#


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


[c-programming]:https://en.wikipedia.org/wiki/The_C_Programming_Language
