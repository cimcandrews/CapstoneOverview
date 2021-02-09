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




<br><br>

# Tues. Feb. 9 and Thurs. Feb. 11 project update status report.

Updates to the app include:

- Admin account is able to invite new users to register an account.

  - Otherwise it is not possible to register - you can only register via invite.
  
  - And of course the invite emails are set up and it works.

- Need to be logged in to submit comments, view comments, etc.

- Email notifications can be turned on/off.

  - So only the researchers get notifications for new comments.
  
  - And the Journalism students won't get emails.
  
  - The Admin account sets this when they invite a new user.
  
  - But users can still change the setting if they need to.

- NLP and Data...

  - Finally got access to their data, the previously submitted misinfo comments.
  
  - Started collecting the data, not finished. Collecting:
  
    - Misinformation comments.
    
    - Good responses to misinfo.
    
    - Bad responses to misinfo.
  
  - Started processing some of the data to se what we can do with it. So far, it looks like we can generate word clouds,
  extract Ngrams, extract URL links, and create visual displays.
  
  - Added webpages to display some of the data so far, to see what it looks like, to get feedback on what would be good

<br>

![Image](https://raw.githubusercontent.com/cimcandrews/CapstoneOverview/gh-pages/assets/ng.png)

<br>

![Image](https://raw.githubusercontent.com/cimcandrews/CapstoneOverview/gh-pages/assets/wc0.png)

<br>

![Image](https://raw.githubusercontent.com/cimcandrews/CapstoneOverview/gh-pages/assets/wc1.png)

<br>

![Image](https://raw.githubusercontent.com/cimcandrews/CapstoneOverview/gh-pages/assets/wc2.png)

<br>

![Image](https://raw.githubusercontent.com/cimcandrews/CapstoneOverview/gh-pages/assets/wc3.png)

<br><br>

Up next:

  - Keep collecting more data
  
  - Keep processing more data
  
  - It sounds like they want to automate the "vetting"
  
    - Currently, when someone submits a misinfo comment, they manually "vet" it to make sure it is misinfo before
    sending off the notifications.
    
    - So we can work on training models to predict:
    
      - Given a comment, how likely is it a misinformation comment
    




<br><br>

# Thursday February 4, 2021 project update status report.

# We have built a web app:

![Image](https://blog.corp-site.envato.com/cdn-cgi/image/width=820,quality=85,format=auto/uploads/2020/03/giphy-5.gif)

## Users are able to create accounts, log in, log out, etc.

![Image](https://media1.giphy.com/media/26uf9Q4RRbWl5DA88/giphy.gif)

# The users (the journalism students) who monitor FB pages for misinformation are able to submit new misinformation comments:

![Image](https://raw.githubusercontent.com/cimcandrews/CapstoneOverview/gh-pages/assets/mm0.png)

# The admin users (the health professionals) will get automatic email notifications when a new comment is submitted, with the link to the comment included in the email:

![Image](https://raw.githubusercontent.com/cimcandrews/CapstoneOverview/gh-pages/assets/mm1.png)

# Users are also able to view the newly submitted comments. These new comments can be manually deleted after someone has responded to them:

![Image](https://raw.githubusercontent.com/cimcandrews/CapstoneOverview/gh-pages/assets/mm2.png)

# Next steps

## We are meeting with the health information response team again to discuss their needs for ML and NLP.

## We are thinking of training models to:

- Given a misinfo comment, predict which response is best.

- Given a factual response, predict how useful is it (how likely is it to end a discussion / shut down a misinfo thread)

- Also generate word clouds and other data visualizations.

We are still discussing with the team what would work best for them. They also have not decided exactly which pages they are going to monitor. We are beginning to collect data. For data collection, we will be manually collecting lots of samples of misinfo comments from FB and Twitter. We will also collect their responses that they have already made, which are available on some of the FB pages. 

For now it looks like we will not be automatically scraping for new comments, as this is against FB terms of service. The health information response team understands this and was not surprised, so we will most likely not pursue this.
