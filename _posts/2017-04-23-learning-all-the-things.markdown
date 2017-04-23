---
layout: post
title:  "Learning All The Things"
date:   2017-04-23 08:25:40 -0500
categories: programming 
---

As I'm typing this my first hackathon event, HackDFW, is coming to a close. Over 36 hours have passed and around 1,000 students have been programming nearly the entire time. While I'm completely exhausted, it has been an exciting two days. But, most importantly, I've learned a lot - more than I ever thought I could squeeze into such a short period of time!

New Tech - MondoDB
===================

One of the event sponsors was Toyota and they hoped to see us create a product that aids in fuel-efficient driving. My team sought to create an app that awards points based on how efficient a user's most recent drive was. The system would be points based, derived from telemetry data which Toyota provided. 

My job was to create a sign-in page for the site - something I've never done. I've heard about MondoDB though, so I figured I'd try that and to see if it would work. I felt relatively comfortable giving it a shot since we've touched on database basics in my CS 290 course.

You can see a snippet of my code for this portion below: 

{% highlight JavaScript %}
MongoClient.connect('mongodb://<dbuser>:<dbpassword>@ds115701.mlab.com:15701/users', (err, database) => {
  if (err) return console.log(err)
  db = database
  app.listen(process.env.PORT || 3000, () => {
    console.log('listening on 3000')
  })
})
{% endhighlight %}

With this single code block I can initialize my database and begin storing data. This was all done through an html form I created in my `index.html` file. I entered some information into the form and clicked submit. Refreshing my database pages showed that the information was added! It was really neat to see this take place in real time. It also helps understand how so many web apps out there actually work.