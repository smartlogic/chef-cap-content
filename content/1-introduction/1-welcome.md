# _Deploying Rails Applications with Chef and Capistrano_

# Introduction

## Welcome

### Hello World

This guide is one path towards automatic, managed, and repeatable server setup 
and application deployment for Rails applications with Chef and Capistrano. It 
is based on how deploying Ruby on Rails applications works at [SmartLogic 
Solutions](http://smartlogicsolutions.com/).
There are many other approaches, and it is best to find and tailor one that 
works for you. Hopefully this can be a solid starting place for you.

There is a companion GitHub repository 
[https://github.com/smartlogic/chef-cap](https://github.com/smartlogic/chef-cap).  
This guide will walk through the various aspects of the repository and how it is 
used to provision a server and deploy a basic Ruby on Rails application.

### Who is this for?

This is intended for anyone who wants to learn more about provisioning and 
deploying web based applications.

- You might want to learn about deploying Rails applications and know nothing 
  about Chef or Capistrano.
- You might want to learn about Chef or Capistrano and know nothing about Rails 
  applications.
- Maybe you are an expert in all of those things but are curious about how 
  others use them all together.
  
If you are curious about any of these things, this guide could be for you.

### What should you know?

To walk through the steps and understand the workflow, you won't need much 
specific knowledge. However, in order to get the most out of the example code, 
you'll need a basic understanding of [Ruby](http://www.ruby-lang.org/en/). A 
background in configuration of [Nginx](http://wiki.nginx.org/Main) or other 
server components is optional.

### System requirements

For the code examples to run on your machine you will need:

1.  The examples assume a *nix terminal. Windows might work, but you are on your 
own.
1.  [Ruby](http://www.ruby-lang.org/en/) >= 1.9.3 suggested
1.  The ability to install additional gems
1.  [Bundler](http://gembundler.com/)
1.  [VirtualBox](https://www.virtualbox.org/)
1.  [Vagrant](http://www.vagrantup.com/)
