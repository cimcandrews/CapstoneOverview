## Welcome to our Capstone Project

** Ty Bergstrom **

** Ian McAndrews **

---

![Image](https://stryvemarketing.com/wp-content/uploads/2016/04/welcome.gif)

![Image](https://stryvemarketing.com/wp-content/uploads/2016/04/image.gif)

---


# Summary
  Our Capstone project is to provide a solution to help automate the monitoring of health misinformation in social media. To achieve this, we are working directly with the Journalism and Public Communications Department Chair and the Alaska Public Health Information Response Team to build a web-application that suits their needs.
  To accomplish this, we are building the web-application to pull comments from several predefined Facebook pages, that users can flag as misinformation that needs to be addressed.
  
## Basic To-Do
  
  - [ ] ~~Use GitHub Pages to host our web-app.~~
  - [x] Look into the Facebook Graph API for pulling comments from pages.
  - [ ] Learn more about the terms of service and policies Facebook has in place for their data.
  - [x] Build app using Flask instead of HTML and JavaScript (Therefore, unable to use GitHub Pages to host our web-app).
  - [x] Implement Python libraries instead of FB Graph API to pull comments from public Facebook Pages.
  - [x] Build a simple website for Capstone class progress reports and presentations.
  - [ ] Work on implementing a system for the Chair of the Journalism and Public Communications Department to easily receive flagged comments to submit to the Information Response Team.
  - [ ] Migrate application to external server as a long-term usage goal.
  
## Advanced To-Do
  - [ ] Visualize characteristics of misinformation behavior (probably using matplotlib and Python).
  - [ ] Implement some sort of ML model that can weigh how likely a comment is misinformation or not.







# Thursday February 4, 2021 project update status report.

# We have built a web app:

## Users are able to create accounts, log in, log out, etc.

![Image](https://blog.corp-site.envato.com/cdn-cgi/image/width=820,quality=85,format=auto/uploads/2020/03/giphy-5.gif)

# The users (the journalism students) who monitor FB pages for misinformation are able to submit new misinformation comments:

![Image](https://media1.giphy.com/media/26uf9Q4RRbWl5DA88/giphy.gif)

# The admin users (the health professionals) will get automatic email notifications when a new comment is submitted, with the link to the comment included in the email:

![Image](https://media.tenor.com/images/4f5efc85854259b4f569ddefc474a633/tenor.gif)

# Users are also able to view the newly submitted comments. These new comments can be manually deleted after someone has responded to them:

![Image](https://media.tenor.com/images/4f5efc85854259b4f569ddefc474a633/tenor.gif)

# Next steps

## We are meeting with the health information response team again to discuss their needs for ML and NLP.

## We are thinking of training models to:

- Given a misinfo comment, predict which response is best.

- Given a factual response, predict how useful is it (how likely is it to end a discussion / shut down the misinfo)

- Also generate word clouds and other data visualizations.

We are still discussing with the team what would work best for them. They also have not decided exactly which pages they are going to monitor. We are beginning to collect data. For data collection, we will be manually collecting lots of samples of misinfo comments from FB and Twitter. We will also collect their responses that they have already made, which are available on some of the FB pages. 
