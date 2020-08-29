---
layout: post
title:      "OnPar-My Javascript Project"
date:       2020-08-29 17:05:59 +0000
permalink:  onpar-my_javascript_project
---


In my past life, I managed a kitchen for a local restaurant. I spent most of my time counting what we had on hand, comparing it to what we needed to have in stock, and then figuring out how much we need to order of each item. It was a very tedious process, and it always felt like there was a better way to accomplish this. With my newly acquired coding skills, I was able to accomplish this on a small scale.

My application, OnPar, is a single page JS application that groups items into their department, tracks pars and onhand amounts, and then tells you how much of each product to order to be fully stocked.

Once I had my migrations set up using rails, the first thing I wanted to do was figure out how to render all of my different item and department lists without having to refresh the page. After quite a bit of trial and error, I decided the best plan of action would be to create two list divs, one for items and one for departments, and have them default to hidden. I also created new buttons to go inside each div. Next I created a navbar attached to a navigate function in my index.js.

```
function navigate(){
  switch(true) {
    case (event.target.id === "departments-nav"):
      container.innerHTML = ""
      Department.all.forEach((i) => {
        i.attachToDom()
        i.addEventListeners()
      }) 
      Department.newDeptEventListener()
      departmentList.hidden = false
      itemList.hidden = true 
      break;
    case (event.target.id === "items-nav"):
      container.innerHTML = ""
      Item.all.forEach((i) => {
        i.attachToDom()
        i.addEventListeners()
      })
      newItemButton.hidden = false 
      Item.newItemEventListener()
      departmentList.hidden = true 
      break;
  }
}

```

Using a switch statment, I was able to attach all of my logic for each class to their buttons as well as render a list of all of them. 

With the navigation in place. I then wanted to create CRUD actions for my classes. For items, I wanted to have all four of them. I wanted users to be able to create items and then update or delete them. For departments, I wanted less control. Ideally I did not want any user to be able to modify or delete departments, it didn't make sense to have that if this was a larger application. Maybe if I had implemented different access levels it would have made more sense. I just wanted users to be able to add new departments.

My biggest challenge with CRUD actions was created a new item and attaching it to an existing department. This took many tries. I tried for loops, while loops, for in loops, everything. I was about to give up and just settle for an input box when, with a little bit of help, I was able to get it working using 

```
static dropDownMenu(){
        const depts = Department.all

        return depts.map((d) => {
            return `<option value=${d.id}>${d.name}</option>`
        }).join(' ')
    }
```

and all was right with the world.

This project, to me, was by far the most challenging. Coming off of rails, which is amazing and does most of the heavy lifting for you, Javascript was an entirely new challenge. DOM manipulation is incredibly tricky, frustrating, and beautiful at the same time, and I can safely say that even though some of the functionality of this project pushed me to edge, I finished it feeling more confident in my coding than ever before.
