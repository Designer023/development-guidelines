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
