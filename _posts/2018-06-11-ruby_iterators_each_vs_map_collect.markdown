---
layout: post
title:      "Ruby Iterators: .each vs .map .collect"
date:       2018-06-11 22:12:17 +0000
permalink:  ruby_iterators_each_vs_map_collect
---


With all the different Ruby iterators out there, it is a little difficult to remember when to use each one.

### .each
The defining characteristic of .each is that it does not change your return value. Using .each will simply return the original array unless you assign your iterated values to another variable. For example, below, we are making user-friendly strings for each plant in our database:
```
plants=['roses', 'lemons', 'tomatoes']
def list_plants(plants)
   plants.each do |plant|
	 puts "Let's plant #{plant}!"
   end 
end

#=> returns ['roses', 'lemons', 'tomatoes']
#=> puts "Let's plant roses!", "Let's plant lemons!", "Let's plant tomatoes!"
```

An easy way to remember this is that .each is most useful for user interfaces and interactions, but not for further operations on data. There is a workaround in which you can tell .each to explicitly return your transformed data, but why go through the hassle when there's .map right around the corner?

### .map
This iterator is nearly a mirror-reverse version of .each. It will always return your transformed data. In fact, if you want it to just put out a phrase, you must tell it to do so specifically (but why, when there's .each?).

Let's take a look behind the hood:
```
plants=['roses', 'lemons', 'tomatoes']
def list_plants(plants)
   plants.map do |plant|
	 "Let's plant #{plant}!"
	end 
end

#=> returns ["Let's plant roses!", "Let's plant lemons!", "Let's plant tomatoes!"]
#=> puts (nothing)
```

Therefore, .map is great for when you want to access your new data further down the road, or if you want to continue with more transformations.

### .collect
GOTCHA! There is absolutely no difference between .map and .collect. You just pick whichever one your heart desires.

![](https://media.tenor.com/images/eebce8042632af14e346c2a0b48cfca2/tenor.gif)

### .select
This is a conditional iterator, meaning it only operates on the pieces of data you pass through that match a given condition. Let's just dive into an example:

```
plants=['roses', 'lemons', 'tomatoes']
def list_plants(plants)
  plants.select do |plant|
	plant.length > 6
  end 
end

#=> returns ["tomatoes"]
#=> puts (nothing)
```

See? Select only returned ```tomatoes``` because it was the only plant passed through the block with a length longer than 6 characters. This can be useful for quick filtering, but as you build more robust apps, you're likely to replace this with ActiveRecord querying. AR uses SQL to help find exactly the data you are looking for.

### WILDCARD: !  (or the bang operator)
Despite the fun name, the bang operator can be a little dangerous. Bang is a destructive method in which it changes the original array passed through the block, rather than just changing the return value. Let's check it out:

```
plants=['roses', 'lemons', 'tomatoes']
def list_plants(plants)
   plants.select! do |plant|
      plant.length > 6
   end 
end

#=> returns ["tomatoes"]
#=> plants = ["tomatoes"]
```

THE BANG DID US DIRTY. It totally erased roses and lemons from our garden, and that simply is not okay. I need my lemon water!

![](https://media.giphy.com/media/5DFIHEdYSyNSo/source.gif)

## The Big Picture
It's all about changing the return values! 9/10 in production, you'll want to change the return value for further use, so stick with .map or .collect. However, if your a UI dev, .each is probably your go-to. Most importantly, beware the bang.
