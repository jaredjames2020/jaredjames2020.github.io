---
layout: post
title:      "Scope: An introduction - Global vs Local"
date:       2020-07-25 09:31:36 +0000
permalink:  scope_an_introduction_-_global_vs_local
---


Scope and hoisting is an important and some what difficult concept to grasp. It is a key priniciple in Javascript development and will be needed to learn well to build a solid foundation. Learning these concepts took work so I will try to break them down and explain some of the things I have learned. 

What is scope?

Scope in Javascript is the location that defines where you can access variable, objects, and functions. Scope changes throughout your application and it is important to always know where you are at. There are two main scope area global, which encompasses the any variable located outside a function, and local, variables declared inside a function. Because local scope contain varibles that are inside function it also referred to as function scope. In turn, functions may also be put inside other functions which is termed nested scope. There are other names for scoped areas, such as blocked scope, but for this post we will stick with the overview. 

Global scope

As mentioned, global scope is for variable declared outside a function. Global scope is the outermost scope. These variables are called global variables and can be accessed and modified from locations throughout your application and also inside functions. Global variables are available for the lifetime of the application. Global variables are a powerful tool, but because of their high accessibility and long lifespan, it is important to use them only when appropriate. As you can imagine, as you build larger and more complex applications keep track of many global variable can get tricky and lead to bugs. 

Local scope

Variable declared inside a function are considered to have local scope. These variable can not be accessed or modified outside of the defined scope location. Local scope encompasses a variety of different nuances. Some of these include scopes within a block, module, or other functions. Variable declaration is also important with scoping concepts as var, and let and const have different implications when considering scope. Scopes can also be nested meaning while inside an inner scopes you can access variables of an outer scope. 

Things to remember

There are two main scope locations: Global and local. Local scope can be further broken up into sub-locations that exist throughtout an application. Global variables can be accessed anywhere within the application so be careful of how you use. Local variable can not be accessed outside their defined location, but scopes can be nested for alternative access. 

