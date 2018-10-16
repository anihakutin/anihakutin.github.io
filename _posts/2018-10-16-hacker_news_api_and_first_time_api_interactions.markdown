---
layout: post
title:      "Hacker News API and first time API interactions "
date:       2018-10-16 00:28:48 -0400
permalink:  hacker_news_api_and_first_time_api_interactions
---


> The secret of getting ahead is getting started.    - Mark Twain

![Getting Started... ](https://media.giphy.com/media/26ufhYjBs6C4Q5SJG/giphy.gif)

For my CLI gem project I went ahead and built a gem that can interact and pull data from Hacker News via it's API, and since the best way to get ahead is to get started my first commit was all about getting my structure and some dummy data displayed on the screen so I can get a feel of what I wanted my program to look like.

```
 def call
    list_news
    menu
    good_bye
  end

  def list_news #(args)
    puts "Teach Yourself to Echolocate: A beginner’s guide to navigating with sound \n
          link 'https://news.ycombinator.com/from?site=atlasobscura.com' \n
          337 point & 39 comments"
  end
..........

```



My next step was creating the scraper class and article class and build the menu.

The hacker news api is pretty straight forward and it returns a list of article id's for each section requested.

```
Example: https://hacker-news.firebaseio.com/v0/topstories.json?print=pretty

[ 9129911, 9129199, 9127761, 9128141, 9128264, 9127792, 9129248, 9127092, 9128367, ..., 9038733 ]
```

Then I wrote a simple loop to generate article hashes and return an array.

```
stories = [ ]
      # request each article via it's post id
      i = 0
      while i < count
      print "."
      # set URL
      story_url = "https://hacker-news.firebaseio.com/v0/item/" + "#{page_data[i]}.json"
      story_uri = URI(story_url)
      #get page data
      story_response = Net::HTTP.get(story_uri)
      # parse data
      story = JSON.parse(story_response)
      # article hash builder
      new_story = {:title => story["title"],
                  :type => story["type"],
                  :author => story["by"],
                  :time => story["time"],
                  :text => story["story"],
                  :url => story["url"]}
      # build article array
      stories << new_story
      i += 1
      end
      # return array with articles as hash
      print "\n"
      stories
    end
```

The rest was quite simple, all I needed to do was bulid search and sort methods and create a functioning menu which wasn't too hard.

![](https://media.giphy.com/media/9Jcw5pUQlgQLe5NonJ/giphy.gif)

It was an amazing experience and I really learned a lot. Every accomplishment by the human being reminds us that the core of desire of any human is to create.

So long,

Heshie 


