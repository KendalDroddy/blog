---
layout: post
title:  "The Devil Is In The Details"
date:   2017-03-22 08:59:40 -0500
categories: programming c++
---

I'm currently finishing up my first semester as a computer science student
at Oregon State University. The amount of content we covered was nearly 
overwhelming, but there are certainly some lessons I learned that stand out.
As I reflect over this past semester I hope to cover these lessons in my blog, 
beginning today!

Something I picked up very quickly is the fact that programming a computer is a
very precise science. Computers are incredibly powerful but they must be given
explicit instructions on how to carry out the tasks they perform. Even the slightest
mistake in spelling or syntax can cause dozens of errors to propogate when compiling.
This is exactly what happened to me on a recent assignment for my Introduction to
Programming course.

One of my final projects was to create a rudimentary online shopping program using
C++. This program utilized three separate classes which allowed a `Store` object to be created that holds `Product` and `Customer` objects. Products could be added to a certain customer's cart, and then they could check out. The member function controlling the checkout process began:

{% highlight c++ %}
void Store::checkOutMember(std::string mID)
{
  //Total price variable
  double total;
{% endhighlight %}

The remainder of this function loops through a vector containing the customer's items,
adds up the prices, and initializes `total` to that value. The program ran great for a single customer. Items were tallied up correctly and the proper total was displayed. But things went sour when I created multiple `Customer` objects to test. Since `total` was not initialized when the function began, the value ended up carrying over in full or in part to my second customer's cart! This means the second customer was paying for items that they didn't want, and that the first customer already purchased. 

I was clued into this error by compiling my code and running it using `valgrind` as follows which produced dozens of the following errors:

{% highlight bash %}
==3079== Conditional jump or move depends on uninitialised value(s)
{% endhighlight %}

Unfortunately, I discovered this flaw a mere two hours before the deadline. I initially thought the problem may be a result of faulty pointer manipulation. This has troubled me on previous assignments, but everything looked clean. My `valgrind` run also told me:

{% highlight bash %}
==3079== HEAP SUMMARY:
==3079==     in use at exit: 0 bytes in 0 blocks
==3079==   total heap usage: 40 allocs, 40 frees, 1,105 bytes allocated
==3079== 
==3079== All heap blocks were freed -- no leaks are possible
{% endhighlight %}

So, I was confident that my pointers were fine, otherwise a memory leak would be likely. After searching and testing for 1.5 hours I stopped and stared at `double total;`. Everything clicked and I realized this was the uninitialized value referenced earlier. I added a `= 0;` and tested again. It worked perfectly!

While similar situations have previously arisen, this would the most stressful and had the highest stakes. It was also a valuable learning experience. Now that I've made this mistake, I am equipped to handle it should I ever encounter another in the future.

