---
title: "Lead Developer at Skelreplica"
layout: single
permalink: /skelreplica/
author_profile: true
toc: true
---
# About the Company
Skelreplica was a Polish startup aiming to facilitate the study of osteological structures. It developed a mobile application, which for a small fee gave medical students access to a whole library of possibly the best scans with marked regions denoting osteological structures.  

# About the Role
Lead Developer at Skelreplica

My job was to oversee the development of the mobile applications, the preparation of 3D assets and building the backend solution for the application. 

# Projects Overview and Technical Challenges
The project was a monolythic application build with Java 17 and Spring 5. It utilized PostgreSQL as the database, and JPA as the ORM. There were two main challenges on the project: secure serving of 3D models to users, handling of user subscriptions. 

## Secure Serving of 3D Assets
Assets were served from an Amazon S3 bucket using expiring links. All 3D Assets were additionally encrypted with a key that was part of the mobile application. A bad actor could potentially still decrypt the models assuming they would reverse engineer the application, however it provided enough security to protect the assets at this level of the business development. 

## Handling user subscriptions
The application contained in-app-purchases, as user subscriptions. We decided to handle them over existing Google Play Store and Apple App Stores to avoid possible issues during iOS application review process. As such the backend solution had to verify all subscriptions in a cron-job and handle cancellations. While it wasn't very challenging it led to an interesting integration with the APIs of both store providers. 
