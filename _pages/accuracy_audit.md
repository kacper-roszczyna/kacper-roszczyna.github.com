---
title: "Client Case: Accuracy Audit"
layout: single
permalink: /accuracy_audit/
author_profile: true
toc: true
---
# About the Client

Accuracy Audit Ltd. is a small company focused on providing financial audit services. In Poland, where the company is headquartered and operates, all companies are obligated to have their financial reports audited by certified auditors. Accuracy Audit is a company which provides precisely that service. 

# My Role

Technical Consultant for Accuracy Audit Ltd.

I did not hold any role directly within the company, however I was allocated support to solve a specific problem and help increase the amount of business generated by their sales process. 

# Case Study
> When life gives you lemons, make lemonade.
> <cite>Probably someone operating a lemonade stand</cite>

## The Problem
The client reached out to improve their process to source clients. In Poland the companies are required to be audited when they meet two financial criterias:
1. Their total asset value crosses a certain theshold 
2. Their total income crosses a certain threshold

## The Initial State of Affairs
The client had a couple of interns scour a public registry of court documents which are filed by all Polish companies every year. The process was time consuming, yielded very few leads and was quite costly.

## The Constraints
There were two key constraints for this project:
1. Time - the client reached out fairly late in terms of the financial audit year, as such there was hardly two weeks to complete the project and create a working solution, before it would become unviable
2. Cost - the client stated upfront that there is very little budget allocated to the project. However how little, I had yet to learn.

## The Solution - V1 - Modern AI Use Case
From the start of the project it was evident that the client is not looking for a big system, but rather a quick fix. With a constrained budget
I understood that my best bet to help them would be to create even a simple script that could be run on the company laptop. And while it doesn't sound
glamorous that's the fastest, cheapest solution that's going to create client value. 

Realizing that I knew that there are a few parts to this:
1. Pulling the data from the public registry - luckily the client provided me with an API for that
2. Reading the documents - at least two per company - and retrieving relevant financial markers
3. Checking the financial markers
4. For companies that qualify pulling the data about their address, web page, email and board from the public registry

Additional requirements not specified by the client:
1. Financial markers have to be configurable
2. This script has to be configurable to search for all companies registered in a range of dates
3. This script has to be run every half-year or quarter

While there is nothing particularly fancy in retrieving data - this can be done via curl even, the data retrieval aspect was a concern. The data is stored in PDFs. 

I recommended the client we use one of the recently released closed source multi-modal LLMs like ChatGPT. However this would mean that evaluating each company would cost at least 50 cents. At over 10k registered companies per quarter that was not a feasible cost for the client. 
As such I had to put my engineering gloves on, abandon OpenAI and get down and dirty with the code.

## The Solution - V2 - Tesseract
In such a predicament the only solution was to go old-school and use an OCR which could run locally. I am not an ML expert so understanding and using one coded from scratch could take too much time. However a very useful OCR is widely available already, and requires little effort to integrate into any Linux system. 

The solution is called Tesseract and provides a lot of functionality in a neatly packaged command line module. One of its functionality is pdf to text conversion. With some experiments and research the right set of options provided a file which was almost as good as a csv to work with. 

And so the final solution to the client's need was a simple Java program, based on Spring. 
While it was a crude solution it met all the clients requirements and allowed them to retrieve all the data 
they required at less than 4 cents per company. It also yielded enough new customers to nearly double their profits at the time. 

# Further Reading