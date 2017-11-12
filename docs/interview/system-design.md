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

For example, use RESTful APIs and deploy exact clones to each server instance. A good API shouldn't store any
session or user information so the user can be equally served by any machine.

### Databases

The data storage layer is a very common (and potentially expensive) bottleneck. Strategies for scalabiltiy include:

* Denormalization
    * Normalization refers to optimizing cols and tables to reduce data redundancy and improve integrity
    * Denormalizing involves removing joins from retrievals
    * Sacrifice write perf for much better read perf and scalability
* Sharding
* Tuning

### Caching

* Memcached or Redis

There are two common strategies

* Cache database queries
    * Hashed query as key for response
    * Main issue is cache expiry
    * Complex queries cache poorly
* Cache objects
    * More involved setup
    * Cached values represent logical components of the app




## 4. Scale the System

Now we dive into details depending mainly on the interest shown by the interviewer or your strengths.


# Examples

Here are some common open-ended system design problems.

## Twitter Clone

Design a clone of Twitter

### 1. Clarify Constraints

* How many users will we served
    * How engaged will they be
        * How often they tweet
        * like/favorite tweets
* How will users interact
    * can they follow each other
* How complex can their interactions be
    * search / filter

Say, 1M users, 1M tweets/day, 5M favorites/day, 10 "follows" per user, expect some major outliers

### 2. Abstract Design

Now that we have aproximite scale, we can start considering designs. We know we need to:

* 


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




# Additional Resources

* High Scalability Blog
    * [ESPN](http://highscalability.com/blog/2013/11/4/espns-architecture-at-scale-operating-at-100000-duh-nuh-nuhs.html)
    * [EyeEm - Deep Learning Models](http://highscalability.com/blog/2017/10/23/one-model-at-a-time-integrating-and-running-deep-learning-mo.html)
    * [Facebook live streams](http://highscalability.com/blog/2016/6/27/how-facebook-live-streams-to-800000-simultaneous-viewers.html)
    * [Kraken.io image optimization](http://highscalability.com/blog/2016/6/15/the-image-optimization-technology-that-serves-millions-of-re.html)
    * [Plenty of Fish](http://highscalability.com/plentyoffish-architecture)
    * [Twitter image uploads](http://highscalability.com/blog/2016/4/20/how-twitter-handles-3000-images-per-second.html)
    * [Twitter storing data](http://highscalability.com/blog/2011/12/19/how-twitter-stores-250-million-tweets-a-day-using-mysql.html)
    * [Twitter timeline](http://highscalability.com/blog/2013/7/8/the-architecture-twitter-uses-to-deal-with-150m-active-users.html)
    * [Uber](http://highscalability.com/blog/2016/10/12/lessons-learned-from-scaling-uber-to-2000-engineers-1000-ser.html)


