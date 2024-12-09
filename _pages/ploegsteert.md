---
title: "Tech Lead at Immotef on a Project for Ploegsteert"
layout: single
permalink: /ploegsteert/
author_profile: true
toc: true
---
# About the Company
Plogesteert is a Belgian company making decorative bricks. 

# About the Role
Tech Lead at Immotef on a Project for Ploegsteert

My job was to design and lead the implementation of a solution for visualizing configurable brick facades.

# Projects Overview and Technical Challenges
The project consisted of a couple of modules:
1. The texture generator - a JS library that could work as frontend and backend dependency
2. The source images processing pipeline - a Python service which processed the images and stored them into S3
3. The orchestrating service - a Java (Spring) backend which handled the customer's configurations, translations, images and products - effectively a PIM sidecar
4. A control panel - a React frontend for handling customer configurations and interactions
5. A texture generating widget - a widget that could be embedded via iFrame and generated textures for desired specifications
6. A high resolution texture generator service - a JS service used for generating high resolution textures on demand

All the services communicated over AMQ. 

The main technical challenge that emerged was making sure that the customer data loaded quickly and that some texture loaded immediately. We leveraged a CDN to preload default textures, and rendered actual textures only on client demand. 

Other than that effective image processing and handling of multiple regions required that the system be turned into a multi-tenant solution after the initial implementation. We leveraged Spring's AOP and an additional customer_key column on all our entities to achieve this. 
