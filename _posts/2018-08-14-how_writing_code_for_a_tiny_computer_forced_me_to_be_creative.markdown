---
layout: post
title:      "Forced Creativity. Writing Code For Limited Hardware."
date:       2018-08-14 23:31:11 -0400
permalink:  how_writing_code_for_a_tiny_computer_forced_me_to_be_creative
---


I recently completed a *'2 day'* project for a summer camp in just *'3 weeks'*.... As with any code project, the anticipated time of project completion and the actual time it takes to complete can be quite far apart.

The client was a friend of my wife who runs a summer day camp in Brooklyn and wanted an exciting way for kids to win prizes and get rewarded via cards that were dealt for good behavior and class participation.

She wanted a big screen that'll play camp pictures and events and it should have a barcode scanner attached so the kids can scan their cards to see if they won a prize.

## How It All Started
It was a typical Sunday afternoon while I was out shopping with my wife and I overheard her speaking to her friend about this fancy screen with a barcode scanner that she wanted to put up for this summer contest and I was like sure, I'll have it done in 2 hours...

**LESSON LEARNED:**  *Never listen in on your wife's phone conversations.*

## What I used to build this project
![Running on chrome...](https://media.giphy.com/media/oNZqhiNC6jcQ2rtLWO/giphy.gif)

**Technologies**
* HTML
* CSS
* JS
* Jquery

**Hardware**
* Liva Mini PC ([picked it up on ebay for $45](https://www.ebay.com/itm/ECS-LIVA-Mini-PC-WIndows-8-1-Pro-2GB/253752439492))
* Standard PC Monitor
* USB Barcode Scanner ([$16 on amazon](https://www.amazon.com/gp/product/B00406YZGK/))

## How I built it
Like anyone else would, I started to build this project feeling all smug thinking that I'll just hack together a CSS slider with some code that accepts barcode inputs since barcodes are essentially keyboards with a laser reader and I'll be the coolest dude in town. But, [as expected], issues arose.

I chose HTML, CSS, and JS because those were the only technologies I knew at the time well enough to actually build something. The code is a *Mish-Mosh* of JS and Jquery. I can't look at that code today... : )

**LESSON LEARNED:**  *Being smug will make you overlook the obvious. Approach every project as your first*

## The road bumps
All Code is on my [github](https://github.com/anihakutin/LazySliderWithBarcodeScanner), feel free to use it as you please.
1.  As kids will always be kids and they love to click on things many times... I needed to implement a method that'll cancel out previous inputs every time a barcode is scanned. 

**The Solution:** Barcode scanners can be programmed to input any end of scan character to be used as a trigger to process the data inputted.

2. Since HTML and CSS are run in a sandbox on the browser without access to the local file system and I did not have the know how to set up a local server, I had to figure out a way to dynamically load images from a folder without previously knowing the names or the number of images.

**The Solution:** I hardcoded the image sources to the images folder in my root directory and I prompted the user on page load to input how many images they wanted to load and I instructed my friend to name the images by number sequentially and just paste them into the images folder so I can then run a loop and build the image links, *Voila!*

**Image link builder code:**

```
//firstRun
var firstRun = true;

// Get number of images
var numOfSlides = prompt("Please enter how many slide images are in the folder", "Example: 10...");

//Get slides
var slides = [];
var imgLinks = [];
var slideNumber = 1;

while(slideNumber <= numOfSlides){
slides.push('<img src="' + 'slides/' + slideNumber + '.jpg' +'" />');
imgLinks.push('slides/' + slideNumber + '.jpg');
slideNumber++;
}
```

3 . Now that I had the major parts out of the way I just copied a CSS Image slider from [Codepen](https://codepen.io/) and proceeded to integrate into my project. *And then it happened...*

## The crash
![](https://media.giphy.com/media/136YrAkcWsvpcI/giphy.gif)

Once all of it was done I proceeded to load it onto the liva mini pc and pat myself on the back for the quick turnaround but to my dismay, all that displayed was the first image and then it would hang and freeze up the entire computer.

Upon checking the task manager I realized that since I was preloading almost a 100 images for the slideshow it basically was overloading the little ram that was left and freezing up the entire computer.

**LESSON LEARNED:**  *Write code that can run on nothing and that'll allow it to run on everything*

## The rebuild
I did some research and found a concept called lazy loading which means that instead of loading all the images at once, build a method that loads just the images needed. 

**So in my case that was the following:**
1. Load the first image in the DOM
2. Load the upcoming slide image in the DOM
3. Transition from the current image to the next image with some fancy CSS
4. Remove the previous image

**My lazy slider code:**

```
//firstRun
var firstRun = true;

// Get number of images
var numOfSlides = prompt("Please enter how many slide images are in the folder", "Example: 10...");

//Get slides
var slides = [];
var imgLinks = [];
var slideNumber = 1;

while(slideNumber <= numOfSlides){
slides.push('<img src="' + 'slides/' + slideNumber + '.jpg' +'" />');
imgLinks.push('slides/' + slideNumber + '.jpg');
slideNumber++;
}

//Append 2 slide element 
var elem = document.getElementById("lazy");
elem.innerHTML += slides[0];
elem.innerHTML += slides[1];

//create timer/slider
var slider = setInterval(mySlider, 4000);
var slideP = 0;
function mySlider() {

if(slideP < numOfSlides) {
//get fist, last and previous slide element
var firstSlide = elem.firstElementChild;
var lastSlide = elem.lastElementChild;

//Load first image and animate
firstSlide.className = "fadeIn";
lastSlide.getAttributeNode("src").value = imgLinks[slideP];

//move to next slide
elem.insertBefore(lastSlide, firstSlide);

//remove image from previous slide, 2nd child
lastSlide.classList.remove("fadeIn");

slideP++;
} else{
    slideP = 0;
}
}
```

And it worked like a charm...! Not to mention that I stayed up all night building the "lazy-loader". The reason it took so long to build this tiny script was that I had never really learned to code from the ground up and I was missing a ton of fundamental concepts and just toyed with it until the console didn't return any errors : ).

Also until the project wasn't due to be delivered it never occurred to me to test it on the actual hardware. 
Until the night before...

I hope you enjoyed reading about this project!

*Best Regards,*

**Heshie**

