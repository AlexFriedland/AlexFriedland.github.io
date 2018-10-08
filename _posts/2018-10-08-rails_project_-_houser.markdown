---
layout: post
title:      "Rails Project - Houser"
date:       2018-10-08 15:57:32 +0000
permalink:  rails_project_-_houser
---

github.com/alexFriedland/houser


**Doing the DB Right:**  

The first major task for this was setting up the DB, which is more complicated than I've made before.  I found Rails-ERD gem which  spits out an image of your database associations. It's really handy and IMO necessary for working with databases.

After building the database I started to import the excel data with RubyXL gem and used it to instantiate objects (seeding).  This has been the most time consuming / painstaking process of this project.  It's worth mentioning at this point that I started this project before I got to some of the topics like nested routes, omniauth, authentication/authorization).  As I implemented those, I had to refactor the DB, and then refactor the calls in the seed file.  
What a pain!  Lesson learned, make sure what you have is what you want before writing a lot of code to import years worth of spaghetti excel tables that you'll have to fix later.


**Rake Tasks - ReSeed**

As I built out my database I realized very quickly that manually dropping and re-migrating my database and seed file was too time consuming.  Quick google reminded me that you can create custom rake tasks. Reseed combines rake db:drop; :create :migrate; and :seed.  It's awesome.  All credit to the Nithin Bekal blog for teaching me this.

 http://nithinbekal.com/posts/rake-db-reseed/
 
 You simply insert the following code into: lib/tasks/db.rake and run it from the console with `rake db:reseed`

```
namespace :db do
  desc 'Drop, create, migrate then seed the development database'
  task reseed: [ 'db:drop', 'db:create', 'db:migrate', 'db:seed' ] do
    puts 'Reseeding completed.'
  end
end
```


**Nested Routes`**

When I got to this part of building out rails apps, I got really worried about having to build deeply nested routes to reflect my model associations.  Luckily it's a Rails best practice to only nest one level deep, so that was a relief, but as it was, I had to re-do alot of work.  Everything from the seed file to the helper methods had to be tweaked.  



