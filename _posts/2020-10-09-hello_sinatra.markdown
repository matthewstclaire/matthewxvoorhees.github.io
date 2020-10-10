---
layout: post
title:      "Hello Sinatra!"
date:       2020-10-10 00:15:39 +0000
permalink:  hello_sinatra
---


I just recently completed my first project using the Sinatra library and I am happy to say it gave me a much needed reinvigoration. Many of the projects and labs I was working on didn't leave me feeling very accomplished. Luckily Sinatra was right around the corner to remind me how fun programming is. The finished product has some functionality that I am actually excited about. 

Book Keeper was an application I built to help a user keep track of the books they have read. It allows a user to login and logout. Once logged in a user can submit posts that represent books they have read. Once a post is created they can edit or delete that post. Along with those basic functions I require all users to have a reading goal. On their index page their reading goal is updated as they read more books. 

Leading up to the Sinatra project were learned a lot about CRUD functions. There are functions designed to create, read, update and delete. In many instances during our labs we were tasks with writing these functions out. It wasn't until I worked with my own web application that they made sense to me. I wanted to outline how these concepts fleshed out in my application. I hope that this gives clear insight into how these functions work through the view of controller. 

```
get '/posts/new' do
        redirect_if_not_logged_in
        erb :"posts/new"
    end
```
	
This snippet of code begins my create function. At this point I have a database and I am waiting for a user to submit a form that will add to that database. You can see that when you access my "posts/new" route that the program will then display what is listed on my ERB file name "new."  ERB, Embeded Ruby, allows Ruby and HTML to work together in order to display information to a user. I have a form on that page that allows a user to fill out what is required in order to add data to our database. 
		
```
post '/posts' do
        post = current_user.posts.build(params)
        if post.save
            redirect "/posts/#{post.id}"
        else
            redirect "posts/new"
        end
    end
```
		
The first snippet above is only doing part of the job. We now have a user at our form. They then complete the form. Now we have our "post" route. What this does is receive that information from a user and decides what to do with it. In this case we assign a variable to post that attaches the current user to that specific post with the parameters given. In this case it would be what they filled in on the form. We then save that information into our "posts" database and we redirect the user to a show page where they can view the information they just entered.

```
get '/posts/:id' do
        redirect_if_not_logged_in
        @post = Post.find_by_id(params[:id])
        erb :"posts/show"
    end
```
		
This code represents the "read" portion of the CRUD. This will show a user their entry from the database by looking for their data based on the ID. It will then direct you to the ERB known as "show" which will show the user their specific post. 

```
get '/posts/:id/edit' do
        redirect_if_not_logged_in
        @users = User.all
        @post = Post.find_by_id(params[:id])
        if @post.user.id == current_user.id
             erb :"posts/edit"
        else
             redirect "/posts"
         end
    end
```

Editing starts with my code above. This route will lead us to a specific user's posts. We will then end up at the edit ERB which will, believe it or not, issue another form! This form will load in what was entered in the post previously. 

```
    patch '/posts/:id' do
        @post = Post.find_by_id(params[:id])
        params.delete("_method")
        if @post.update(params)
            redirect "/posts/#{@post.id}"
        else
            redirect "posts/new"
        end
    end
```

This part does differ from creating a new post. Due to the fact we have data in our database for the original form we want to delete the old information and add the new information. This part can be tricky because we get used to the get and post requests. However it is easy to thing that the database had a bad piece in it. So we will patch that bad piece with a new piece and move on.

    ```delete '/posts/:id' do
        @post = Post.find_by_id(params[:id])
        if @post.user.id == current_user.id
            @post.destroy
        end
        redirect "/posts"
    end```
		
Lastly, we have our delete method. The big difference here is that delete does not have an ERB attached to it. This function doesn't display anything back to the user and does not require any form completion. Once the button is hit it is gone forever! 

That being said delete does have it's own form that exists in an ERB. Just not an ERB specific to delete. If this wasn't the case then we'd never find it!

## Conclusion
Sinatra was a great experience for me. Seeing all of the parts come together helped me in a big way. I got a glimpse into how all of these smaller concepts form together to make something greater. It was greatly important to my self esteem and well as my understanding of the course thus far. I can't wait to get into Rails!
