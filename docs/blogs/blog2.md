---
title: Lecture 14 - Review Session, Critique of HTTP Status Codes
layout: doc
---

# Lecture 14 - Review Session, Critique of HTTP Status Codes

<a href="https://mpadilla198.github.io/portfolio-miguel-padilla/blogs/blog1.html">Link to original post</a>

I found Miguel's thoughts on HTTP Status Codes very insightful! Prior to working with APIs, I was unaware of the existence of any status codes but 404 and 500. This past summer however, I became very familiar with these codes by working on a project for my internship which involved developing a system of APIs. Part of my work was to create documentation for each API, essentially defining valid pre conditions and post conditions for each system, similar to what we have learned to do with our code. One part of Miguel's post which particularly resonated with me is when he stated that "status codes have as much meaning as we [give to] them". Although Miguel did not directly state this in his post, I believe his points not only show the importance of status codes, but also the importance of writing documentation for APIs--especially those used by third-party applications. 

One thought I would like to add is that while it is true the specific number of a status code does not necessarily impact core functionality, I do believe that carefully defining specific error codes and error classes allow for a stronger connection between the front end and back end of applications. To be more precise, let's say a user attempts to complete a task and some of their actions fail in the backend. By using unique, specific error codes in our backend, we have the opportunity to modify the user flow to allow the users to correct past mistakes rather than displaying error messages.