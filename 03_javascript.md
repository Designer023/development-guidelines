---
layout: page
title: Javascript
permalink: /javascript/
---

#Where to put the javascript?

Unless it's essential for it to be in the head of the HTML document, place all javascriptvjust before the closing body tag of a page.

##What's essential for the head?

That can vary from project to project but a rule of thumb would be:

- Modernizr
- a minimal amount of inlined javascript 

##What should do in the footer

- jQuery. Nothing essential should be using jQuery.
- Everything else like galleries and slider js, social js etc.
- Analytics. I know it says put it in the head, but a quicker page is a happier user and a more accurate stat. A quicker stat is a slower site and unhappy user (who might then leave).

#How many js files should there be.

For a normal site there should be 2 js files that are loaded for the whole site. The header.js and the footer.js. That's it! Call them what you like! There may be more specific files that are loaded for certain pages or sections of a site.

##header.js

Contains the header javascript that contains things like Modernizr. This can be created by concatenating (joining together) lots of smaller js files.

##footer.js

Contains everything else that is global js. Concatenated from other js files like jQuery/Zepto and other plugins and libraries. They should be conactenated in a logical order, starting with the biggest libraries, then plugins and then the callbacks to activate the plugins.

#Writing style

##Variables

Things that can change once the code is running e.g. counters. These should be lowercase with underscores.

    var variable_things = 123;

##Constants

Are variables too but they are ones that stay the same e.g. A DOM element that won't change.

   var CONSTANT_THING = 'I never change! I am a rock.';

If you find yourself doing something late in your code like `CONSTANT_THING = 'Something else';` then it's not a constant and should be refactored to lowercase.

##Line endings

Should finish with a semi-colon. Older browsers will fall over if you don't do this. These are not really required by modern browsers, but make things clearer and let's do it right anyway. The browser engine should not have to assume. 

    var me = 'Carl';
    var you = 'Not Carl (Probably)';


#Writing efficient code

If you have to write something more than once it should be a variable or a function. This makes your code clear and maintainable. 

##Variables

###No

     $('.thing').on('click' function() { ... });
     $('.thing').on('tap' function() { ... });
     $('.thing').on('swipe' function() { ... });

###Yes
    
     var THING = $('.thing');
     THING.on('click' function() { ... });
     THING.on('tap' function() { ... });
     THING.on('swipe' function() { ... });

The second example looks more code, but imagine that this both examples are spread over a massive plugin you just wrote. Now I know this **never happens** but what if you happen to change the class of `.thing` to `.other-thing`. Reduce the possibility of missing one instance of your variable, and of making a typo. You're lining yourself up for bugs and broken plugin. Choose the option that is easier to maintain.

##Functions

###No

     $('.next').on('click', function(e) {
        current_slide++;
        if (current_slide > MAX_SLIDES) {
            current_slide = 1;
        }
        //Logic to update slides...
        e.preventDefault(); //stops default action of clicking things.
     });
     
     $('.next').on('swipe-right', function(e) {
        current_slide++;
        if (current_slide > MAX_SLIDES) {
            current_slide = 1;
        }
        //Same logic to update slides...
        e.preventDefault(); //stops default action of clicking things.
     });
     
     $('.index').on('click', function(e) {
        current_slide++;
        if (current_slide > MAX_SLIDES) {
            current_slide = 1;
        }
        //Same logic to update slides...
        e.preventDefault(); //stops default action of clicking things.
     });
   

###Yes
    
     //The slide update functionallity is in only one place
    function update_slides() {
      //Logic to update slides...
      
      //Logic to update index can be in the same place to keep it neat or it can reference it's own unique function too!
    }
    
    
    //The handling of slide navigation is broken down into unique functions.
    //These can now be called by timers, navigation clicks on arrows or indices or anything else.
    
    function next_slide() {
      current_slide++;
      if (current_slide > MAX_SLIDES) {
        current_slide = 1;
      }
      update_slides();
    }
    
    function prev_slide() {
      current_slide--;
      if (current_slide < 1) {
        current_slide = MAX_SLIDES;
      }
      update_slides();
    }
    
    function goto_slide(slide_num) {
      //Constrain the slide within the range available.
      if (current_slide < 1) {
        current_slide = MAX_SLIDES;
      } else if (current_slide > MAX_SLIDES) {
        current_slide = 1;
      }
      update_slides();
     }
     
     //Rest of the app
     $('.next').on('click', function(e) {
        //now we can just call that function when needed. It does the rest! 
        next_slide();
        e.preventDefault(); //stops default action of clicking things.
     });
     
     ...


#How to write a javascript class

A class is a code template for creating objects that provides initial values and functions and can be extended to create new classes. There is more than one way to make a class in javascript. Best stick to one, as follows. Note the CamelCase Style for the class name.
    
    /* @class Playlist */
    //
    function Playlist(name, tracks) {
      this.name = name || 'my playlist';
      this.tracks = tracks || [];
    }

    //By using prototype we don't have to duplicate core object functions
    //requests for functions and properties are passed up the protostupe chain
    //meaning less duplication of code
    Playlist.prototype = {};
    
    //Add functionallity with functions for the class
    Playlist.prototype.addTrack = function(track) {
      this.tracks.push(track);
    };

    Playlist.prototype.getTrackList = function(format) {
       if (typeof format !== 'undefined' ) {
          return this.tracks.join(format);
        } else {
          return this.tracks;
        }
    };

    /* End @class MyClassName */
    

    //Now we have the class we can use it
    //make a new Playlist object using the Playlist class
    var my_playlist = new Playlist('Such Wow', 99);
    //add a track to the list
    my_playlist.addTrack(1234567890);
    //print the tracklist to the console
    console.log( my_playlist.getTrackList() );


[Read more about prototypes](http://sporto.github.io/blog/2013/02/22/a-plain-english-guide-to-javascript-prototypes/) and why they are useful and get your head around the concept.

#Validating code

To make sure your code is nice, use a validator. jshint.com is usually good enough, but if you want a challenge go with jslint.com

- [http://jshint.com/](http://jshint.com/) - Shows bad code but not bad formatting.
- [http://www.jslint.com/](http://www.jslint.com/) - A bit more picky. Spaces and indents are a fail!
