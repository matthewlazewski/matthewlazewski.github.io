---
layout: post
title:      "My Sinatra Project"
date:       2020-06-26 03:01:40 +0000
permalink:  my_sinatra_project
---


Going in to my Sinatra project, I was extremely excited to finally build an actual working website. Something I could show to my friends and family and have them actually be able to use it and understand it (no offense to my CLI project). 

I really liked the idea of an interface where users could make posts for everyone to see, but I wanted to take it one step further. I was originally going to make it an app for any business to see who does what and users could post for all to see. I ended up catering it towards restaurants specifically. 

I began with my schema. I had three tables: users, jobs, and posts. Users would belong to a job and have many posts, jobs would have many users, and posts would belong to a user. Upon sign up each new user would have to provide a username, an email, a unique password, and choose their job. 

After logging in each user is sent to the posts index page. Which shows all posts from users. They can then click on the post to see it by itself and who wrote it or create one of their own. Users can only edit their own posts. This is protected by comparing current_user.id to post.user_id. The edit button is only an option if you are the owner of the post. 

Users can also view a list of all employees. Each user can be clicked on and sent to a page with that users name and job. Users can also go to the jobs page and view all the jobs within the business. Clicking on one of the jobs sends the user to a list of said job along with all the users who have that job. 

Jobs can only be created and edited by users with "admin" authorization. I was able to do this by creating a row on the users table titled admin with a boolean value. That way only certain users have access to creating and editing jobs. 

All of my routes were secured through proper error handling. This was most challenging in posts. In /posts/index.erb, I used the line <% if @post.user == current_user %> to create an edit and delete button that can only be viewed by the creator of the post and I protected the route itself using  

``` if current_user.id != @post.user_id
            flash[:message] = "You don't have access to edit this post. " 
            redirect to '/posts'
        end``` 
				
				
All CRUD methods also require a user to be logged in. That way only users of the site can view its contents. 

This project was much more challenging but also much more fulfilling than the first. I felt a great sense of pride viewing my finished product and also more confident in what I have learned than ever before. 


