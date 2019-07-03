---
layout: post
title:      "Rails Project: Drivenwork.com"
date:       2019-07-02 19:42:17 -0400
permalink:  rails_project_drivenwork_com
---


And it's finally (in)complete, my Rails Project.
[DrivenWork.com](http://drivenwork.com)

Driven Work as in itself means companies that are driven something else other then making money, something that solves a real world problem.

## The Objective
Create an app where users can submit companies with their Ceo and the problems or technology breakthroughts they solved or achieved.

> Example: “Tesla, Electric Cars, Solving Sustainable Energy.
          CEO: Elon Musk, Year Founded: 2007, Major Breakthroughs: Compelling electric vehicles for an affordable price.

## The App 
*Quite self explanatory...(Not yet)*

### Models: 
- Company 
	* Has_many **Problems**
	* Has_many **TechnologyBreakthroughs**
	* Belongs_to **User**
	* Belongs_to **CEO**
- CEO
	* Has_many **Companies**
	* Has_many **TechnologyBreakthroughs** through **Companies**
	* Has_many **Problems** through **Companies**
- Problem
	* Belongs_to **Company**
- TechnologyBreakthrough
	* Belongs_to **Company**
- User
	* Has_many **companies**
		
## Functionality 
	
* Users can signup with an email or github(Yes, there's an open vunerability for the rails github gem that's why I'm not taking social security numbers yet...
* Any user can add or edit posts
* Only an admin can delete posts,  currently anyone can signup as admin
* You can view all Companies,  Ceo's, Problems and Technology Breakthroughs through the main menu
* You can add a company or you can add a problem or a technology breakthrough to an existing company.

That's all there is, I know the layout and design is crap, I threw bootstrap on so It wouldn't look 90's but other then that it needs work, shoot me a msg if you find yourself lost...

Oh, and it took me 4 hours to [learn how to] deploy to AWS...

Thanks for looking,
***Heshie Brody***
	
	



