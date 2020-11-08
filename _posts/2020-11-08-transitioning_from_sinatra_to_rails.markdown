---
layout: post
title:      "Transitioning from Sinatra to Rails"
date:       2020-11-08 21:16:01 +0000
permalink:  transitioning_from_sinatra_to_rails
---


Somewhere during my time with Sinatra I felt I really had things under control. For one of the only times in my coding journey I felt like I was able to bring my ideas to fruition rather painlessly. I noticed I was troubleshooting much more naturally and efficiently. The Sinatra project was a great time and my confidence was at a high. 

It is made very clear that programming through a bootcamp is a rollercoaster of emotions. I can certainly testify to this as my Sinatra high became a 90 degree fall with many loops along the way. Rails quickly became a daunting concept to understand. However, after struggling to understand the lessons and then using that knowledge for my Rails project I can testify there is light at the end of the tunnel. I have a few ideas that could help somebody making their transition from Sinatra to Rails.

## Don't get stuck in a Sinatra mindset

A lot of the processes you will use in Sinatra can easily become the truth across the board for how things are done. This is an idea that existed in my head. Through the power of rails many processes you do in Rails can be done easily in Rails. This was a setback for me due to the fact I was so stuck in Sinatra mindset that I couldn't see these processes for what they were. An easy example that took me a while to understand is forms. Look at my form below for my Sinatra project. 

```
<input type="text" name = "title" id = "title"></br>
<label>Author:</label></br>
<input type="text" name = "author" id = "author"></br>
<label>Genre:</label> </br>
<input id="genre" type="text" name="genre"></br>
<label>Description:</label></br>
<input type="text" name = "description" id = "description"></br>
<label>Review:</label></br>
<input type="text" name = "review" id = "review"></br>
</p>
<input type="submit" id="Submit">
</form>
```

Here you can see a basic Sinatra form to submit title, author, genre, description and review. After I finished Sinatra I could easily read this form. Now look at a similar form, but done it rails. 

```<%= form_for @workout do |f| %>
    <h3>Workout Name/Date</h3>
    <%= f.text_field :workout_name %><br>
    <h3>Warm Up</h3>
    <%= f.text_area :warmup %><br>
    <h3>Power</h3>
    <%= f.text_area :power %><br>
    <h3>Endurance</h3>
    <%= f.text_area :endurance %><br>
    <br>
    <%= f.submit %>
  <% end %>```
	
It took me a long time to feel comfortable with a Rails form. Now looking back and comparing the two I am blown away by how beautiful the Rails form_for form truly is. Using your instance variable you're able to iterate through all of the fields and then easily send the input data into your database. The fields are easily labeled with the HTML, type of text field, and keys from your database. This one example of many that took me a while to transition my mindset towards. 

## You know more than you think

When looking at my completed Rails and Sinatra projects they aren't all that different. What is different is how much code I am writing to do a task in Sinatra vs Rails. Rails has so much power that it can be hard to understand. Sinatra is a way to transition you from writing raw Ruby to using the magic that is Rails. Truly if you were to make that jump without Sinatra as the bridge you wouldn't be able to understand how things are working. As developers we need to know what is happening on the backend. Macros are fantastic, but can create bugs that you would never be able to work out if you couldn't begin to describe what is happening on the back end. 

## Embrace the change

Another point for me that is taking time to adapt to is writing better code. Early on my only focus was getting a lab to pass or something to display to a user in a way I liked. That feeling is great. However now it is time to transition your mindset to writing better code. The goal will inevitably be to make your code more DRY. (Don't repeat yourself) Rails give you a new ability to write code that is cleaner and more abstract than ever. As you are progressing through the transition constantly challenge yourself to see if you can make your code easier to understand, more concise and overall better. As I am at the end of Rails I look back and wish I had embraced this more. I now find it challenging to bring myself to really examine code that I may have struggled to write in any format. 
