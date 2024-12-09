---
title: "Contractor at Clearstream from Be Shaping The Future Poland"
layout: single
permalink: /clearstream/
author_profile: true
toc: true
---

# About the Company
Clearstream is a major custody services provider based in Luxemburg and part of the Deutsche Boerse Group. The company provides a wide array of financial services.

# About the Role
Java Developer with Kafka

While the title is a little vague I was a contractor hired by Be Shaping the Future Poland to help in a project at Clearstream, which made heavy use of Kafka. My job was to build a distributed system in cooperation with Confluent and Clearstream Architects. I was part of a two developer team. 

# Project Overview and Technical Challenges
Sadly, I can't provide much details on the specifics of the project however some of the more interesting technical details abstracted away from the domain of the problem are listed below. The main challenge of the project was not in fact technical, but rather organizational. It was the first project of its kind in the unit, and as such the existing upstream systems weren't prepared to provide feeds of data on Kafka. 

## KStream-KStream join
One of our key tools was the KStream-KStream join without windowing. We achieved this by leveraging the Processor API provided by KafkaStreams library. 

## Monitoring 
Since our project was "the first of its kind" adequate dashboards, logging practices and metrics had to be created and collected. I leveraged Dynatrace and created reusable dashboards for subsequent Kafka Streams projects to use. 

## Robust Error Handling
The solution built was part of a **critical path** at the company, as such it could not fail even if processing the message would fail. I implemented a reusable solution which allowed to properly redirect errors and their causes to a dead letter topic from any point in the topology. 

## Handling Legacy Feeds and Infrastructure
As this was the first system utilizing Kafka legacy producers weren't able to supply data on the platform. One of my responsibilities was defining the connectors to properly consume produced feeds, as well as defining the topic policies and retention periods using Helm charts. 

## Cartography Tests
One of the biggest wins on the project was creating cartography end to end tests. These were tests which utilized **TopologyTestDriver** class and multiple topologies from all services involved in the system. These topologies were compiled into a single "super-topology", which allowed us to unit test the entire system behavior. It effectively cut down regression tests for the streaming component by half and later shortened the testing loop with FA involvment from 4 hours to half an hour. As a final stage of the project I encouraged the FAs to define new or problematic scenarios in tests before doing any manual tests. This significantly cut down on testing costs. Since these tests were faster, more stable and required less memory than a comparable suite utilizing **TestContainers** the team was able to run the entire suite in a Github Runner and make it part of every Pull Request. 

## Developing a Business Application Monitoring Solution
It's difficult to monitor a streaming system. Many events can come in varied order, not to mention the sheer traffic we faced. To facilitate it I built a service which consumed all relevant topics and created an ordered 'state of the world' for each processed item. This allowed the team to reason about the system state, find logic faults, improve testing speed in UAT level environments, and finally resolve issues in production, when they arose. 

# Personal Initiatives Outside of the Original Project Scope
## Kafka Streams Service Template
I built and internally marketed a commons repository, which served as a Service Template for other Kafka Streams projects significantly decreasing the onboarding time for new engineers, and allowing them to meet deadlines even with limited knowledge of Kafka Streams, and proper deployment structure for Kafka Streaming Applications. This has been succesfully used on two other projects at the time of writing this post.

The added benefit of the service were common components for:
1. Error handling
2. Cartography testing
3. Change Detection and Event Versioning
4. Idempotency Handling
5. Common metrics gathering - processing time of the record within topology and waiting time of the record

## Kafka Streams Application Bootstrap Guide
I wrote and internally marketed a checklist for deployment and design for Kafka Streams Applications. It was linked as a wiki to the Kafka Streams Service Template. It successfully helped resolve an issue with a deployment structure on at least one project at the time of writing. It also helped fix a Kafka Streams Topology bug on the same project, letting it meet a critical deadline. 

## Migration of a major component from Go to Java
During my contract with Clearstream I was instrumental in migrating an existing codebase which lacked support from Go to Java. While it might sound like a questionable choice given current technological choice it was important from an organizational point of view. Additionally the client's team was able to introduce new developers onto the project, which was previously impossible without external hiring. It improved the client's autonomy, support capabilities and most important confidency in the project. The main challenge of the migration was tied to the complications which came with certain design choices on the project. 
