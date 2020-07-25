---
layout: post
title:      "Building your first Sinatra app — Three things to know"
date:       2020-07-25 08:31:50 +0000
permalink:  building_your_first_sinatra_app_three_things_to_know
---

1) CRUD methods

2) Corneal gem

3) MVC

What is CRUD?

Create, Read, Update, Delete/Destroy (CRUD). When building web applications developers construct models, which I will discuss in a little more detail down below. For most models to be considered complete they will need to be able to perform the following four actions:

Create — functions that allows for a new entry with a unique access identifier
Read — functions that allows access to entries of a specified model, this may be one entry or many entries
Update — functions that allow for entries to be modified, this may be the entire entry or specific fields
Destroy — functions that allow for the deletion of an entry

Understanding and utilizing these functions on your models is an important step in web development.

File structure template with Corneal

For many people in the beginning stages of their web development journey, remembering all the files and connections is challenging. Often times you may not know where to begin which can be a huge roadblock to your success. Thats where templates come in handy! A template framework may greatly reduce the lift needed for you to get started on your project, while also helping you learn all the necessary file connections along the way.

Corneal is a ruby gem that generates all the files for our Sinatra app. These files will serve as your template to get you started. Corneal was created by Brian Emory and can be found by searching for ‘Corneal’ at https://rubygems.org/.
Step by step instructions for how to install the gem can be found here: https://thebrianemory.github.io/corneal/

Model, View, Controller — MVC

Model, view, controller or MVC is an architectural design pattern used to separate application concerns. Utilizing MVC principles may help you generate scalable code that is easier to maintain and less buggy.

Model — represents the data and contains no logic on how to represent that data to a user
View — represents the interface between the data and the user. The view can access the model data, but does not know what this data means or what the user can do to manipulate it
Controller — represents the interface between the data and the view. The controller receives interactions from the view and executes these actions typically by retrieving data from the model, which may result in sending information back to the view for the user

There is a learning curve to understanding the MVC, but take the time to truly learn it. The MVC is an amazing way to organize clean, simple, and easy to scale code. It will enhance your ability to work with others and control your own applications better.



