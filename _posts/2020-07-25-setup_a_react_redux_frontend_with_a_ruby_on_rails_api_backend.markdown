---
layout: post
title:      "Setup a React + Redux frontend with a Ruby on Rails API backend"
date:       2020-07-25 08:34:57 +0000
permalink:  setup_a_react_redux_frontend_with_a_ruby_on_rails_api_backend
---

Utilizing this approach we are able to leverage the popular frontend libraries of Javascript and the simple, yet powerful server side framework Ruby on Rails provides to build a modern web application. Lets begin.
Backend
Generate a new rails project to serve as the backend by running the following command:
rails new <project name> --api
(NOTE: consider installing any additional dependencies or Webpacks specific to your application (e.g., PostgreSQL, Webpack bundler)
Navigate into the root directory of your new project:
cd <project name>
Inside the root directory folder there will be many generated files that make up the structure of the Rails application. We will now initialize the database and test to be sure all went well during initialization. Run the following commands:
rails db:create
rails s
Image for post
You’re now on Rails.
Next, add any additional Ruby gems to Gemfile located in your project. Gems can be used to modify or extend capabilities of Ruby. Some gems to consider are cors-rack and pry.
(NOTE: don’t forget to run bundle install after adding gems)
Next, let build out or generate the MVC components of your backend application.
To generate models run: rails generate model <model name>
To generate controllers run: rails generate controller <Controller name>
(NOTE: Learn more here about rails generate here: https://guides.rubyonrails.org/command_line.html#rails-generate)
After generating models and controllers, the backend is setup and you are now ready to start to coding specific components for your project. Navigate to your controllers to build the logic for actions your application will conduct. Utilize your models to develop the schema for your database. Next, we will add a frontend to our project.
(NOTE: Other important aspects of backend setup not discussed including: configuring routes, seeding the database, CORS, model association, authentication)
Frontend
Navigate to the top level folder of your project and run the command:
npm install -g create-react -app
create-react-app <project name>
(NOTE: Create a top level folder that contains two separate folders for your frontend and backend. The backend project we setup in the walkthrough above in one folder; the frontend project we are setting up now in another folder.)
After initialization with create react app (which may take a few minutes). Test setup by running the following command:
npm start
Image for post
The frontend of the project communicates with the backend utilizing PORTs. We can specify which ports the backend API will be called on. To do this, in the newly created React project navigate to your package.json file and add the following command:
“proxy”: “http://localhost:3000”
(NOTE: any available port can be utilized)
This tells react to begin all API call with this initial address. We will then add more specific endpoints for each request. These endpoints will correspond to the controller actions we setup in our backend API.
Once the ports are referenced and configured you can build components in your React frontend that interact with data stored in your Ruby on Rails backend. These components can access that data in the API in many ways. A popular way is middleware called Axios. Axios is a promise based HTTP client that transports JSON data. Learn more about Axios here: https://github.com/axios/axios.
This completes the initialization of the React frontend. It is now time to build specific components for your project. These components can link to the Ruby on Rails backend to carry out CRUD functions to store, access, update, and delete data.


The content of your blog post goes here.
