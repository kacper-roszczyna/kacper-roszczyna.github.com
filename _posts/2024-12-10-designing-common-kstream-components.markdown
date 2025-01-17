---
layout: single
title:  "Designing Common Kafka Streams Components"
date:   2024-12-10 15:54:59 +0100
categories: jekyll update
---
DRY. Do not Repeat Yourself - it's possibly one of the first things taught to fledgling developers, and abused more frequently than used correctly. Still, libraries are the most important in-the-wild occurrance of the principle, and without them modern software engineering would not be possible. So how is it that many large scale companies, banks especially in my experience, avoid building their own commons and service templates like the plague? 

That's a question that is tough to answer - on one hand having a service template makes boostratping new projects and uplifting old ones much easier and lets developers focus on business logic not the tedious tasks of setup at the beginning and later monitoring, logging, error handling, configuration, security... and many more. On the other if you get one thing in that service template wrong, a whole lot of applications are suddenly in danger of falling victim to the same bug or design flaw. 

In this article I would like to shine some light on building a service template, specifically one focused on Kafka Streams. An avid Kafka Streams user might point out that Michelin has open sourced their own framework for bootstrapping such services, however not all tech driven companies are eager adopters of such novelties, and so it might be worth pointing out my own approach, and the difficulties I faced, some of which may seem counterintuitive at first. 

# The mandatory elements of a good service template
Before I dive into what exactly made my template a little special lets have a look at what every proper service template should provide. 
## Security
Your service template should provide an easy out of the box way to access user authorization. If there are multiple ways to authorize within your organization eg: SSO and SSL Certificate, then you should provide a configuration option which one is going to be enabled. 

Furthermore your Template Service should provide either easy annotations or at the very least a utility to check in signed in user and enable/disable security completely. 

Configuring and dealing with security on a project is always done once and then pretty much forgotten - aim to make it an implement once, import always task. 
## Logging
All applications log details about their inner workings and processing. A must is providing proper logging configuration which can be overriden and sensible defaults in your service template. 

There have been lengthy books written about what to log and how often. My personal experience has given me the following rule:
**Log enough to be able to tell exactly what happened at each step of processing**
## Metrics
Like logging proper metrics collection is the backbone of a properly functioning, IT-driven company. Metrics can also act as an early warning system, and hopefully will tell you your systems are malfunctioning before the users start doing just that. There are a few things which should always be measured, and your Service Template should provide that in a discrete manner without any extra configuration from the user. 
1. Processing time - whether you are processing Kafka messages or HTTP requests your service should be able to tell how long it took to process them. 
2. Errors - any time an exception occurs your metrics should indicate that. 

Metrics are tied to alerting, but that is something that usually isn't part of your service template, unless you decide to include deployment and operations details in it. That however is a matter of a totally separate article. 
## Testing 
Often times a company has a single tech stack dedicated 
## Configuration
## Common Data Access Objects
## Useful Design Patterns
## Proper Documentation!
## Optional: Sample application

# Making use of a Service Template
## Import
## Clone

# Kafka Streams Service Template