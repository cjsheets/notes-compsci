# Overview

Interviews often contain a system design component. At face value, the questions can seem overwhelming
but a couple common strategies can make the tasks manageable.

## Example Questions

* Design a URL Shortening Service
* Design the Google Search engine

# Strategy

## 1. Clarify Constraints

The first step is to scope the problem. You can't design a system for an ambiguous problem.

Resist the temptation to dive into any particular component.

https://raw.githubusercontent.com/antonrd/hiredintech_files/master/system_design/digram_url_shortening.jpg


## 2. Abstract Design

Layout the principle components at the highest level possible.

Again, resist the temptation to dive into any particular component.


## 3. Understand Bottlenecks

Your system will typically have bottlenecks based on its constraints. It's goal is to choose scalable
approaches that allow growth using standard tools or techniques.


## 4. Scale the System

Now we dive into details depending mainly on the interest shown by the interviewer or your strengths.


# Examples

Here are some common open-ended system design problems.

## URL Shortener Service

Design a service to shorten URLs

### 1. Clarify Constraints

Define primary user flows. 

* Shorten URL
* Perform Redirection
* ? Custom URLs
* ? Analytics
* ? User management of Urls

Determine rough estimate of requirements for constraints.

If we expect 1B requests / month, we need to support ~380 requests per second. It's fair to assume
90% of requests are to redirect and 10% to shorten. 

If we allow 8 bit ASCII characters we can assume 1 byte per character.

10% of 1B is 100M new URLs / month. In 1 year we'd have 1.2B Urls to store.

To determine how many characters our URLs need, we can how many permutations are available. 26 lower + 26 upper case +
10 numbers = 62 characters. 62 ^ (number of characters) = available permutations. If we want the service to run for 10 years
we'd calculate (10 * 1.2B) = 62^n -or- log 62 (12B) = n -or- n = 5.6.

We could estimate each URL contains on average 200 characters and each hash takes 6. 

### 2. Abstract Design

Define the high level system components.

* Application service layer
    * Shortening service
    * Redirection service
* Data storage layer
    * Acts like a big hash table


### 1. Clarify Constraints


