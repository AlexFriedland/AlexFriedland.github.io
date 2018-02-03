---
layout: post
title:      "the joy of join tables"
date:       2018-02-03 22:00:15 +0000
permalink:  the_joy_of_join_tables
---


So I created a program to manage dogwalking companies. When I was coding out the models, I created a has_many / belongs_to (also known as many-to-many) relationship.  Explicitly, dogs have_many :walks, and walks have_many :dogs.

When I realized that I should have used a join table, initially I figured that since my models worked, it's fine.

Wrong.

Here's the code I started with:


```
class Dog < ActiveRecord::Base
  belongs_to :user

  has_many :walks
  belongs_to :walk
end
```


The problem is, if we need to extend this relationship later ( for instance, like adding a DogWalker), we'll have to refactor a whole lot more than if we simply make an intermediary join table and handle our associations in there.  With just a little work now we can save ourselves a lot later.

To that end, I changed my Walk and Dog models:


```
class Dog < ActiveRecord::Base
  belongs_to :user

  has_many :dog_walks
  has_many :walks, through: :dog_walks
end

class Walk < ActiveRecord::Base
  belongs_to :user
	
	has_many :dog_walks
  has_many :dogs, through: :dog_walks
end
```


The :dog_walks table needs to be migrated into the database, and the model is instantiated with the belongs_to :dog and :walk.

And that's it.  Now, our Dog has Walks and vice versa through the third association, DogWalks.
