---
layout: post
title:      "NerdBox, Share Your Setup and Display Your Gear"
date:       2019-03-04 21:08:43 +0000
permalink:  nerdbox_share_your_setup_and_display_your_gear
---

<img src="https://i.ibb.co/Vwn3RPK/Screen-Shot-2019-03-04-at-3-50-55-PM.png" alt="Screen-Shot-2019-03-04-at-3-50-55-PM" border="0">
## Display your Pc Setup and Gear
For my sinatra project I created an app which allows users to signup and create profiles for thier gear and pc setup.
I started off with a join table for my has many through realtionship(Hardware model), but later switched to a [polymorphic relationship](https://guides.rubyonrails.org/association_basics.html) since it would make things cleaner and less complex.

I used bootstrap for styling (Spolier: There isn't much... ) and layout.
I haven't gotten the time yet to deploy it on heroku since I would need to switch to a postgres db.
Here's a [youtube link](https://youtu.be/bkSbcTueqNE) to see it in action.

Below is the structure of my app. The functionality doesn't go past CRUD except users have slugs for thier username.
### User:
- Has many Resources
- Has many Hardwares  as hardwareable(polymorphic namspace) 
- Has one Setup

### Resource:
- Belongs to user

### Hardware
- Belongs to "hardwareable" (polymorphic association)

### Setup
- Belongs to user
- Has many hardwares

### Models
- User (Fields: UserName, Email, Password, PasswordDigest)
- Resource (Fields: Name, link, icon, rank, user_id)
- Hardware (Fields: Name, images, link, rank, hardwareable references)
- Setup (Fields: Name, images, specs, rank, user_id)

## Views
### User
- Login (Login and Signup)
- Index
- show (profile)
- edit
### Resource
- index
- New
- Show
- Edit
### Hardware
- index
- New
- Show
- Edit
### Setup
- Index
- New
- Show
- Edit


Untill Next TIme,
Heshie

