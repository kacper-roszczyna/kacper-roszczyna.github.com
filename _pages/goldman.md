---
title: "Contractor at Goldman Sachs from ITDS Poland"
layout: single
permalink: /goldman/
author_profile: true
toc: true
---
# About the Company
Goldman Sachs is a pretty sizeable US based bank focused on corporate banking. In recent years it has started providing more and more retail services, however the core of its business remains centered around providing financial services on the market and to corporate clients worldwide. 

# About the Role
Senior Java Developer (Full Time Contractor) for ITDS Poland at Goldman Sachs

The role was a very standard senior developer role with a heavy focus on systems leveraging Kafka. I took part in a number of projects. Sadly, due to the signed documents I can not disclose exact details. However I can state that my work focused on building applications utilizing Java 6/8/11, Kafka, Kafka Streams, Spring, Weblogic and an occasional smidge of Python for reconciling data. 

# Projects Overview and Technical Challenges
## Replacing an existing cache with a Kafka Topic
Large corporations frequently run legacy software which can't be demised. One of the first projects I took part in was fixing a long cache warm up time. After some investigation it turned out that the main culprit is the contents of the cache. The solution, though unorthodox, allowed to drastically shorten the startup time of the application by persisting the cache entries onto the Kafka topic, and warming the cache from it. 

## Uplifiting a legacy system
As I mentioned earlier - large corporations run legacy software. Luckily, sometimes they also want to demise it. A project I was tasked with was to uplift a piece of code written in an internal scripting language of Goldman Sachs to a modern Java application. When I left the company the code was not yet productionized, however I later found out it finally made it into production. 

## Bug hunting
I fixed a number of small, though troublesome bugs related to Spring Reactor use in two core services. I also fixed a pesky bug related to the use of **HashSet** difference method and recurrance. 

## Designed and Built a System for Prioritizing Tasks for Operations
My final project was to build a system which prioritized tasks that had to be performed by operations. Each task was given a priority score based on its features and current company wide events. I utilized the Kafka Streams library, Spring and Java 11 to implement it. 