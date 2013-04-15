## Goals

There are a few primary goals behind the approach we'll cover for server 
provisioning and application deployment. By combining server configuration 
management and automated application deployment, anyone on your team can be 
empowered to perform the tasks of server setup, maintenance, etc.

### Build a machine quickly and repeatedly

Using a configuration management system for your servers will allow you to 
capture the knowledge of application dependencies and standard server setup 
procedures so they are common across the team. It allows for simple setup of new 
hardware, both physical and virtual. Server configuration management can also be 
extended into continuous integration or development environments to help with 
application isolation. This approach provides a consistent baseline setup for 
both developers and testing.

### Add components easily and seamlessly

Once a server is configured and put in service, maintenance becomes crucially 
important. Having an idempotent system for applying updates and changes is 
extremely useful. It is important to be able to add a component or update an 
existing component while leaving as much as possible of the rest of the server 
untouched.

### Deploy and update code seamless

Finally, the ability to apply patches and updates to the running application 
code is necessary. The system needs to be able to minimize (or ideally 
eliminate) downtime while updates are being applied.
