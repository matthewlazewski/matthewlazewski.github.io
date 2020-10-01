---
layout: post
title:      "Linked Lists: What are They and How Do They Work?"
date:       2020-10-01 19:09:53 +0000
permalink:  linked_lists_what_are_they_and_how_do_they_work
---







When beginning my coding journey, I spent hours learning what an array was. How to add, find, delete, and iterate through them. I felt like I could take any array and do whatever I wanted with it. Then along came objects, which were a little trickier, but after some more practice and as my coding confidence grew, I could do just about whatever I wanted to an object I wanted to. I thought I was the king of data manipulation. Ask me to get all the keys in an object…boom you got it. Ask me to remove the nth item in an array…done. Then along came linked lists…

You may think right off the bat, how much different could a linked list be? Surely there’s built in methods to add to the beginning and end, delete, and find whatever you want. I was once that naive too.

**So What Exactly is a Linked List?**
At its simplest, a linked list is a linear data structure similar to an array. However, unlike an array, items in a linked list do not have indices. Meaning you cannot call, for example, LinkedList[3] to grab the fourth element in your linked list. Instead, they are connected by a chain of references, where each node references the next one.

**Linked List Breakdown**
Each list is marked by a head and the data is marked as data. Meaning you could call LinkedList.head.data to receive the content on the first node in any linked list. The box on the right marked next is the reference the next node in the chain, so LinkedList.head.next.data would equal to b, and so on. When LinkedList.next is equal to null, that is how our code knows we have reached the end of the list. Each link in the chain is a node, and a node is just a simple JavaScript object. However, the built in JavaScript function we have come to know and love, such as Object.keys(), do not work on linked lists. This is where things get tricky.

**Traversing and Modifying Linked Lists**
Without built-in methods, it is pretty easy to conclude that we will not be able to modify a linked list as easy as an object or an array. Let’s say we have a JavaScript class set up for a linked list.

``class LinkedList {
    constructor(value) {
        this.head = {
            value: 1,
            next: null
        };        this.length = 1;
    }
}
{head: {value: 1, next: null}}``

Here we have a list with just one node containing the value of one. With just basic JavaScript knowledge, we can probably conclude that if we wanted to add a new node to the front, we could do something like:

``addToFront(val){
  const newNode = { value }; 
        newNode.next = this.head;  
        this.head = newNode;       
        this.length++;
        return this;
}``

Pretty simple right? We create a new node, then we set newNode.next to equal the head, establishing our new node as the head. We then add one to the length of the list so our code knows to look for two nodes.
In order to remove a node from the head, we do something very similar:

``removeFromFront() {
        if (this.length === 0) {
            return undefined;
        }
        
        const value = this.head.value;
        this.head = this.head.next;
        this.length--;
        
        return value;
    }``
Here we take the value of the current head and set it to a variable. We then assign the value of next to the head and subtract one from the length. So instead of deleting it directly, we essentially just remove it from existence.
But what if we want to delete a node thats not at the front? This is where linked lists can get a little tricky. We now know how the lists work, start at the head, then iterate through using .next, but how do find the value we’re looking for, then delete it from the list? What is the best way to iterate through a linked list? The answer is a while loop.

``delete(val) {
        if(this.length === 0) {
            return undefined;
        }
        
        if (this.head.value === val) {
            this.head = this.head.next;
            this.length--;
        }
        
        let previousNode = this.head;
        let currentNode = previousNode.next;
        
        while(currentNode) {
            if(currentNode.value === val) {
                break;
            }
            
            previousNode = currentNode;
            currentNode = currentNode.next;
        }
        
        if (currentNode === null) {
            return undefined;
        }
        
        previousNode.next = currentNode.next;
        this.length--;
        return this;
    }``
		
We start with our easy cases. If the length is 0, there’s nothing to delete. If the value to delete is the head, we handle it like our previous function. For iteration, we want to establish two variables, a previous node, which represents the head, then a current node, which represents one after the previous node. Then comes our while loop. We want to iterate as long as there is a truthy value to currentNode, when it is null (the end of the list) we want it to stop. Once we find our value, we set previousNode to currentNode and currentNode to currentNode.next, making previousNode the node we want to delete. Then after our iteration, we set previousNode.next to currentNode.next, which removes previousNode from our list and boom…deleted. It may seem hard to wrap your head around, but with a little practice that little lightbulb in your head will be going off before you know it.

**But Why?**
Arrays can be expensive when it comes to memory. Using indices requires the computer to use a lot of memory space because every time an array is modified, it must sort through the entire array and reset all of the indices. Using linked lists, while harder to grasps and arguably harder to maneuver, we can save memory and add, find, and sort to our hearts content, making them an extremely useful option when deciding how to store your data.

