---
layout: post
title:      "Ruby - Command Line Interface (CLI) to an external data source"
date:       2020-07-25 08:27:47 +0000
permalink:  ruby_-_command_line_interface_cli_to_an_external_data_source
---


This post provides information on:
· Command line interface: (More info: 1 / 2)
· Ruby gems
· Bundler
· Web scraping with Nokogiri: (More info: 1 / 2 / 3 / 4)
· Gemspec: (More info: 1)
· Local Ruby gem execution
· Ruby gem publishing

Overview: This post describes how to create and publish a Ruby gem to parse a web page and provide scraped data to a user via a command line interface.

Command Line Interface
The command line interface (CLI) provides a means for the user to issues actions to a program application. Unlike a graphical user interface (GUI), which primarily utilizes graphical images, CLI users enter typed text-based commands into a prompt.

The example application we will build for this post will provide a CLI prompt allowing the user to interact with the program by typing commands and receiving a program response the same way.

Ruby Gems
Step 1: Create a gem
To get started, we will create a gem. By creating a gem, we will be able to manage, install, and share the application with others or for use in other libraries or applications we develop by requiring the gem.
Ruby gems package ruby code together. Many of the programs we use everyday rely on helpful libraries that can be found in the Rubygems community. Anyone can easily search, install, or share a Ruby gem with the Rubygems community.
Ruby gems typically contain the same standard structure of code organization. A gems basic components are:
· Code — usually found in a lib folder
· Documentation — usually a README document with installation instructions
· Gemspec — usually contains information about the gem’s files, test information, platform, version number and more are all laid out here along with the author’s email and name

Bundler
Step 2: Create gem file structure

Bundler is a tool to create the basic component of the gem. To create a gem using Bundler navigate to your desired application folder. Then enter the following in your command line interface (CLI):
bundle gem <your new application name>
Example:
bundle gem my_new_program
This command will create the file structure for your new gem and initialize a Git repository, if Git is installed. If this is your first time using Bundler you will be asked whether you want to include the CODE_OF_CONDUCT.md and LICENSE.txt files with your project.
The CLI output for your project will be similar to the following:
MIT License enabled in config
Code of conduct enabled in config
create <your new application name>/Gemfile
create <your new application name>/lib/nonono.rb
create <your new application name>/lib/nonono/version.rb
create <your new application name>/nonono.gemspec
create <your new application name>/Rakefile
create <your new application name>/README.md
create <your new application name>/bin/console
create <your new application name>/bin/setup
create <your new application name>/.gitignore
create <your new application name>/LICENSE.txt
create <your new application name>/CODE_OF_CONDUCT.md
Initializing git repo in <your new application folder location>
Gem ‘<your new application name>’ was successfully created. For more information on making a RubyGem visit https://bundler.io/guides/creating_gem.html
The file structure provided by Bundler provides the directories needed to begin the process of developing code for your application. Additional files may need to be created as your application grows in complexity.

Web Scraping with Nokogiri
Step 3: Collecting data from an external source
For this particular example, we will use Nokogiri to parse data from an html web page. Nokogiri is a gem that searches documents via XPath or CSS3 selectors. To install Nokogiri enter the following command in your command line interface (CLI) prompt:
gem install nokogiri
In order to use the Nokogiri gem in your application we need to require it. The require method imports class and method definitions from the required gem file in order to execute all its statements in your application. To require Nokogiri in your application add the following line to the code file where you would like to use the gem:
require ‘nokogiri’
Navigate to the gemspec file of your application and add the following line to the dependency:
spec.add_dependency “nokogiri”
Nokogiri is a large library and has many uses. We are using Nokogiri to parse CSS selectors and return data from an external web page. To open the web page as if it were a file we will use the wrapper gem OpenURI. To require OpenURI in your application add the following line to the code file where you would like to use the gem:
require ‘open-uri’
Next, we will fetch and parse the HTML. Add the following line to the code file:
<any variable> = Nokogiri::HTML(open(<any webpage>)
Example:
doc = Nokogiri::HTML(open(‘https://nokogiri.org/tutorials/installing_nokogiri.html'))
This will open the webpage as HTML and provide access to parse the CSS selectors. Extracting data from web elements is called scraping. Next, we will scrape data using CSS selectors. Ability to select elements with CSS is a great skill to develop, learn more here.
It may be necessary to iterate through CSS selectors to provide all the data. Scrape and output the HTML using CSS by adding the following line to the code file:
<fetch variable>.css(‘CSS Selector’).each do |<iteration variable>|
puts <iteration variable>.text
end
Example:
doc.css(‘nav ul.menu li a’, ‘article h2’).each do |link|
puts link.content
end
This will return text found by the CSS selector. You may need to utilize other methods or use regex to return data you intend to scrape.

Gemspec
Step 4: Generate the gemspec
The gemspec file defines what’s in the gem, who made it, and the version of the gem. It also provides all the information needed to share your gem with the Rubygems community. Many of the components of the gemspec are completed for you when you create a basic file structure with Bundler.
After completing the gemspec you can run the gem locally to test it out or publish the gem to share with the Rubygems community. Some important fields to complete are:
· spec.summary — brief description of the gem
· spec.description — longer detailed version that explain the gem
· spec.homepage — URL of the gems home page
· spec.executables — executable Ruby files to be run by the gem
· spec.require_paths — paths in the gem to add to $LOAD_PATH when this gem is activated
· spec.add_development_dependency — adds a development dependency named gem with requirements to this gem. Development dependencies aren’t installed by default and aren’t activated when a gem is required.
· spec.add_dependency — dependencies required to run the gem
With the gemspec complete you can now generate a gemspec file. To generate the gemspec file enter the following command in your command line interface (CLI) prompt:
gem build <your new application name>.gemspec
Example:
gem build my_new_program
The output for this command will build the gem and a gemspec file that will include the version number in the file name and will be similar to the following:
Successfully built RubyGem
Name: my_new_program
Version: 0.0.0
File: my_new_program -0.0.0.gem
Local Ruby gem execution
Step 5: Running and testing your application locally
Once you have completed your application code and created your gem file you can run your gem locally to test it or use it in another application. To install the gem locally enter the following command in your command line interface (CLI) prompt:
gem install <your new application name>.gemspec
Example:
gem install my_new_program.gemspec
The output for this command will install the gem and will be similar to the following:
Successfully installed my_new_program-0.0.0
1 gem installed
Installing ri documentation for my_new_program-0.0.0…
Installing RDoc documentation my_new_program0.0.0…
The gem is now installed on your local system. To use the gem the final step is to require the gem and run it in an irb session. To do this follow these steps:
1) open command line interface and start a new irb session
2) enter the following command in the irb session:
require ‘<your new application name>’
Example:
require ‘my_new_program’
3) execute the application based upon your code — this may be done by initializing a new instance, executing a file placed in the bin directory, shebang file execution, etc.
Publishing Ruby Gems
Step 6: Sharing your application
Once you have completed your application and tested it locally you are now ready to share it with the Rubygems community. To share your gem, you’ll need to create an account or sign-in by supplying an email address, a handle (username) and a password.
To publish your gem enter the following command in your command line interface (CLI) prompt:
gem push <your new application name>-<version>.gem
Example:
gem push my_new_program-0.1.1.gem
The output for this command will push the gem to RubyGems.org and will be similar to the following:
Pushing gem to RubyGems.org…
Successfully registered gem: my_new_program (0.1.0)
Your gem can now be found by searching the Rubygems community, installed, and utilized by Ruby users around the world.
