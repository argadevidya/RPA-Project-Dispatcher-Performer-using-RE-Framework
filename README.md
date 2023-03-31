# RPA-Project-Dispatcher-Performer-using-RE-Framework
Generate bulk offer letters in UiPath using RE framework.

### Table of Content
  * [Overview](#overview)
  * [Motivation](#motivation)
  * [Demo Video](#demo-video)
  * [Steps in the project execution](#steps-in-the-project-execution)
  * [Technical Aspect](#technical-aspect)
  * [Installation](#installation)

# 𝗥𝗼𝗯𝗼𝘁 𝗳𝗼𝗿 𝗛𝗥 | 𝗚𝗲𝗻𝗲𝗿𝗮𝘁𝗲 𝗢𝗳𝗳𝗲𝗿 𝗟𝗲𝘁𝘁𝗲𝗿 | 𝗨𝗶𝗣𝗮𝘁𝗵 | 𝗨𝘀𝗲 𝗰𝗮𝘀𝗲

### Overview 
Use Case Description:
Bulk Hiring / Campus Recruitment is a strategy for sourcing and hiring young crowd for internship or entry-level positions for medium- to large-sized companies with high-volume recruiting efforts.

Once the Hiring process is completed - The HR has to work on generation of offer letters and rollout the offer letters to the hired candidates which is a repetitive and mundane task. How about an Robot doing the same for the Team.

The HR Process for Generating Offer Letter ( Diagram )-

* Students / Candidates are Interviewed.

* Some are Selected , Some are Rejected

* As there are multiple Recruiters / Students - We keep track of all and maintain Status lets say in a Spreadsheet.

* At the End of the Day - We have to roll our offers to the candidates Hired and send them Offer letters - This Task is Mundane and Repetitive and has scope of Automation.

### motivation
With the Introduction on an RPA Robot - The HR Team can focus on the more Important Task and the Mundane task of generating the Offer letter can be given to the Robots.

* Robot Reads the Status Files from Email / Shared Location.

* Filter all the Hired Candidates

* Generate The Offer letters as per company template

* Send the Offer Letters to the Candidates.

### Steps in the project execution
Lets have a look at the solution design approach of the use case. we would have the Complete automation in 2 Parts Dispatcher and the Performer. Reason for having 2 robots is Scaling , Transaction Management and maintenance.

## 1. Dispatcher
The First part of the Robot would be called Dispatcher whose job would be load the information to Queue required for generating the offer letters. Now here we are free to use any HR application / Source (Emails / Excel / Shared Drive) having the details of the Hiring Drive and Candidates Information’s.
Robot Reading Date from a Source (Excel)
Filtering Data as per the Conditions
Adding Data to the Queue - This Queue will help to attain the Transactional Processing

## 2. Performer
The Second part of the Automation is called the Performer - where the Robot is supposed to read the candidates info one by one from the Queue and Generate the Offer Letters
Read Item one by one from the Queue populated by the Dispatcher
Read the Company’s Offer Letter
Generate Offer Letter
Send email to Candidates with Offer Letter as attachments.
