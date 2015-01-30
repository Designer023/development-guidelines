---
layout: page
title: CSS
permalink: /css/
---


##CSS writing style

There are a few ways of writing css. For consistency we will adopt only one naming convention. This is lowercase and hyphen separated. It is the most readable and fits well with other CSS methodologies that are covered below.

**Yes**

    .hyphen-separated {...}

**No**

    .camelCase {...}
    .underscore_separated {...}
    .alllowercase {...}
    .ALLUPPERCASE {...}

##Specificity

Keep your selectors short and with as low a specificity as possible. A maximum of three classes in your selectors is recommended. Why? Two reasons:

- Selectors with a high specificity can be time consuming to override
- long selectors can bloat your css. 

**Yes**

    .my-thing { … }
    .my-main-thing .my-thing { … }
    .my-main-thing .my-space .my-thing { … }

**No**

    .my-main-thing .my-sub-thing .my-space .my-thing { … }

Do not include one or mote #ID's in your selectors...EVER. [It’s too specific](http://cssguidelin.es/#ids-in-css). Use #ID with javascript ... but not styles.

So you like namespacing with #ID's? Cool...namespacing is good, just do it with a class instead.

**Yes**

    .my-thing { … }

**No**

    #my-thing { … }

!important is ok in a very small number of circumstances. One example is error messages which always display the same way - red and bold. We don’t have a !superimportant so if you have to use !important to override something else, then the something else is too specific to start with. Go back and reduce the specificity of the selector that you need to use !important to override.
Do not add more specificity, because it can make it hard for future development. 

It’s hard to override an !important for a reason and it’s meant to be used to make sure a rule works as it should. It’s not a fix for overriding something that is broken. 

**Yes**

    .hidden { display: none !important; }
    .error { color: red !important; }

**No**
    
    /* as a group of rules */
    .my-thing { color: red  }
    .my-thing { color: blue !important; }

Check the specificity of your CSS. It should be a flat line or a gentle incline from left to right with minimal spikes. Spikes should be towards the right/end.

- [http://csswizardry.com/2014/10/the-specificity-graph/](http://csswizardry.com/2014/10/the-specificity-graph/)
- [http://jonassebastianohlsson.com/specificity-graph/](http://jonassebastianohlsson.com/specificity-graph/)

##Commenting your code

- If you have to think about how to make work, provide a comment to share your thinking (and remind your future self)
- Did you find the answer to your problem in a web page? Include the URL to that page.
- If your file is longer than a screen length then provide comments to note the code so it can be navigated - split it into sections with comments. If it’s very long then think about adding an index.
- Comment frequently. Are you concerned that you have too many comments? Don't be - everyone likes good documentation.
- There’s nothing wrong with a bit of humour in a comment, but don’t make it offensive! People can read the CSS publicly.

##CSS methodologies

###FLAT

There is no overall structure to the css. This is ok on small sites/microsites. 


###BEM
[http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/)

A block consist of elements such as headers, search bars, primary navigation, widgets, list panels etc. Basically anything that can be a stand alone item. The block should be named something sensible and relevant but not a stupidly long name like .this-is-the-block-where-the-results-sit-in. Try something like .events-list assuming there is no other event list blocks. If there is then make it a little more specific so there is no name clash!

The elements within the block should all be prefixed with the block name followed by a double underscore and any html selectors are nested in the css if they are not explicitly named.

The block

    .block-name {...}
 
Specific items within the block

    .block-name__title {...}
    .block-name__more-info {...}

Generic items within the block are ok not to have a class on

    .block-name p {...}
    .block-name ul li {...}
    .block-name span {...}

Try to nest no more than 3 levels, preferably 2. For example, the following selector is too long:

    .block-name ul li a span {...}

Either:

- give the span a class e.g .block-name__some-class 
- drop the li a out of the selector.

Global styles

If there are any global styles that need to be used in several blocks, use a prefix of .global__. Using a close button as an example:

**Global item**

    .global__button-close

**Block item**

    .block-name__button-close

This might create a few more classes on things but it should keep them all unique and reduce the possibility of clashes as blocks get moves/updated over time etc.



###OOCSS
Object Orientated CSS [http://appendto.com/2014/04/oocss/](http://appendto.com/2014/04/oocss/)
If you've used Bootstrap, then you've used a OOCSS. 

##State names
 
    .is-active {...}
    .is-disabled {...}
    .has-error {...}

These are used only to define the state of an object. They should be prefixed with .is- or .has-. 

These should never be styled as a stand alone classes as is as they always are tied to an element or module. The state classes should be wrapped within the module or element:

**Yes**

    .my-module__item.is-active { display: block; }
    .btn.is-disabled { color: grey; }
    .form.has-error { border: 1px solid red; }
    .has-error .form { border: 1px solid red; }

**No**

    .is-active { display: block; }
    .is-disabled { color: grey; }
    .has-error { border: 1px solid red; }

##Utility classes

Utility classes are used for more global styling. Ideally they should be prefixed with .u- to denote what they are for, but since there are only a few it’s acceptable to have it without the .u-. 

**Yes, and preferred**

    .u-right { … }
    .u-left { … }
    .u-clearfix { … }

**Yeah, ok too**

    .right { … }
    .left { … }
    .clearfix { … }

###Javascript hooks

These should NEVER BE USED FOR STYLES. You can apply styles to a class that is added via javascript, but anything that is for js to hook onto MUST NOT HAVE STYLES RELATED TO THE CLASS.

    <span class='js-menu-toggle'>Menu</span>
    <ul class='js-menu-target is-active'>...I’m a menu</ul>

The javascript should add/remove the .is-active class and that should be styled. The .js-menu-target is only for the javascript.
