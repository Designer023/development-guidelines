---
layout: page
title: Javascript
permalink: /javascript/
---

#Where to put the javascript?

Unless it's essential for it to be in the head of the HTML document it should be placed just before the closing body tag of a page.

##What's essential for the head?

That can vary from project to project but a rule of thumb would be:

- Modernizr
- a minimal amount of inlined javascript 

##What should do in the footer

- jQuery. Nothing essential should be using jQuery.
- Everything else like galleries and slider js, social js etc.

#How many js files should there be.

For a normal site there should be 2 js files that are loaded for the whole site. There may be more specific files that are loaded for certain pages or sections of a site.

##header.js

Contains the header javascript that contains things like Modernizr. This can be created by concatonating (joining together) lots of smaller js.

##footer.js

Contains everything else that is global js. Concatonated from other js files like jQuery/Zepto and other plugins and libraries. They should be conactonated in  a logical order staring with the biggest libraries, then plugins and then the callbacks to activate the plugins.


#Writing style

##Variables

Things that can change once the code is running e.g. counters. These should be lowercase with underscores.

    var variable_things = 123;

##Constants

Are variables to but they are ones that stay the same e.g. A DOM element that won't change.

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

The second example looks more code, but imagine that this both examples are spread over a massive plugin you just wrote. Now I know this **never happens** but what if you happen to change the class of `.thing` to `.other-thing`. Just thing of the chance of missing one, or a typo or anything else. Hello bugs and broken plugin. Now what is easier to maintain?

##Functions

###No

     $('.next').on('click', function(e) {
        current_slide++;
        if (current_slide > MAX_SLIDES) {
            current_slide = 1;
        }
        next_slide();
        e.preventDefault(); //stops default action of clicking things.
     });
     
     $('.next').on('swipe-right', function(e) {
        current_slide++;
        if (current_slide > MAX_SLIDES) {
            current_slide = 1;
        }
        next_slide();
        e.preventDefault(); //stops default action of clicking things.
     });
     
     $('.index').on('click', function(e) {
        current_slide++;
        if (current_slide > MAX_SLIDES) {
            current_slide = 1;
        }
        next_slide();
        e.preventDefault(); //stops default action of clicking things.
     });
   

###Yes
    
     //The slide update functionallity is in only one place
    function update_slides() {
      //Logic to update slides...
      
      //Logic to update index can be in the same place to keep it neat or it can reference it's own unique function too!
    }
    
    
    //The handinling of slide navigation is broken down into unique functions.
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

