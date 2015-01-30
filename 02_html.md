---
layout: page
title: HTML
permalink: /html/
---

##HTML

###Syntax

HTML that is indented is readable HTML. You can use either tabs or spaces to indent - be consistent with what you use in your markup.

**Yes**

    <div class="form">
      <div class="form__item">
        <p>
          <span></span>
        </p>
      </div>
    </div>

**No**

    <div class="form">
    
    <div class="form__item">
    <p>
    
        <span></span>
        </p>
    </div>
    </div>

###Commenting code
Use comments to:
- add notes for your future self and other people working on your code to say why you used the code you did
- indicate the start and end of HTML blocks - especially useful in HTML emails.
- keep comments professional - they will end up on the internet.

###Things to do
Prefix comments with TODO if the comment is a record of things that you want to work on.

###DOCTYPE
Use HTML5 for all work 
[Introduction to HTML5](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/HTML5/Introduction_to_HTML5)

You might work on projects that are using a different DOCTYPE, so check first.

###Validation of code
If you choose to validate your code, you can do so using the [W3C Validator](http://validator.w3.org/).
If your HTML is not working as you were expecting it to, check for invalid markup by using the W3C validator.

New browsers will attempt to fix unclosed tags, but they might not fix it correctly. Aim for valid HTML and remember to close tags properly.
