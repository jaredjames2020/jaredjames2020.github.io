---
layout: post
title:      "Creating Nested Resources and associations for a Rails Application"
date:       2020-07-25 08:33:03 +0000
permalink:  creating_nested_resources_and_associations_for_a_rails_application
---


Active Record associations help to build relationships between models. An association is a connection between Active Record models. Utilizing associations, such as belongs_to and has_many, creates related resources that gives you the ability to manage standard Create, Read, Update, and Delete (CRUD) operations. Associations may also be used to develop in nested routes which you can place routing resources within other resources.
Step 1:
Create the application
$ rails new content-app
We will use scaffold to save time to generate a content management database application.
Step 2:
Generate scaffold Post resource
$ rails generate scaffold Post title:string body:text
This places a title:string and body:text in the posts database table.
Step 3:
Generate scaffold Comment resource
$ rails generate scaffold Comment comment:text post:references
Step 4:
Setup Post model associations
class Post < ActiveRecord::Base
validates :name, :presence => true
validates :title, :presence => true, :length => { :minimum => 5 }
has_many :comments
end
Step 5:
Setup nested resources ; config routes
resources :posts do
resources :comments
end
Step 6:
Add validations to the Comment resource
class Comment < ActiveRecord::Base
validates :commenter, :presence => true
validates :body, :presence => true
belongs_to :post
end
Step 7:
Edit the Comment controller
class CommentsController < ApplicationController

GET /posts/:post_id/comments

GET /posts/:post_id/comments.xml

def index
#1st you retrieve the post thanks to params[:post_id]

post = Post.find(params[:post_id])
#2nd you get all the comments of this post

@comments = post.comments
end
end

GET /posts/:post_id/comments/:id

GET /comments/:id.xml

def show
#1st you retrieve the post thanks to params[:post_id]

post = Post.find(params[:post_id])
#2nd you retrieve the comment thanks to params[:id]

@comment = post.comments.find(params[:id])
end
end

GET /posts/:post_id/comments/new

GET /posts/:post_id/comments/new.xml

def new
#1st you retrieve the post thanks to params[:post_id]

post = Post.find(params[:post_id])
#2nd you build a new one

@comment = post.comments.build
end
end
