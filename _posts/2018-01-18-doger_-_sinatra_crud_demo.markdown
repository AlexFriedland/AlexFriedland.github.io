---
layout: post
title:      "Doger - Sinatra CRUD project"
date:       2018-01-18 21:39:00 -0500
permalink:  doger_-_sinatra_crud_demo
---


I found this project to be pretty simple.  I also think my coding skills have turned a corner. I used to get frustrated with errors and discouraged.  Now I'm pretty zen and just take it step by step. 

My first step here was getting the file structure setup. I decided to try to use the rails console commands to build the initial filetree, but the file structure it stubbed out for me was pointing to folders and files I haven't worked with before, so I scrapped that and just built it manually myself.

Then I built the database.  Again, pretty simple, I want Users, Dogs and Walks.  Users have many dogs and walks.  Dogs have many Walks and vice versa (Dogs <-> Walks).  Once I built that, I built the models and tested the functionality.

When I was satisfied, the real work began - building the views and controller actions.  My experience in doing these projects so far has been that despite my planning, as I build, the scope of the project changes as I see what works, and what doesnt.  For this one, I really only needed it to do a couple things:

* Log in or sign up new Users.
* Display basic user information, plus their dogs
* Clicking on a dog shows it's information, it's walks, and allows you to edit or delete it.
* Same thing for walks
* logout

I really like the bcrypt gem, I find netsec really interesting and look forward to learning more about encryption and cracks as I move forward.  I was a little confused by the attention paid to brute force hacks in the tutorials on encryption; I'd assumed one can generally get in more elegantly, but maybe I'm wrong.  

Speaking of elegantly, I felt like there was a much simpler way of validating whether or not a username is already taken (when registering a new user), but I'm a newb and this is my solution:


```ruby
if User.all.any? {|user| user.username == params["username"]}
      redirect "/failure"
    else
      @user = User.new(email: params["email"], username: params["username"], password_digest: params["password"])
```




