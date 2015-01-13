---
layout: page
title: Environments
permalink: /environments/
---

##Vagrant

Suitable for:

- Django/Python
- Rails/Ruby
- PHP
- HTML

Complexity:

- Hard but easy once you know how

**How work with Vagrant**

##Virtualenv

- Django/Python

You will need a virtual environment in which to run a Python/Django site.

###How to create a virtual environment

####Per machine

    #Install virtualenv on your local machine
    pip install https://github.com/pypa/virtualenv/tarball/1.9.X

####Per project

virtualenv creates a folder that has the name of the environment you specify below. It's best to keep envs with the projects so use a similar folder structure to the following:

     |project-name <-- navigate to this folder when you create your env
     |----project-repo
     |----project-env

    #Create wrapper for this project
    virtualenv project-env

####Everytime

    source project-env/bin/activate
    #prompt will change to prepend the environment name
    (project-env)$


##LAMP Stack

- PHP
- HTML

Complexity:

- Easy

**How work with LAMP stack**
