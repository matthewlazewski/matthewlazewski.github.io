---
layout: post
title:      "My Rails Project"
date:       2020-07-30 20:56:38 +0000
permalink:  my_rails_project
---


For my rails project I wanted to create an application that would allow users to search through workouts of all types and find one that suits what they are feeling that day. Users would also be able to create their own workouts and also review and comment on workouts they have done. 


To do this I needed four tables: users, categories, workouts, and comments. Users would have many comments and workouts as well as many categories through workouts. Categories would have many workouts and many users through workouts. Comments would belong to a user and a workout. Workouts would belong to a user and a category while also having many comments and many users through comments. The schema ended up having two join tables: comments and workouts. 

I first created my login and signup features. I was also able to implement a login through Facebook feature using OmniAuth. This process was made much easier using ActiveRecord validations as well as has_secure_password. 

```
validates :email, :password, uniqueness: true 
 validates :username, :email, :password, :height, :weight, presence: true 
```

To simplify the security of most of my application. I implemented a logged_in? helper method, which utilized another helper method, current_user, to prevent access to most every page if a user was not logged in. This was made possible using another built in rails method, before_action :logged_in?, in my controllers. Using this saved me the hassle (and the hand cramps) of having to include something like if @user.id == current_user in just about every method in my application. 

The most difficult table to put together for me was the comments table. Comments belong to both a user and a workout and had to be associated to both upon creation. In order to create a comment, I had to be able to add both foreign keys within the post action. 

```
  def create
        @workout = Workout.find(params[:workout_id])
        @comment = @workout.comments.create(comment_params)
        @comment.user_id = current_user.id       
        if @comment.save
            redirect_to workout_path(@workout)
        else 
            redirect_to root_path
        end
    end
```

Using this method I found the workout then created a new comment that was already attached to it by chaining methods. Then on the next line I set the user_id of the comment to the id of the current user. 

Compared to Sinatra, which required a lot more code, building this project with Rails was much easier. I was able to spend more time perfecting the features of my application and less time building out CRUD methods and routes. The rails gem simplifies a lot of the tedious CRUD actions and allows developers to have uniform actions and work together more efficiently than if they were to build them out from scratch. 


