---
layout: post
title:      "Building Wanderlist with Sinatra & ActiveRecord"
date:       2018-04-23 21:02:38 +0000
permalink:  building_wanderlist_with_sinatra_and_activerecord
---


Travel has always been a major interest and passion of mine, so when it came time to build a Sinatra app, it was my first idea. I wanted to create an application where users could browse destinations and build trips (planned, past, or dreamed) from the destinations. It is built with the MVC model, and allows users to manage all CRUD actions from their browsers.

***Overview of model associations here***

### Stumbling blocks:

1. When I was first trying to seed my database for testing, I was having an issue with ```rake db:seed``` recognizing the secure password functionalities I had enabled via [bcrypt](https://www.npmjs.com/package/bcrypt). I was getting the following error message: ```ActiveModel::MissingAttributeError: can't write unknown attribute 'password'```, even though I was using ```:password_digest``` in my table creation migration and ```has_secure_password``` in my model file.

After some fruitless Googling, I started to play around with different methods of assignment. In my first, error-prone attempt, I was using a mass assignment technique to take my seed's hash and assign attributes based on that hash's key-and-value pairs. My next idea was to simply use ```User.new(hash)``` to feed in the given attributes. This method worked without a hitch, and it resulted in cleaner code as well!
