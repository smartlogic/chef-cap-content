## What we use

So far you've seen general discussion about infrastructure configuration
management and application deployment. But what is available to meet these
needs? It is time to introduce [Chef](http://www.opscode.com/chef/) and
[Capistrano](https://github.com/capistrano/capistrano).

### Chef

Chef provides robust infrastructure configuration management designed to scale
in both volume and complexity. It supports clear and precise control over
installed packages, user accounts, running services, and configuration files.

The cookbooks (a collection of Chef code providing some functionality) are
written in Ruby, which makes them very easy to figure out. The number and size
of cookbooks, as well as the dependencies between them can be overwhelming.

Chef also provides great control over the differences between servers in your
infrastructure, making it easy to set up a server as both web and database in
staging or development, but deploy a full multi-tier infrastructure in beta or
production.

TODO find a better way to say "very easy to figure out" understand? comprehend?
follow allong with?

### Capistrano

Capistrano has long been the gold standard in deploying Ruby on Rails
applications. It has a straight forward approach and performs well. The
configuration can start very simply and evolve with the dependencies of your
application.

Capistrano offers a simple set of required dependencies, and can be useful with
very little configuration.


### Why Both?

You could argue that everything could be done with one of these two tools. You
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
the application, but this is for convenience in this guide and is not how we
often do things, opting to put the Chef code in its own repository.

TODO find some place to explain why we use multiple repos for app code and chef
code
