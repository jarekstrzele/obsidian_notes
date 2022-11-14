[[0-AWS w3school INTRO]]
[[AWS EC2]]

# AWS EC2 Scaling

Scaling is about only using the resources that you need.

Make sure to have an architecture that can handle changes in demand,

## auto scaling
Servers can get more requests than they can handle.
but
Too many requests can cause timeouts and outages.


AWS EC2 can automatically add or remove EC2 instances.

#### Two approaches:
- dynamic scaling: responds to changing demand
- predicative scaling: schedules the number of instances based on a predicted demand
- dynamic and predictive scaling can be combined to scale faster

EC2 Auto Scaling can be added as a buffer on top of your instances.
It can add new instances to the application when necessary and terminate them when no longer needed.

You can set up a group of instances.

__minimum capacity__ you cant set a minimum capacity of instances that will always be running. (__maximum capacity)





