---
layout: post
title:      "ShipMatix - My First SaaS App, Submitting My Final Project,  Part 1."
date:       2020-01-30 01:40:12 +0000
permalink:  shipmatix_-_my_first_saas_app_submitting_my_final_project_part_1
---


## Reflection
![](https://media.giphy.com/media/BDagLpxFIm3SM/source.gif)

I can't believe that after this long and exciting journey to code I am finally here, submitting my final project.
Looking back it's truly unbelievable where I've arrived, the lessons, long nights of frustration and achievements.
What a journey this has been!

## The Project
A friend of mine approached me a while back with a problem he was having at work. He runs an ecommerce business and uses shipstation to process orders and print shipping labels. It takes around 3-4 hours every day for his employee to process the orders and print shipping labels.
What we came up with is ShipMatix. [Matix - automatic]
Basically what ShipMatix will do is download orders from shipstation and automatically select the cheapest shipping level according to a set of predefined rules.
I figured that I can kill 2 birds with one stone by building the app for my Flatiron School final project.

## The Technology Stack
I tried to keep it fairly simple and not have too many external dependencies, after some research I decided on the following stack:

#### Backend API

* [Rails](https://rubyonrails.org/) as a web framework
* [Postgres](https://www.postgresql.org/) as the DB, mainly because ActiveRecord supports [JSONB](https://blog.codeship.com/unleash-the-power-of-storing-json-in-postgres/) out of the box
* [JWT](https://www.sitepoint.com/introduction-to-using-jwt-in-rails/) for authentication
* [Faraday](https://github.com/lostisland/faraday) for API requests
* [Sidekiq](https://medium.com/@josh_works/sidekiq-and-background-jobs-for-beginners-89c95fef786f) to run long background jobs(Processing orders)

#### Frontend Framework
* [React](https://reactjs.org) as the framework
* [Redux](https://react-redux.js.org) for managing state
* [Grommet](https://v2.grommet.io) React component library for layout and style

## The Challenges, Road Map And Part 2
In order for my tool to be complete it would need to do the following:
* Allow users to sign up for an account
* Allow the user to connect their shipping platform(starting with ShipStation) to the app
* Allow the user to set rules how the service should select and purchase shipping
* Allow the user to view processed orders and shipping purchased for that order
* Allow the user to print purchased shipping labels from a queue or schedule auto print

My plan was to start building the app starting with the items needed to fulfill my flatiron school project requirement and then finish the app once I graduate.
 
So... 
I completed the project part but not the working part which actually makes the app useful.
Currently users can signup and set shipping rules but nothing more.  'Part 2' here we go!

## The Road Ahead
The road ahead is still unknown but I can't wait to see what it'll bring.
Once the app is complete I will try to find more people that it can help.
I am really excited to where this can go and lessons it'll teach me, *my first SAAS app bring it on!*

*So Long,*

Heshie
