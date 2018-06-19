---
layout: post
title:      "Pieces of an App: The files you need to start a Rails App"
date:       2018-06-19 15:29:39 +0000
permalink:  pieces_of_an_app_the_files_you_need_to_start_a_rails_app
---


One of my biggest questions in starting my first Rails app from scratch was which files I actually needed to get up and running. What do they all do? How do they all connect and relate? Most tutorials get you up and running from a default scaffolding, so this was all pretty fresh to me.

## Root Files
Most notably, your Gemfile lives here which is responsible to installing any gem your app is dependent upon. When executed, your Gemfile also generates a Gemfile.lock. Gemfile.lock is specifically in charge of versioning your gems.

Other notable files here include your README.md file, which should be an introduction for others using the app. We also have the Rakefile in the root. I didn't (and don't) use the Rakefile for much, but here you can load tasks to be executed in your command line. However, the actual writing of tasks should take place in lib/tasks.

## /app
This folder is the main attraction, and holds just about everything that makes our app, well, our app. There are typically sub-folders for models, views, and controllers, as well as assets such as stylesheets. Since most of our learning time to this point has focused on the mechanics of this folder, I'm going to assert that we have a good handle on /app and move forward.

## /bin
This was perhaps the most confusing folder to me. The [Rails scaffold generator](http://guides.rubyonrails.org/v3.2.9/getting_started.html) doesn't even include this folder, so why do we need it?

In short, this folder makes sure our code executes in the right environments. The individual files with a /bin folder are called ```binstubs```, and most Learn repositories include binstubs for bundle, rails, rake, spring, and yarn. You may recall having to run a command such as ```bundle install``` or ```rails s```. When doing so, you are telling the system to wrap your gems and code within the bundle or rails environment respectively.

## /config
Learn has also spent a good amount of time going over this folder. For example, our routes are all defined within ./config/routes.rb. This folder also contains the configuration settings for things like our databases and environments referenced above in ./bin.

For Tillio, the only file I added beyond Learn's default scaffolding was omniauth.rb which contains the builder for Google OmniAuth.

## /db
Again, I'm asserting we all have a pretty good handle on ./db from prior Learn lessons and labs, so I'm going to breeze over this. Just remember this is where all our migrations, seed data, and database schema live.

## /lib
Technically, this folder is for any extended modules used in an application. However, I have not found a practical application for this folder yet, nor have I seen this used in any Learn repos for anything other than .keep files.

## /public
This folder's name says it all--files here are seen by everyone, exactly the way they are. It can be used for static pages and compiled assets. While building Tillio, I only used this folder for my standard error pages, such as my 404.html.

## /spec
Hello, rspec! This folder is used for BDD (behavior-driven development) and houses the files and folders for feature and model test units rspec generates. BDD differs from TDD because it takes into consideration the end user behaviors. Though a lot of debate surrounds rspec vs test, rspec outnumbers test applications on Github 5:1, and is standard in entry-level job postings.

## /test
./test is the Rails-included folder for tests. It uses the Test::Unit framework that Rails employs for TDD (test-driven development). However, since I am a good Learn student and I'm most familiar with the ./spec folder, I stuck with the for the Tillio app.

## /vendor
Any and all third-party code goes right here!


