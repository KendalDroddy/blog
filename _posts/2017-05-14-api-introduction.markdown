---
layout: post
title:  "First Taste of APIs"
date:   2017-05-14 08:25:40 -0500
categories: programming api
---

This semester has been moving along at an unbelievable pace. I'm taking my final midterm for the quarter in just a few hours, and several large projects are looming just over the horizon. But on of the positives to such a rigorous semester is the sheer amount of new material I'm learning!

As of late, the most interesting material I've learned comes from my web development course. Having built a solid foundation with JavaScript, we are now venturing into the world of application program interfaces, or API for short. 

What's In An API?
=================

An API provides a user with a set of pre-defined tools that they can then use to build other pages or applications. I was unfamiliar with them previously, but I now see the world of possibilities that they open up to developers. This was most clearly demonstrated in an assignment I completed for my course. Utilizing OpenWeatherMap's API, we were required to build a webpage that would load the weather for a user-submitted city or zipcode via HTML form. Using Bootstrap, I set up a page with the necessary fields without too much difficulty. My Javascript took a bit longer as this was my first attempt at using an API. You can see a portion of my implementation below: 

{% highlight JavaScript %}
  function sendRequest() {
    var req = new XMLHttpRequest();

    //Get user's input from city and zipcode fields
    var cityValue = document.getElementById("city_input").value;
    var zipCodeValue = document.getElementById("zipcode_input").value;

    //If else statement to generate the correct URL based on user's input
    if (cityValue == "" && zipCodeValue != "") {
      req.open("GET", urlFirst + "zip=" + zipCodeValue + urlSecond, false);
    }
    else if(cityValue != "" && zipCodeValue == "") {
      req.open("GET", urlFirst + "q=" + cityValue + urlSecond, false);
    }

    req.send(null);
    var response = JSON.parse(req.responseText);
    console.log(response);
    document.getElementById("city").textContent = response.name;
    //Convert temperature from K to F
    document.getElementById("temp").textContent = Math.round((response.main.temp 
      * (9/5) - 459.67)) + " F";
    document.getElementById("humidity").textContent = response.main.humidity;
    document.getElementById("description").textContent = response.
      weather[0].description;

    event.preventDefault();
  }
}
{% endhighlight %}

This function is embedded another function which adds an event to the submit button on my page. Once clicked, this function will trigger, sending a request for the necessary information. Once the information returns, it must be parsed and the applied to the correct HTML elements. For my purposes, I chose to display the city name, temperature, humidity, and description of the weather.
This event ends with `preventDefault();` in order to keep the page from reloading. This ensures that the data is properly displayed after the request is made. Here is the result:

![OpenWeathMap API Example](/img/weather.png)

My next project involves creating a How-To guide for the National Park Services Data API. I'm excited to dig in and see what I can do with it!