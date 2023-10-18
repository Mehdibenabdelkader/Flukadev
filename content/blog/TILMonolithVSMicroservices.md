---
title: "Today I Learned : Monolith vs Microservices"
date: 2023-10-18T17:33:30+01:00
draft: false
---

> "There are only two ways to lead: you either divide and conquer, or you build and unite."

This concept of dividing to conquer was a staple in the course of my academic life, I found it very intresting how such an idea can be applied to multiple fields of study, even in life problems.
And on my journey towards becoming a better devops enginner, I learned that this concept is the base of a whole architecture, and the difference between monolithic applications and microservices. What I discovered not only clarified the distinction but also highlighted the importance of working in small, manageable chunks.

## The Monolith: An elephant in the Room

First, let's talk about the monolithic architecture. IT'S LITERALLY A GIANT, all-encompassing piece of software that contains all its components tightly integrated. Everything, from the user interface to the database, is bundled into one massive unit. While this may seem convenient initially, it can lead to several challenges.

One of the most significant issues with monoliths is scalability. As your application grows, you might need to scale the entire blob of software, even if only one specific component requires additional resources (this process takes up to 6 months in big companies). This leads to inefficiency, increased costs, and potential performance bottlenecks.

Additionally, imagine having a pet elephant, maintaining monolithic code can be an overwhelming task. Every change made to a monolith can have unintended consequences throughout the entire system. The risk of breaking something elsewhere in the application looms over every developer's head. Furthermore, onboarding new team members can be a daunting process due to the complex nature of monolithic codebase, which gave birth to all the junior-senior programmers memes we see today.

## The Rise of Microservices: Working in Small Chunks

On the other side of the architectural spectrum, we have microservices. Microservices break down an application into smaller, individual services that can be developed, deployed, and scaled independently. Each service focuses on a specific business functionality, resulting in a modular and more agile architecture.

What's amazing about microservices is the ability to scale only the components that require it, avoiding the over-scaling issue that plagues monoliths. This efficiency can translate to cost savings and better performance. and knowing that services are independent, they can be developed and maintained by small, dedicated teams, simplifying the onboarding process for new developers.

I realized that microservices promote a mindset of working in small, manageable chunks. This approach has far-reaching benefits beyond just architecture:

### 1. **Flexibility**:
Microservices allow you to pivot swiftly when market demands change or new features need to be implemented. You can iterate on specific services without affecting the entire application.

### 2. **Robustness**:
Failure in one microservice doesn't necessarily mean a system-wide outage. The isolation of services helps to contain issues and maintain system availability.

### 3. **Scalability**: 
Scaling only the components under load is a more cost-effective approach than scaling an entire monolith. Microservices make efficient use of resources.

### 4. **Team Empowerment**: 
Smaller teams can take ownership of specific services, leading to faster development and more focused expertise.

### 5. **Continuous Deployment**: 
Microservices can be deployed independently, enabling more frequent releases and faster response to customer needs, and with the power of automation, the deployement of new pieces of software becomes a piece of cake for both the dev and operation teams.

### Embracing the Power of Small Chunks

In conclusion, my exploration into the world of devops taught me the importance of working in small, manageable chunks. While monolithic architectures have their place, microservices offer an attractive alternative for projects that demand agility, scalability, and maintainability.

By breaking down applications into smaller pieces, we can unlock the potential for more efficient development, deployment, and maintenance. and knowing that devops is more than just tools and theory, but rather a culture; adopting this architecture facilitates how teams collaborate, how projects evolve, and how organizations adapt to changing market dynamics.

This new perspective goes beyond just software development, it's a way to live ! So, on your own journey to greatness, remember the lesson I learned today – Divide to conquer, think small, think microservices.