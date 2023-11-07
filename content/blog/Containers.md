---
title: "Today I learned : Containers"
date: 2023-11-07T13:34:04+01:00
draft: false
---

Another day, and another buzzword to learn. As I am learning more and more about new concepts I find out that some topics I used to think are impossible to grasp - because of confusing they can be - are pretty simple (even fun sometimes) when you put you're mind to it and approach it the right way, Today's topic will be all about containers. First I thought this was just a funny comparaison that people used to explain how to deliver software, but turns out it's actually a thing : the same way a we ship goodies from a country to a country, we can ship software (the computer goodies) from a computer to another.

## So what are containers exactly ?

In other words, Containers are a method of packaging and running applications and their dependencies in a standalone, isolated environment. The ultimate solution for the "It works on my machine" issue.

And Unlike traditional virtual machines (VMs) that run an entire operating system, containers share the host OS kernel while providing a separate file system and environment for each application. This means that containers are incredibly lightweight and efficient, resulting in faster startup times and easy portability.

## Why Containers ?

1. **Portability**: Containers are designed to be consistent across different environments, such as development, testing, and production. This means that once you create a containerized application, you can confidently move it from one environment to another without worrying about compatibility issues : You create a containerized application, and it's ready to party wherever you take it, No problems.

2. **Isolation**: if one container decides to go crazy, the others won't be dragged into the chaos. Containers offer a high level of application isolation. Each container runs independently of the host system and other containers, ensuring that changes in one container won't affect others. This isolation leads to a more stable and secure environment.

3. **Resource Efficiency**: Containers use fewer resources compared to traditional VMs, making them highly efficient. They share the host OS kernel, which reduces overhead and allows you to run more containers on the same hardware, ultimately saving you more than lunch money. 

4. **Scalability**: Containers make scaling your applications feel like a breeze. They're like Lego blocks – you can stack them up or break them down as needed. 

5. **Fast Deployment**:  Containers start up almost instantly, which means faster deployment and updates. Developers can iterate on their applications more rapidly, reducing time-to-market and improving overall agility.

6. **Version Control**: Containers provide an effective way to manage application versions and dependencies. You can version your containers, making it easy to roll back to a previous version if a new release encounters issues.


## Conclusion

Containerisation is truly a mindset shifting concept, it can be applied to any field of life : the ultimate "divide to conquer" concept. it is reshaping the way I develop, deploy, and manage my software applications with the significant advantages it offers over traditional deployment methods.  So Whether you're a developer, system administrator, or part of an operations team, understanding and incorporating containers into your workflow can lead to more streamlined, efficient, and agile software development. So get on board captain, it's time ship some containers.

