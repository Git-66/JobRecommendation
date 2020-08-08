# AWS based Web Service Development – Job Recommendation 

It is a Restful Web Application using Java Servlet, used Amazon Relational Database Service to store data and deployed to AWS EC2 with Docker. The main functions of this service is to obtain a users geo-location, retrieve all open nearby jobs available based on the users location, 
the ability to save job offers that a user is interested in and this system can automatically recommend jobs based on keywords that are extracted from the users saved jobs. 


## How to Run 
### Local Deploy 
You need to set up Tomcat server, add JobRecommendation web application from a server and restart the server.  You can play it on http://localhost:8080/jupiter now
### EC2 Deploy
1. Launch an EC2 instance 
2. Connect to the instance; Run Docker container on EC2 VM 
3. Build Job Recommendation app Archive and Upload to EC2
4. Build a Docker Image 
5. Run a Docker container
## About the Service
I used Java to build a few servlets. The first one is a SearchItems API that provides the functionality to search job around, 
The second servlet that allows a user to set or unset their favorite records. 
The last one that recommends similar items to the user. 
And I deploy these servlets on tomcat.

### Restful 
Makes quickly adding a RESTFul API to my project easy. Restful API provides full HTTP verb support (GET, PUT, POST, DELETE) for my resources, 
as well as the ability to job, history,recommendation. You will also have the ability to read and manipulate related data with ease.
### GitHub API
This project uses data fetched from GitHub jobs via the GitHub Job API. GitHub Job API is a web-based API provided by GitHub that allows clients to 
get retrieve job data from the GitHub Job server. 
Official Documentation: https://jobs.github.com/api 
### MonkeyLearn API
After we fetched data from Github API, we requires some keywords/categories for content based recommendation. So the keyword extraction and use Monkey Learn API to achieve t
he results. The Java examples provided by Monkey Learn API reference : https://github.com/monkeylearn/monkeylearn-java
### Recommendation Algorithms - Content-based Recommendation
The key concept behind a content-based recommendation is the idea that "people will like things of similar characteristics". In particular, it means that given 
different characteristics of an item (category, price, keyword) that a user has liked, recommend items that share the same profile.
Content-based recommendations use the similarities within different items for a recommendation, and it is widely used for services under cold start conditions. 

Here are some endpoints you can call:
```
http://localhost:8080/jupiter/search?lat=37.38&lon=-122.08
http://localhost:8080/jupiter/recommendation
http://localhost:8080/jupiter/history
http://localhost:8080/jupiter/login
http://localhost:8080/jupiter/logout
http://localhost:8080/jupiter/register
```
## Built MySQL database on Amazon Relational Database Service(RDS) to store data 
### Tables for jupiter project
```
users - store user information.
items - store item information.
keyword - store item-keyword relationship
It’s an implementation detail, we could save keywords in the item table, but there will be more string join/split manipulations in our code, 
so let’s save them in a separate table.
history - store user favorite history
```

