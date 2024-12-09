---
title: "Tech Lead at Immotef on a Project for Wienerberger"
layout: single
permalink: /wienerberger/
author_profile: true
toc: true
---
# About the Company
Wienerberger is a Belgian company making decorative bricks and other structural elements

# About the Role
Tech Lead at Immotef on Projects for Wienerberger

My job was to design and implement a solutions for visual marketing and provide procution support for them

# Projects Overview and Technical Challenges
## Texture Visualizer
The project's focus was to provide a configurable widget that visualized a texture made of bricks the client sold. The customer had to be able to configure the texture to their liking, this included the mix of bricks, the joint color and thickness, and the bond type. All the while construction rules had to be preserved, so that the generated texture could physically be built from the customer's products. 

Additionally the customer could render the texture in a higher resolution. 

We leveraged multiple languages, and integrated the solution over AMQ. 

However the biggest challenge were two requests made by the client.

### Rendering shadows in 2D
The biggest challenge came with the client requesting that our texture be 3D rendered. We immediately shot down the idea, maintaining the constraints of rendering time and 3D in a web being performant wasn't feasible within the budget. However, I managed to find a different solution, one which would be considered **cheating**, only "there is no such things in graphics as cheating". 

The shadow was created by casting the pixels to black and white, shifting the texture and adding the images together in a weighted fashion. A trick, but a shadow. Effectively it met the visual requirements the client requested, and what more allowed us to only marginally impact the time of generating the texture.

### Rendering a 3D texture
The next step was taking a texture and overalying it on images. I implemented a function which transformed the 2D texture to look 3D by image manipulation. Sadly the project never made it to production, but it allowed me stretch those image-processing muscles. 