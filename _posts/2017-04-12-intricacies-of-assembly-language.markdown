---
layout: post
title:  "Intricacies Of Assembly Language"
date:   2017-04-12 01:25:40 -0500
categories: programming assembly
---

As anticipated, this semester has started off at a ferocious pace. Several of my classes required significant setup before beginning the actual course material. My Assembly class requires the use of Microsoft Visual Studio. As I work primarily on a Mac, this posed a significant hurdle to overcome right off the bat. Thankfully, I found a good solution in using Bootcamp to install Windows 10 and Visual Studio. The main downside is that I have to restart to swap between operating systems, but it is working out fine so far.

With the initial setup complete I was able to dive into the course material. Talk about being blasted by a fire hose of information! The first two chapters I read gave a very detailed look at a computer's hardware and how it all works together. This was difficult material to wade through. Initially, I failed to make a connection between hardware and programming. 

This changed once I made it to the programming assignment for the first week. I realized that all those registers, memory locations, and components are under my direct control with Assembly. I can literally command a value to move between specific registers within my computer and perform certain tasks once there. I also quickly learned that writing a program in Assembly takes much more time than in C++. 

Let's look at a brief example. Say I want to take two integer variables, initialize them with a value, add them and store the sum in a third variable.
In C++ I could accomplish this very quickly with the following:

{% highlight C++ %}
int main()
{
  int x = 3,
      y = 4,
      z = x + y;
}
{% endhighlight %}

A program performing these same operations may look something like this in Assembly: 

{% highlight Assembly %}
.data

  x     DWORD   3
  y     DWORD   4
  z     DWORD   ?

  .code
  main PROC

  mov   eax, x
  add   eax, y
  mov   z, eax

main ENDP

END main
{% endhighlight %}

Being a lower-level language, the syntax is certainly not as user-friendly as C++. But with some practice I was able to complete an arithmetic calculator without too much difficulty. So far I'm enjoying learning something so different from what I encountered last semester.

## YouTube Channel
Another goal of mine this semester is to upload a few helpful tutorials to YouTube. In my web development course I noticed that several students had questions about testing `HTML` and `CSS` files. Since there wasn't any instruction on this topic in the course material I decided to make my first tutorial video which can be seen here:
<iframe width="560" height="315" src="https://www.youtube.com/embed/nFvzhWFQdIk" frameborder="0" allowfullscreen></iframe>
I hope to make more tutorials throughout the term. They ensure that I understand the material, and they also help my classmates so it's a win-win!
