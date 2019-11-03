---
layout: post
title:      "ERB To JS on a Rails API - jQuery Free"
date:       2019-11-03 05:39:49 +0000
permalink:  erb_to_js_on_a_rails_api_-_jquery_free
---

The Rails JS project really was something I looked forward to because it gave me the opportunity to finally pull all that I know together and build on what iv'e learned in the past year.

## The project and my jQuery diet
The project goals were straight forward, take your Rails app and instead of rendering ERB in the views have them return JSON, create JS objects from the returned json and then use those to build out your page.

When I was first introduced to the world of JS lot's of it was all about learning jQuery and it's methods, but once JS matured and many new features and API's were introduced like js classes and the fetch api It didn't feel like jQuery was so much better and cleaner anymore, therefore I decided that a jQuery diet it is.


## The process and why Rails is so great as an API
My rails app I built for my original rails project was called driven work and It was based around the idea of listing companies and ceos for their accomplishments and innovations.

Since my app was built in a typical rails fashion of MVC I knew I needed to do the following to convert it to a JSON api:
1. Create serializers to return the appropriate data required for my JSON responses.
2. Modify my controllers to handle and return the requested format/serialization.
3. Create JS classes to represent the model objects returned via JSON with class methods to return html objects.
4. Handle the JSON responses and use my JS classes to build out my page and display the response.

Rails makes it really easy to build api's with the following two features:
* **Serialization:** It allows you to create serializers(a file named with you model object name) that will return the only model attributes specified in those files in the specified format when you call render in your controller.

![My User Serializer](https://i.ibb.co/tCMvNhN/Screen-Shot-2019-11-03-at-12-56-30-AM.png)

* **Render JSON:** Render is a rails method which allows you to specify the return format according the the user's request using a single route and controller method. So for instance if the browser requests the */companies* page it'll return an html page but if the request specifies a type it'll return that type specified as long as you build out the method to support that. Aha, The simplicity of it all!

![My companies controller](https://i.ibb.co/P42Xf0S/Screen-Shot-2019-11-03-at-1-04-51-AM.png)

### *And that's really all it takes to get a rails app API up and ready.*
<br>
## Rendering your JSON with Java Script
Rendering the response was quite simple. The javascript fetch method makes it really simple to make requests and handle responses and is as elegant and simple as the jQuery method if not more intuitive. Once I got my response I use that to build JS objects and then called its class method I built to return html list objects and append it to the list on the page.

The class:
```
class Company {
  constructor(id, name, description, authorId,  authorName, numOfBreakthroughs) {
    this.id = id;
    this.name = name;
    this.description = description;
    this.authorId = authorId;
    this.authorName = authorName;
    this.numOfBreakthroughs = numOfBreakthroughs;
  }

  indexPageListItem () {
    let html = "";

     html += `<li> <a href=/companies/${this.id}>${this.name} - Major Breakthroughs: ${this.numOfBreakthroughs}</a></li>`
     if (this.authorId !== null) {
      html += `<p>by <a href=/users/${this.authorId}>${this.authorName}</a></p>`
     } else {
       html += "<p>by N/A</p>"
     }
    return html;
  }

  showPageListItem () {
    return `<li> <a href=/companies/${this.id}>${this.name}</a></li>`
  }
}
```

The page:
```
<h1>Companies</h1>
<p><%= display_errors(@companies) %></p>
<ol id="companies">

</ol>

<script type="text/javascript">
  document.addEventListener('DOMContentLoaded', () => {
    fetch('/companies.json')
    .then(response => response.json())
    .then(json => updateList(json));

    let updateList = (json) => {
      const list = document.getElementById("companies");

      json.forEach( company => {
        const companyObj = new Company(company.id, company.name, company.description, (company.user == null ? null : company.user.id), ((company.user == null ? null : company.user.name)), company.numOfBreakthroughs);
        list.innerHTML += (companyObj.indexPageListItem());
      });
    }
  })
</script>
```

## Posting forms with JSON and JS
It's 1:27am and i'm fighting to stay awake so I guess I'll leave the posting forms with JSON with JS for another time.
Checkout all the code here: [driven-work with JS repo on Github](https://github.com/anihakutin/driven-work-js)

*So Long,*<br>
**Heshie**
