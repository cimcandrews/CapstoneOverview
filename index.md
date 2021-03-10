---
layout: default
---

## Welcome to our Capstone Project

Ty Bergstrom

Ian McAndrews

---

## Overview

Our proposed project is to provide a solution to help automate monitoring health misinformation in social media, and to help provide tools to process and understand the misinformation data and the responses to misinformation. We will work directly with the Journalism and Public Communications Department Chair and the Alaska Public Health Information Response Team to provide a solution to suit their needs.

We were considereing scraping the Facebook pages for new comments, but there is no way to do that without violating FB terms of service. 

We are considering developing a web application to help make the monitoring, notifying, and responding process more smooth. Our application lets users submit new misinformation comments, and the health team automatically receives email notifications when new comments are submitted, which is one way to make the process smoother. (Furthermore, the team can easily add new responders to the email list - new responders will not have to download anything or sign-up in order to start getting notifications.) 

Additionally, we are considering using Machine Learning and Natural Language Processing to help automate certain tasks and to help analyze the misinformation and to help inform the team what makes a good response. We are considering using the web application for processing and presenting data, including WordClouds, diagrams, and other visualizations. 

## Read about the Information Response Team here!

They were featured in the Anchorage Daily News.

[https://www.adn.com/alaska-news/2021/02/10/alaska-public-health-experts-are-taking-the-fight-against-covid-19-misinformation-to-facebook-comment-threads/](https://www.adn.com/alaska-news/2021/02/10/alaska-public-health-experts-are-taking-the-fight-against-covid-19-misinformation-to-facebook-comment-threads/)

## Basic To-Do

  - [x] Research Facebook Graph API for scraping comments from pages.
  - [x] Research Facebook terms of service and policies for their data.
  - [x] Abandon all ideas of scraping anything from Facebook.
  - [x] Develop an app with basic user functionality.
  - [x] Create a simple website for Capstone class progress reports and presentations (this page).
  - [ ] Create a separate page for the final "poster" presentation.

## Advanced To-Do

  - [x] Implement a system to submit misinfo comments and notify the Response Team.
  - [ ] Collect data (the misinfo comments and responses).
  - [ ] Create data visualizations of the misinfo data.
  - [ ] Do Machine Learning and Natural Language Processing projects to help understand the misinfo.
  - [ ] Integrate the ML projects into the app - use the app as an interface for the ML tools and visualizations.
  - [ ] Implement a model to predict how likely a comment is misinfo or not - a misinfo classifier.
  - [ ] Migrate application to an external server for long-term deployment.
  - [ ] Test the application thoroughly.






<br><br>

### Week of Tuesday March 16 and Thursday March 18 project update status report

- TBA...

- TBA...

- TBA...

# - Tracking sentiment analysis - for comments containing a keyword

For example, to help understand 'what is the +/- sentiment towards vaccines or masks in the misinfo comments'

![Image](https://raw.githubusercontent.com/cimcandrews/CapstoneOverview/gh-pages/assets/trackwordsent0.png)

<br>

![Image](https://raw.githubusercontent.com/cimcandrews/CapstoneOverview/gh-pages/assets/trackwordsent4.png)

<br>

![Image](https://raw.githubusercontent.com/cimcandrews/CapstoneOverview/gh-pages/assets/trackwordsent2.png)

... We already know there are lots of negative comments overall, but it looks like there is more negativity concentrated in comments containing the word "flu" ... it seems like this might be informative...

<br>

![Image](https://raw.githubusercontent.com/cimcandrews/CapstoneOverview/gh-pages/assets/trackwordsent3.png)

<br>

# - Text processing

Did some more work on processing input.

![Image](https://raw.githubusercontent.com/cimcandrews/CapstoneOverview/gh-pages/assets/submitcomment.png)

<br>

When users input the link to a facebook comment, we process it to make sure it's the right link to a comment.

Also, when you copy a link to a comment, the facebook links are full of garbage, so we process all links down to only what is necessary.

Therefore, it's easier for users to input the links, and the response team will always get accurate links to comments.

For example, users can just copy and paste the link:

- https://www.facebook.com/alaska.dhss/posts/10158906939714929?comment_id=10158907457684929&reply_comment_id=10158909556429929&__cft__[0]=AZUaNwRFn2ZMih1i8ezszTzrs9HovZSb6FSfUJZSer1B_Jl2GCHg29BJXfiQQ2RB6TIRYf_r7RPdjm4n6wUV6vsnyl9_jOsDk3odnJJLSWIbpSSHn_MM69TJ6oXewHspPhqGHgY1oq599houY3wybuH-&__tn__=R]-R

And we make sure it gets processed down to:

- https://www.facebook.com/alaska.dhss/posts/10158906939714929?comment_id=10158907457684929&reply_comment_id=10158909556429929

And now all of the links to comments in our database are standardized like this.

We made sure to test this with all types of valid comments, including replies to video streams.

We also did some more processing for links found in comments. It makes sense to just pre-process all links in the input comments, because this is the data that goes into the WordClouds and sentiment analysis and everything else, so now that will be easier to work with.

For example, sometimes a misinformation comment is just a link (usually to a non-reputable biased source), for example:

![Image](https://raw.githubusercontent.com/cimcandrews/CapstoneOverview/gh-pages/assets/commentlink.png)

<br>

If you copy and paste this link:

- https://www.infowars.com/.../seniors-who-already-beat.../

it's better if we just parse it now, and not have the garbage in our dataset.

Additionally, if you copy this link directly from facebook, you get this:

- https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.infowars.com%2Fposts%2Fseniors-who-already-beat-covid-19-are-dying-after-taking-the-vaccine%2F%3Ffbclid%3DIwAR3EPFP8hBwSbg4K0MrH-WIhh3DGMp4mcTvk8egsrMkNKtILKL6JXhfiXmY&h=AT3uDyp77_LFERjJlsedWCWOF8uCdGvQdOLzmEXgrXQaBh8P9VxZpejdXUXLCHpquqEyEpUexB2rHMDkfwpEzc6ewSNfaO2E0ZaP9GPyGu1BlbEMrIzszBa2cOvY&__tn__=R]-R&c[0]=AT3tBwZC2jtGnStLhYcdUhzVzvu_ryImz1q15CgpGYYbvt7rD5EGcAWDhbCXI6FAawI6lOuw9gNlLBMivhiEgTJPTU4cYZbYWMJTRhfqX1mxY8VaI6sahGyK3bplb-WaHaVz9V7meAYpmmFcV7Me8IKh-jc1HZ1rpez7I2cCqx_qmgDv

This is obviously even worse garbage, so we make sure that whatever our users copy and paste and submit, we parse it all down to:

- infowars.com

So now we have better data in our database, less garbage, and processing will be smoother later in the machine learning pipeline. It's not important to get the full link, because it's junk anyways, so just parsing down to the source is good enough. Now we can easily query our database to see what are the sources found in misinfo comments.

# - Always doing more work on the ML tools and data visuals

- Adding more functionality, such as selecting date ranges.

- More work on bigrams and phrases:

![Image](https://raw.githubusercontent.com/cimcandrews/CapstoneOverview/gh-pages/assets/freqbigrams0.png)
<br>

![Image](https://raw.githubusercontent.com/cimcandrews/CapstoneOverview/gh-pages/assets/freqbigrams1.png)
<br>

- Another example: it's easier to look at comments per day over a specific time period:

![Image](https://raw.githubusercontent.com/cimcandrews/CapstoneOverview/gh-pages/assets/comments_per_day3.png)
<br>

![Image](https://raw.githubusercontent.com/cimcandrews/CapstoneOverview/gh-pages/assets/comments_per_day4.png)
<br>

# - Added an optional "notes" field for submitting comments, to help with communication between the monitors and the responders

![Image](https://raw.githubusercontent.com/cimcandrews/CapstoneOverview/gh-pages/assets/submitcomment1.png)
<br>

![Image](https://raw.githubusercontent.com/cimcandrews/CapstoneOverview/gh-pages/assets/submitcomment2.png)
<br>

# - Reminder: There's a bonus tool! You can select "View All Misinformation Comments" and then you can ctrl+F to search all of the comments for any keywords. It's also a great way to help quickly find an old comment, or if you need to locate a similar/duplicate comment that has almost the same wording. This way, you won't have to search through your browser history or scroll through lots of pages.

![Image](https://raw.githubusercontent.com/cimcandrews/CapstoneOverview/gh-pages/assets/bonustool.png)
<br>








<br><br>

### Tues. March 2 and Thurs. March 4 project update status report.

- Started collecting new data.

- Working on migrating application to a production server.

- Updating email server.

- Lots of testing and refactoring.

- Still working on other ML and NLP projects and other data visualizations.

# - Sentiment analysis!!

![Image](https://raw.githubusercontent.com/cimcandrews/CapstoneOverview/gh-pages/assets/sa0.png)

<br>

![Image](https://raw.githubusercontent.com/cimcandrews/CapstoneOverview/gh-pages/assets/sa1.png)

<br>

# - Still working on extracting bigrams and longer phrases

![Image](https://raw.githubusercontent.com/cimcandrews/CapstoneOverview/gh-pages/assets/bg.png)

<br>

# - Tracking word usage!!

![Image](https://raw.githubusercontent.com/cimcandrews/CapstoneOverview/gh-pages/assets/trackwords0.png)

<br>

![Image](https://raw.githubusercontent.com/cimcandrews/CapstoneOverview/gh-pages/assets/trackwords1.png)

<br>

![Image](https://raw.githubusercontent.com/cimcandrews/CapstoneOverview/gh-pages/assets/trackwords2.png)

<br>

![Image](https://raw.githubusercontent.com/cimcandrews/CapstoneOverview/gh-pages/assets/trackwords3.png)

<br>

![Image](https://raw.githubusercontent.com/cimcandrews/CapstoneOverview/gh-pages/assets/trackwords4.png)

<br>

![Image](https://raw.githubusercontent.com/cimcandrews/CapstoneOverview/gh-pages/assets/trackwords5.png)

<br>

<br><br>

### Tues. Feb. 23 and Thurs. Feb. 25 project update status report.


- Most of the data has been collected!

- Still working on misinfo classifiers! Likely will need to augment the dataset with other datasets.

# - Setting up the data visualizations with the application!!

<br>

![Image](https://raw.githubusercontent.com/cimcandrews/CapstoneOverview/gh-pages/assets/data_exp.png)

<br>

# - Setting up data visualiziations for selected date ranges!!

<br>

![Image](https://raw.githubusercontent.com/cimcandrews/CapstoneOverview/gh-pages/assets/date_range0.png)

<br>

![Image](https://raw.githubusercontent.com/cimcandrews/CapstoneOverview/gh-pages/assets/date_range1.png)

<br>

# - Setting up trending topics visualizations with Latent Dirichlet Allocation models!!

<br>

![Image](https://raw.githubusercontent.com/cimcandrews/CapstoneOverview/gh-pages/assets/LDA0.png)

<br>

![Image](https://raw.githubusercontent.com/cimcandrews/CapstoneOverview/gh-pages/assets/LDA1.png)

<br>

# - Also thinking of other visualizations, such as most frequent words:

<br>

![Image](https://raw.githubusercontent.com/cimcandrews/CapstoneOverview/gh-pages/assets/freqwords0.png)

<br>

![Image](https://raw.githubusercontent.com/cimcandrews/CapstoneOverview/gh-pages/assets/freqwords1.png)

<br>

# - Also providing other analysis, such as looking at the number of misinfo comments and responses per day:

<br>

![Image](https://raw.githubusercontent.com/cimcandrews/CapstoneOverview/gh-pages/assets/comments_per_day1.png)

<br>

![Image](https://raw.githubusercontent.com/cimcandrews/CapstoneOverview/gh-pages/assets/comments_per_day0.png)

<br>

![Image](https://raw.githubusercontent.com/cimcandrews/CapstoneOverview/gh-pages/assets/comments_per_day2.png)

<br>

<br><br>

### Tues. Feb. 16 and Thurs. Feb. 18 project update status report.

Still working on the app, updating it, and testing it.

Most of the user functionality is stable. This includes user account stuff (securely invite new users, access permissions, login/logout, etc), submitting comments, receiving email notifications for new comments, changing email notification setting, etc. We are now mostly working on integrating ML and NLP data processing and visualizatinos to the app.

Machine Learning and Natural Language Processing Tasks:

- Collect more data.

- Build a classifier to predict: Given a submitted comment, how likely is it misinfo.

	- Implement the misinfo classifier on submitted comments, include prediction in the automatic email template.

- Generate WordClouds:

	- For misinfo comments, For good responses.

	- For date ranges: All time, This month, Last month, etc.

- Build a trending topics model using LDA: Generate the trending topics for:

	- misinfo comments, for date ranges

- Sentiment analysis visuals: Track sentiment analysis over time

	- for misinfo comments, for date ranges

- What types of posts are more likely to generate more misinfo comments

	- based on post title? based on linked article title and content? based on keywords or topics (mask, vaccine, etc)

- what types of good responses are more associated with increased positive engagement

	- positive engagement = "Likes" and other positive affirmations

	- types of responses could be considered classes:

		- has links to articles, has humor, has a certain GIF, has other image

- When are good responses most effective:

	- up to 6 hours after the misinfo comment was posted, within 24 hours, after 24 hours


These are some of the things that the Response Team has mentioned that might help them, and we would like to do as much of these as we can. 

We will be very busy collecting data, processing data, building models, generating visualizations, and integrating it all into the app and making it easy for the team to view the data.



<br><br>

### Tues. Feb. 9 and Thurs. Feb. 11 project update status report.

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
  
  - We are considering how to automate the "vetting"
  
    - Currently, when someone submits a misinfo comment, it manually "vetted" to make sure it is misinfo before
    sending off the notifications.
    
    - So we can work on training models to predict:
    
      - Given a comment, how likely is it a misinformation comment
    




<br><br>

### Thursday February 4, 2021 project update status report.

We have built a web app:

![Image](https://blog.corp-site.envato.com/cdn-cgi/image/width=820,quality=85,format=auto/uploads/2020/03/giphy-5.gif)

Users are able to create accounts, log in, log out, etc.

![Image](https://media1.giphy.com/media/26uf9Q4RRbWl5DA88/giphy.gif)

The users (the journalism students) who monitor FB pages for misinformation are able to submit new misinformation comments:

![Image](https://raw.githubusercontent.com/cimcandrews/CapstoneOverview/gh-pages/assets/mm0.png)

The response team will get automatic email notifications when a new comment is submitted, with the link to the comment included in the email:

![Image](https://raw.githubusercontent.com/cimcandrews/CapstoneOverview/gh-pages/assets/mm1.png)

Users are also able to view the newly submitted comments (with links). These new comments can be manually deleted after someone has responded to them, or they can be left for reference:

![Image](https://raw.githubusercontent.com/cimcandrews/CapstoneOverview/gh-pages/assets/mm2.png)

Next steps

We are meeting with the health information response team again to discuss their needs for ML and NLP.

We are thinking of training models to:

- Given a misinfo comment, predict which response is best.

- Given a factual response, predict how useful is it (how likely is it to end a discussion / shut down a misinfo thread)

- Also generate word clouds and other data visualizations.

We are still discussing with the team what would work best for them. They also have not decided exactly which pages they are going to monitor. We are beginning to collect data. For data collection, we will be manually collecting lots of samples of misinfo comments from FB and Twitter. We will also collect their responses that they have already made, which are available on some of the FB pages. 

For now it looks like we will not be automatically scraping for new comments, as this is against FB terms of service. The health information response team understands this and was not surprised, so we will most likely not pursue this.
