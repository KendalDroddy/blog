---
layout: post
title:  "CSS Media Queries"
date:   2017-05-01 08:25:40 -0500
categories: programming 
---

I recently found my first opportunity to create a live website for a local cycling group! I frequently ride with this group and happened to notice their website was expired. So I mentioned this to the club's vice president, and I ended up with the task of redesigning their site from the ground up!

The majority of their information is found on their team's Facebook page. For this reason I decided to design a hero-style landing page for the team. I decided to use Bootstrap as my framework as it is well-suited to creating a simple, yet beautiful page. 

Hero Component
==============
![Programmers at Earthack](/img/hero.png)

One of the first issues I encountered was placing text on top of the image. Including an image and some text within a `div` element just stacks vertically. I wanted my text on top of the actual image. I searched around and eventually devised the solution seen here: 

{% highlight CSS %}
.hero-container {
  background: linear-gradient(0deg, black, transparent 40%),
              black url('../img/cycling2.jpg') no-repeat;
  background-size: cover;
  background-position: 15% 85%;
}

.hero-img {
  opacity: 0.0;
}
{% endhighlight %}

First, I placed the image and text within my `div`. I included the image here to ensure my div was the proper size. The trick is in the fact that I set the images `opacity` to 0. Then I set the `background` to the image I wanted to appear. This background image covers the entire `div`, including the space taken up by the text within the div. As can be seen, this provides the perfect look that I had in mind. 

However, I encountered a problem when I began testing this element at various breakpoints. On the iPhone 6 and smaller screens, the text was much too large. It was so large in fact that it completely skewed the way the background image was displayed. To counter this, I implemented the following media query: 

{% highlight CSS %}
@media (max-width: 450px) {
h1 {
  font-size: 2.625rem;
}
.hero-text {
  font-size: .925rem;
}
}
{% endhighlight %}

I implemented the breakpoint at a max width of 450 pixels which covers the iPhone 6 and all smaller devices. I then reduced the font size within this breakpoint to ensure all my content is correctly displayed on these screens. After testing again, it worked perfectly! Now onto the next element of the site.