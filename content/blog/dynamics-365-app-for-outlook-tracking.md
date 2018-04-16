---
title: "Dynamics 365 app for outlook tracking"
date: 2018-03-25T21:20:08+01:00
draft: false
banner: "img/blog/outlook-app/FirOutlookApp1.png"
author: "Martin Grinde"
categories: ["Dynamics 365"]
tags: ["promo"]
---

<br>

When Microsoft release Dynamics 365 app for Outlook, they introduced a client with modern and seamless experience for tracking email to Dynamics 365. While the client introduces a lot of great benefits that were no doubt great, it forgot one of the most basic tasks. Before you could see a small icon on emails when things were tracked. 

<img class="img-fluid mt-4 mb-4" src="/img/blog/outlook-app/OutlookApp1.png" /> 
<br>
Now you have to open the outlook client on every single email you have in the inbox to see if it has been tracked. The goal of making a users workday easier just got a little harder. Did I remember to track this email?  
 
George Rizk found a great and simple solution to the problem of viewing tracked emails that he posted to the community: https://community.dynamics.com/crm/f/117/t/257004 .  
 
The genius solutions he provided was conditional formatting to emails in your inbox based on the tracked status in CRM! (see picture below).  
  
<img class="img-fluid mt-4 mb-4" src="/img/blog/outlook-app/OutlookApp2.png" /> 
 
All you have to configure is the following:  
 
Outlook stores a value based on the tracking status in the “crmLinkState” column. <br> 
0 – Not tracked but has been tracked at some point <br>
1 – Tracking pending <br>
2 – Email is tracked <br>
 
The column can be added to outlook by navigating to – View – View Settings 
  
<img class="img-fluid mt-4 mb-4" src="/img/blog/outlook-app/OutlookApp3.jpg" /> 

Click Columns <br>
  
<img class="img-fluid mt-4 mb-4" src="/img/blog/outlook-app/OutlookApp4.png" /> 
  <br>
Click New Column 
<br>
  
<img class="img-fluid mt-4 mb-4" src="/img/blog/outlook-app/OutlookApp5.png" /> 
  <br>
Write: crmLinkState in name and Type: Number 
<br>
<img class="img-fluid mt-4 mb-4" src="/img/blog/outlook-app/OutlookApp6.png" />  

Now that we have the column we can create the conditional formatting based on the tracking status. Navigate back to View Settings and chose “Conditional Formatting”.  

Choose Add and give the rule a name.  
  
<img class="img-fluid mt-4 mb-4" src="/img/blog/outlook-app/OutlookApp7.png" /> 
  <br>
Click on condition on the rule and choose the tab Advanced in the new window. Here you can add “crmLinkState” and set value based on the state.  
  
<img class="img-fluid mt-4 mb-4" src="/img/blog/outlook-app/OutlookApp8.png" /> 
<br>  
At last we choose how we want to format the emails with the status «2» that we have in the example above.  

<img class="img-fluid mt-4 mb-4" src="/img/blog/outlook-app/OutlookApp9.png" /> 
  <br>
FINALLY we can see emails we have tracked! 

<img class="img-fluid mt-4 mb-4" src="/img/blog/outlook-app/OutlookApp10.png" /> 
 