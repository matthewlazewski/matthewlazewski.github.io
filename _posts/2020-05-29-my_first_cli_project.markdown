---
layout: post
title:      "My First CLI Project"
date:       2020-05-29 20:34:55 +0000
permalink:  my_first_cli_project
---


For my CLI project, I created a database that provides information about newspaper publications throughout history. The API i used was from chroniclingamerica.loc.gov. I chose to use my home state, Oklahoma, but the API method fetch_newspapers can be modified to work for any state of your choosing. 

The first thing I wanted my CLI to do was create a new instance for each newspaper. To do this, I first parsed the API and saved it as a hash. After that I created an array to store the hash. To create a new instance I iterated through the array and pulled the five pieces of information I wanted from each newspaper instance, the title, place of publication, the start year, the end year (if applicable), and the frequency the publication was published. Each instance was then saved to an array all in my newspaper class. 

Once I had the instances where I wanted them, it was time to start the CLI. I created a start method that introduces the program then immediately call the homepage method that gives user two options, to list all the publications or to see more options. The first option was very straightforward. It simply listed all the applications by name next to a number. The number was based on the index of the Newspaper.all method plus 1. I was able to accomplish this using .each.with_index(1), a trick I had previously not known about. If the user selects a number. It returns the five pieces of information I pulled from the API then gives the option to return to the homepage or exit the program.

The more options page was where I got the chance to be creative. I wanted to do as much as possible with the information I had pulled. I first created two methods, one that returns all current publications and another that returns all publications that were published daily. I was later able to create one method that would create a list based on the information I wanted to return, which I used to refactor those two methods. Next I created a method that listed the newspapers based on when they were first released. I did this my using .sort on the all array and return them with the name and year. The hardest method to create was the search method. This method takes in user input then using the .find method on the all array it returns the info of that newspaper if there is a match.  





I have always been fascinated by computers. How they work, the parts that go into them, and how much they can do. When I was a kid, any time something wasn’t working on our home computers my parents would call on me to try to fix it. I may have only been in elementary school and had no idea what I was doing, but after clicking a few things and downloading something (and probably deleting other things in the process), I would almost always fix it somehow.
As I got older I still used them and was good with them, but never thought to pursue it any further than fixing issues on my own laptop and never learning why something was working. I got into the restaurant industry at 16 and never looked back. It was all I knew. I was good at it and I had fun doing it. I even got earned a bachelor’s degree in Hospitality Management. They always joked in school about working long nights, weekends, and holidays but at the time I was too stubborn to know what that really entailed. I took a job right after school and immediately felt every bit of that. I worked constantly. I missed family dinners, holidays, special events, everything. I never saw my family and friends and when I did I was too tired to enjoy it.
Coding always interested me, but it felt too broad and I had no idea where to even start. It was something I really wanted to do but just didn’t know how, and also I was scared to leave behind the only business I had ever known. I remember riding to the airport at 3:00 am the day after Thanksgiving so I could catch the earliest flight back home to get to work. My family had big plans that day but I had to miss them. It dawned on me then I needed a change. I immediately got on google and simply searched “Learn to Code”. It pointed me to an app that taught basic HTML, CSS, and Javascript. I downloaded it immediately and was hooked. It was all I did for weeks in my free time. It was so cool to see something so simple make something so elegant. I eventually did some more research and discovered bootcamps and knew that was what I needed to do. I hatched a plan to save up, leave my job, and eventually pursue software engineering full-time.

