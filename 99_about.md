---
layout: page
title: About
permalink: /about/
---


##How to update this guide

The documentation is written in Markdown and the site uses Jekyll to complie the static site. You can edit the pages directly in Github and it will recomplie and update them, or you can clone the repo and push. If you clone the repo you will need to have Jekyll installed on your system. **To make a change to this site you will need access**.

###What should I update on this documentation

- Typos
- Missing & broken links
- Missing info

**DO NOT ADD ANY SENSITIVE INFORMATION** This includes internal wed addresses, usernames or passwords. Remember that if you do it will remain in the git history even if you then update it later.

### How do I get access?
Ask me! Or make a change in your own branch and submit a pull request and I'll review it.

###How do I update this using Github

Simply click on the edit icon while viewing any of the pages. Once you have made your edits commit and the site will update on it's own after a short while (~5 mins).

###How to make your changes on your local machine
    
Clone the Repo. 
    
    git clone http://this-repo-url
    
Create a new branch from `gh-pages`. This is the master branch for this repo.
    
    git checkout -b my-new-branch
    //or
    git branch my-new-branch
    git checkout my-new-branch
    
Make your changes and commit them.
    
    git commit -am 'updated the docs specific text here'

Merge the updated `gh-pages` branch with yours and then if there are no conflicts merge yours with `gh-pages`   

    git checkout gh-pages
    git pull
    git checkout my-new-branch
    git merge gh-pages
    
Now your branch is upto date with `gh-pages` and you can merge and push your changes.
    
    git checkout gh-pages
    git merge my-new-branch
    git push

Github will complile and update the site files and the site will update.


###What is Markdown

It's an easy way to write documentation. Who needs crazy tags when you can write in plain text. 

- [http://www.markdownviewer.com/](http://www.markdownviewer.com/)
