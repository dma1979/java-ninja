[All questions](README.md)

# Miscellaneous

## What is Software Development Life Cycle?
* Planning
* Requirements Analysis
* Design
* Implementation / Development
* Testing 
* Deployment
* Maintenance and improvement

## Are you interested in further developing your skills?
Software engineering is a job in which you need to always thrive and sharpen your skills. 

## What os AJAX?
AJAX is the abbreviation of Asynchronous JavaScript and XML. AJAX is a technique for creating better, faster, and more interactive web applications with the help of XML, HTML, CSS, and JavaScript.

## How would you explain APIs to non-technical stakeholders?
It’s the messenger between software products. It allows software systems to communicate with each other and synchronize.

## Explain a non-functional requirement and a functional one?
A non-functional requirement describes a system’s type (accessibility, maintainability, security). 
A functional requirement describes the specific functionality of that system.


## What is the difference between black box and white box testing?
Black box testing is only used for establishing a correct output given an input. 
In contrast, white box testing also covers the implementation of that particular function — it tests whether its implementation is correct or not.

## Can you describe the model-view-controller (MVC) architecture?
It separates data from the user interface. 
The MVC architecture is mostly used for GUI applications. 
The model layer contains the data, the view layer sends the data to the user, and the controller is the one that makes changes to the model based on user input.

## What is a recursive function?
A function that calls itself directly or indirectly. The recursion continues until it reaches a set of parameters that return a value instead of calling the function recursively. 

## How to explain big-O notation in the simplest terms?
The big-O notation tells how fast an algorithm is. 
Big-O notation, also known as Landau’s symbol, tells how the runtime or space requirement of a function grows as the input grows. Which means that the algorithm speed isn’t measured in seconds but in the growth of the number of operations.


## How does the A* algorithm work?
It’s a computer algorithm widely used in pathfinding and graph traversal. 
It works with a heuristic function that estimates the cost of going from node A to B. 
The nodes in each step are huddled together in a priority queue.

It uses the formula f(n) = g(n) + h(n) to add every, adjacent to the start node, node into the queue along with their cost estimates. 
g(n) is the actual cost from the start node to node n, whereas h(n) is the heuristic function. 
At each step, the node with the lowest estimated cost f(n) is further expanded. And a path is finished when the final node is the one that expands.

[Table of content](#miscellaneous)

## Problem 1 
Input: You have a list of N+1 integers between 1 and N. You know there’s at least one duplicate, but there might be more. For example, if N=3, your list might be 3, 1, 1, 3 or it might be 1, 3, 2, 2. Print out a number that appears in the list more than once. (That is, in the first example, you can print ‘1’ or ‘3’ — you don’t have to print both.)
Basic solution: The most obvious approach is to compare every number in the list to every other number until you find a duplicate with O(n²) time and O(1) space complexities.
Improved solution: you could just use a boolean array and use the integer values as indices with O(n) time complexity to iterate through the list and O(n) space complexity for the array/hash.

