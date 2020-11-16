---
layout: post
title: "Book Stash - Building Microservices - The Evolutionary Architect (Chapter 2)"
date: 2020-11-15 12:00:00 +0530
categories: [microservices, building-microservices, sam-newman, book-notes]
---

> Book stash is a series wheren, I put out my chapter wise notes on books. The following are my notes from the book _Building Microservices - Chapter 2, The Evolutionary Architect_

# The Evolutionary Architect

- Microservices bring in a lot of choice and decisions to make:
  - How many different technologies to use?
  - Should we allow different teams to used different languages?
- The role of architect has changed over time

> You keep using that word. I don't think it means what you think it means.

# Table of Contents

1. [Inaccurate Comparisons](#inaccurate-comparisons)
2. [An Evolutionary Vision of the Architect](#an-evolutionary-vision-of-the-architect)
3. [A Principled Approach](#a-principled-approach)
4. [The Required Standard](#the-required-standard)
5. [Governance Through Code](#governance-through-code)
6. [Technical Debt](#technical-debt)
7. [Exception Handling](#exception-handling)
8. [Governance and Leading from the Center](#governance-and-leading-from-the-center)
9. [Building a Team](#building-a-team)

## Inaccurate Comparisons

- Architects have one of the most important job, to maintain a balance between the ideal technical vision and the ever changing user requirements
- Architect has a direct impact on the quality of the system built, working structure of their colleagues, and the ability to respond to change
- Our industry is nascent, just over 70 years since its advent
- We are in constant search of validation from other professions to explain what we do
- Our profession is neither comparable to the doctors not plumbers. We fit somewhere in between. Making it hard for us to define ourselves and for the society to understand what we do
- This is why we have borrowed terms like `engineers` and `architects`. When in the actual sense of the terms we are definitely not
- If a concrete structural building like a school collapses the `architect` would be held responsible, is liable to go to jail, and be part of criminal proceedings
- The fact is these professions need qualified professions in society. For someone to be termed as an architect, it requires a minimum of 7 years of study
- Our certifications seem merely like gimmicks and worthless in some sense when compared
- The need of justifying ourselves have led us to take up these names, thinking we could gain similar respect to the professionals who are titled with these. This turns out to be risky:
  - Implies that we know what we are doing, which in all honesty we do not
  - Like real architects our software is not constrained by the laws of physics. What we build is built to bend, adapt, and evolve with user requirements
- The term `architect` has done the most harm:
  - Actual architects: someone who draws out a detailed plan for others to interpret and take action on. Part artist, part engineer, responsible for overseeing the creation of a singular vision with occasional comments from the structural engineer
  - Software architects: Doing the above in our industry would be bad i.e. focusing on building the perfect system to fit in a use case without knowing the following unknowns:
    - Fundamentally unknown future
    - How hard it can be to implement. (Which the `actual architects` in some sense have the liberty of ignoring)
    - Whether or not all the pieces would fit in
    - Will it work
- Calling ourselves what we call ourselves would more likely be a disservice to society. Since we are stuck with this name, best we can do, redefine the terms in our context

## An Evolutionary Vision of the Architect

- Our requirements change more often that for the architects responsible to design and build buildings
- The tools we use are ever changing too and the change is more often
- Our systems can be defined as ever-changing once launched into production the journey just begins, the software has to evolve as how the product is being perceived by the end customers
- In our case the architects need to shift focus from building a perfect solution to the problem at hand to instead focusing on creating a `framework` wherein new systems can be built and can evolve
- `Erik Doernenburg's` analogy of software architects being similar to `town planners`:
  - Aim is to gather information and optimize the layout of the city
  - Instead of pointing out which building is to built where, is responsible for zoning out cities, like the `industrial zone`, `residential zone`, etc
  - Defining the restrictions of each of these zones
  - Focus is not heavily on how a particular zone is doing, but it is on how people and utilities move from one zone to another
  - Like a town planner the architect does his best to anticipate change, but accepts that this is not always possible
  - As our system is bound to change, over-specifying every last detail should be avoided
- City should be a good place for everyone, not just customer but developers and operations too

> Architects have a duty to ensure that the system is **habitable** for developers. _- Frank Bushmann_

- _Example_: If a sewage plant is trying to be build in the residential zone. The architects should be empowered enough to be able to cut it off
- In conclusion, architects should set directions in broader terms and get involved into specifics in exceptional cases only

### Zoning

- Zones are analogous to service boundaries (or) a group of service boundaries
- More necessary to be worried about what happens between zones rather than on what happens within
- _Example_: how services should inter communicate, if REST should be used, should each zone be give freedom to expose APIs differently like HTTP, RMI or protocol buffers
- How involved the architect gets into the whereabouts of these zones depends on the organizations structure
- Independence of choosing technologies is another such decisions. If given complete freedom, people moving in and out of teams becomes hard and so does hiring
- Netflix for example has chosen to use Cassandra as its persistence layer of choice even though it is not suitable in some cases. Argument to do so is that they have gained more value in building tooling and expertise on Cassandra than to have lesser expertise in multiple use-case fitting database options
- In conclusion, need to be worried about what happens between the boxes, and liberal in what happens inside

### The Coding Architect

- Extremely important for the architect to be able to empathize with the developers
- Interacting with the teams by contributing code. If the organization practices pair programming, it occasionally makes sense for the architect to be one of the member in the pair
- How often to do it, depends on the size of the team(s)
- It improves awareness and communications with the teams you are working with

## A Principled Approach

> Rules are for the obedience of fools and the guidance of wise men _- Douglas Badger_

- Microservices are all about trade-offs. Often which are or should be made by the architect
- Needs a set of principles and practices to follow when in doubt

### Strategic Goals

- A separate strategic goal is not needed to be defined for an architect - a role which is already daunting enough
- They generally defined at an organization level - stuff like `expanding into southeast asia` to explore newer markets (or) `moving to an in house logistics`
- Although tech is not directly involved, important to understand where the company is headed and to keep the tech aligned
- Most importantly not letting tech become a bottleneck when implementing business features
- Often involves being involved in non technical aspects of the organization to envision the tech aptly

### Principles

- These are rules which help you align yourself to what you are doing to achieve larger strategic goals
- _Example #1_ - Say the goal is to reduce time to market. A principle indicating that individual team will be responsible for their software and can ship the feature independently would help achieve this
- _Example #2_ - If the goal is to expand to different countries, the principle that could be defined is to having inbuilt support for i18n from the get go of a new feature and ensuring that every component should be independently deployable to promote data sovereignty
- A good example is Heroku's set of [12 Design principles](https://12factor.net/) that help in creating applications deployable on the Heroku platform
- Fewer than 10 is a good number of principles
- Some of these principles could actually be constraints. Its better to have both constraints and the principles in the same list, promotes constraints to be challenged across organization and gives a clarity of whether constraints are actually constraints

### Practices

- Well defined practical guidelines to ensure that the principles are being followed
- _Examples_: Using HTTP/REST for all communications, using ActiveMQ as the messaging queue of choice, services handled by teams to be independently deployed on different AWS accounts
- Often highlights the constraints in the organization
- Practices change more often than principles

### Combining Principles and Practices

- If defined at a team level okay to interchanges them but at an org level should be differentiated and well defined as multiple teams use multiple techs
- The practices for Java might be different that for that of microservices in GoLang, but the principles remain the same
- HTTP/REST for all communications as a practice, the merit is not actually in the tech itself but, to ensure standardization

### A Real-World Example

<p align="center">
    <img src="https://interview-daily-assets.s3-ap-southeast-1.amazonaws.com/blog/a-real-world-example-blog.png" alt="A Real-World Example" width="600" class="center"/>
</p>

## The Required Standard

- When practicing(making trade-offs) one of the key things which need to be actively thought about is how much variability to allow in the system
- Continuing the analogy of town-planners, we need to define what a good citizen of the town is. This definition might differ from town to town but the core remains same

> When thinking about the bigger picture, "it needs to be a cohesive system made up of many small parts with autonomous lifecycles but all coming together" - _Ben Christian (Netflix)_

- Basically, giving emphasis on autonomy without loosing sight of the bigger picture

### Logging and monitoring

- Individual service health is useful to have but will not be very helpful in troubleshooting and pinpointing the root cause in case of downtimes and outages
- Having a centralized monitoring solution helps
- Push based or pull based
  - Push based - Each individual service is responsible to send out general health metrics to a centralized location
  - Pull based - A polling system pulls data from individual nodes themselves
- _Example:_ Graphite, Nagios, New Relic (paid)
- The service level metric aggregator should be standardized and the monitoring system should be decoupled from it

### Interfaces

- Picking a small number of interface technologies helps in integrating a new consumer
- If you use rest, questions to answer-
  - How will versioning on endpoints be handled?
  - How pagination will be handled?
  - Will verbs be used or nouns?

### Architectural Safety

- Being able to handle potential downfall of downstream services
- Mandating that each downstream service gets its own connection pool and also if possible a circuit breaker
- When using a circuit breaker if it relies on status codes, being able to differentiate what a successful call is and what is not, say considering 2XX and 4XX as a successful call and 5XX as failures. It is important to be able to differentiate 4XX(in the example) and not confuse it with 5XX codes. If not the safety measures could fall apart
- Applies if a technology other than HTTP is being used too
- Basically, the ability to fail fast and track down issues is a highly desirable quality in a system

## Governance Through Code

- Agreeing on how things have to be done at a microservice level is good and important
- Convincing developers to follow it is hard
- Rule of thumb is to make doing things right easy

### Exemplar

- Idea is to have a real world service which is doing things right for people to refer to
- The point being that you can't go very far wrong if you refer from the existing good parts of your system

### Tailored Service Template

- Having a templated base structure for each project to build business logic upon, which provides things like metric collection, health-checks, etc. out of the box. Example using open source templates like Dropwizard, Karyon
- Enhance this template as per the org context like providing support for circuit breakers by baking in resilience4j, or integrating a metric reporting capability to push the metrics to a Graphite server, etc
- Evolving the template should not be the task of a dedicated team but, of the org. Following an internal open-sourced approach
- Maintaining versioning and not relying on a single version of this template, introduces tight coupling if done

## Technical Debt

- Situations where we knowingly agree to cut corners as a trade-off to ship some features faster
- Just like actual debt has an ongoing cost and needs to be paid off from time to time
- Again, depending on the org, the architects role of getting the tech debt paid is different
  - _Case #1:_ Highly involved and responsible for maintaining a log of these debts and reviewing them frequently
  - _Case #2:_ With some guidance letting the team itself decide how to pay back the debts accumulated
- In any case, the architect must have an overall picture of the tech debt across the org

## Exception Handling

- An exception is when we knowingly deviate from the standard principles and practices that are defined
- For example if we have a practice to use MySQL as the datastore of choice and there comes a scenario where in using Cassandra to handle querying at higher volumes of data makes sense, taking up Cassandra would be an exception
- If an exception continues for long it helps in updating and iterating our standard practices

\*\***Note**: Microservices as an architecture, is not just attractive as it focuses on autonomy, but it also helps in structuring the organization. Giving more freedom to developers to solve problems at hand. If placing a lot of restrictions on developers is what the org is looking for, then microservices is not the right option for them

## Governance and Leading from the center

- An architects responsibility(quite a lot):
  - Ensuring a set of principles that guides development
  - Ensuring that these principles match the strategy of the organization
  - Having working practices to promote these principles, all while not making the developers life miserable
  - Making sure that the colleagues they are working with are in line with their decisions
  - Spending time with individual teams
  - Occasionally getting involved in coding

## Building a Team

- As the main person responsible for the technical vision of the org., it becomes the architects responsibility to ensure a growth trajectory for people working
- Another advantage that microservices give is having multiple independent service life cycles, each person in the team could be given ownership of a set of services before they take up responsibility of building things from the ground up
- Great software comes from great people and focussing too much on the tech would lead to missing out on more than half of the actual picture
