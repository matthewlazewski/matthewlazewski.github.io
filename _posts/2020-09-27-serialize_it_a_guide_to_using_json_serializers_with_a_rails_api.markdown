---
layout: post
title:      "Serialize It: A Guide to Using JSON Serializers With A Rails API"
date:       2020-09-27 22:50:33 +0000
permalink:  serialize_it_a_guide_to_using_json_serializers_with_a_rails_api
---


API’s, or application programming interfaces, can be great. They store data and allow that data to be accessed, and sometimes modified, by other applications through requests. You can find API’s already created on anything from your favorite foods to every stat about every Pokemon ever created.
When building your own application, it isn’t uncommon to build your own API to store your data. Ruby on Rails, and it’s extremely user friendly MVC (model, view, controller) framework, makes it incredibly easy to build your own API from scratch. You can even tell Rails your creating an API upon creation using :

``$ rails new my_api_name --api``


This tells Rails to only create you the files, gems, and functionality needed to create your API while still allowing you to set up your relationships on the backend.
So your API is set up and storing data. You’re probably feeling pretty good about yourself. You go to your frontend application, write your fetch request, and oh no! None of your relationships are saved. Your dream of sorting cat pictures by category is dead, you have no way to store the pictures within the category on your back end. At least not an easy one.

Enter JSON serializers. Serialization is the process of converting data stored in an object into a string that can be easily sent between servers or from a server to a browser. By adding serializer classes to your Ruby API application, you easily control the content of the object being passed to your frontend.

**Step 1: Install Fast_jsonapi and Make a Serializer Directory**

``gem install fast_jsonapi
mkdir Serializers
touch base_serializer.rb``

Within the serializer directory you will create a base_serializer folder as well as a folder for each of your Rails classes. This base serializer will include fastjson_api, and each of the other classes will inherit from the Base Serializer.

``class BaseSerializer
include FastJsonapi::ObjectSerializer
end``

Each class needs to include the attributes to be included in each class as well as the relationships you want to keep record of. For example, a User serializer for a social media app would look like:

``class UserSerializer < BaseSerializer
attributes :name, :email
has_many :posts
has_many :likes
has_many :comments
end``

**Step 2: Add Serializers To Your Model**

Like any other class, serializers need to be instantiated. In order to get the result you want, your serializers need to be instantiated inside of your model. Let’s take our user model again. Ideally, upon creation we would want to save the new instance to our API, assuming it is valid. To achieve this we would want our create method to look like:
``def show
@user = User.find(params[:id])
if @user.save
render json: {
user: UserSerializer.new(@user)
}
else
render json: {
status: 500,
errors: ['user not found']
}
end
end``

Here, if the user is valid and it saves, we call our UserSerializer just like any other class within our render json method, and we get a beautiful API that looks something like this.
Serialized User API

**Step 3: Sit Back and Smile**

There you have it. With an organized API like that you can go into your frontend application and have most of the heavy lifting done for you. With just a simple fetch request you can easily access all of your data and the data that relates to it, saving yourself a ton of time and a major headache.


