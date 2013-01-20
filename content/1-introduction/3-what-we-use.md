# What we use

So far you've seen general discussion about infrastructure configuration 
management and application deployment. But what is available to meet these 
needs? It is time to introduce [Chef](http://www.opscode.com/chef/) and 
[Capistrano](https://github.com/capistrano/capistrano).

## Chef

Chef provides robust infrastructure configuration management designed to scale 
in both volume and complexity. 

TODO expand

## Capistrano

TODO expand

## Why Both?

You could argue that everything could be done in one of these two tools. You 
wouldn't be wrong or misled in your argument. but this what we’ve settled on 
uses each for what it is best at.

The way SmartLogic has it set up:

1.  Chef for infrastructure
1.  Capistrano for apps

The result is that you could use a single Chef setup designed for an application 
on all servers supporting multiple components for the single product.

The other motivation is that with this approach, Chef changes are infrequent and 
are often isolated to their own provisioning repository, Capistrano changes are 
more frequent as the application changes or evolves and are stored right 
alongside the application code.

Note: In the example repository for this guide, the Chef code is right alongside 
the application, but this is for convenience and is not how we often do things.
