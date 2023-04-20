# RPA-Project-Dispatcher-Performer-using-RE-Framework
Generate bulk offer letters in UiPath using RE framework.

### Table of Content
  * [Overview](#overview)
  * [Motivation & Project Explanation ](#motivation)
  * [Steps in the project execution](#steps-in-the-project-execution)
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

### Motivation
With the Introduction on an RPA Robot - The HR Team can focus on the more Important Task and the Mundane task of generating the Offer letter can be given to the Robots.

* Robot Reads the Status Files from Email / Shared Location.

* Filter all the Hired Candidates

* Generate The Offer letters as per company template

* Send the Offer Letters to the Candidates.

## Here we are using dispatcher-performer robots.Why we need to use this approach ?<br>

Dispatcher is a bot that we create to load some data into the queues/datatables. This data can be later used by another bot called as Performer.

Basically, it is breaking one single big bot (having both functions of loading and performing) into two pieces. One bot loads the data & the other performs over it.

So if you have got a process where it first fetched the input data from a resource and then process it later then use dispatcher and performer concept

Or

If you have a process which is used to keep the input ready for other multiple process then use a single dispatcher process to create new queue items as input so that it can be picked and processed by multiple performer bots


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

### Steps in the project execution
1.Read excel file data values using read range activity</br>
2.Open browser to visit "www.rpachallenge.com"</br>
3.Use anchor base activity->find element and type into activity to input form fields</br>
4.Use anchor base for all the form fields</br>
5.Use click activity to click on submit botton</br>
6.Use loop(step 3- step 5) to type into all fields for every round</br>
7.after all 10 rounds, the web site will show you the result with achieved accuracy and time</br>

### Installation

### Prerequisites

Before starting, make sure you have the following software and tools installed on your machine:

1. UiPath Studio (Community or Enterprise edition)
2. UiPath Orchestrator (Community or Enterprise edition)
3. Microsoft Excel


### Installation Steps for Dispatcher project:

* The project starts with the Init state. In this state, the Config.xlsx file is read to retrieve the necessary settings such as Orchestrator URL, credentials, and queue name.

* In the Get Transaction Data state, the employee data is read from an Excel file. This Excel file contains the employee details such as name, age, salary, etc. The data is stored in a DataTable variable.

* The For Each Row activity is used to loop through the rows of the DataTable variable. For each row, a new transaction item is created using the Add Queue Item activity. This transaction item contains the employee data.

* After creating the transaction item, the project moves to the End Transaction state. In this state, the transaction item status is checked. If the transaction item is successful, the project moves to the next row in the DataTable. If the transaction item fails, the project retries the transaction item until it succeeds.

* Once all the rows in the DataTable have been processed, the project moves to the End Process state. In this state, any necessary cleanup actions are performed, and the project ends.

* The project is then published to Orchestrator. A new process is created in Orchestrator, and the published project is associated with this process.

* A new queue is created in Orchestrator, and the necessary settings such as queue name, description, and transaction priority are configured.

* The project is executed in Orchestrator, and the employee data is loaded into the queue. The queue can then be processed by other projects such as the Performer project to perform further actions on the employee data.


Overall, the Dispatcher project in UiPath is a simple yet powerful way to load data into an Orchestrator queue. It can be customized further to fit the specific requirements of the application.

### Installation Steps for Performer Project:

1. Open UiPath Studio and create a new project.
2. In the "New Project" window, select the "Robotic Enterprise Framework" template and click "Create".
3. In the "Create a new REFramework project" window, give your project a name and select the "Dispatcher-Performer" option.
4. Click "Create" to create the project.
5. In the "Solution Explorer" panel, expand the "Data" folder and open the "Config.xlsx" file.
6. Update the values in the "Settings" sheet with the appropriate values for your environment. Make sure to include the Orchestrator URL, robot credentials, and queue name.
7. Save the "Config.xlsx" file and close it.
8. In the "Solution Explorer" panel, expand the "Main" folder and open the "Main.xaml" file.
9. Modify the "Init State" and "Get Transaction Data" sequences to match the specific requirements of your application.
10. Modify the "Process State" sequence to process the transactions retrieved from the queue.
11. Modify the "End Process" sequence to perform any necessary cleanup actions.
12. Save and publish the project to UiPath Orchestrator.
13. Create a new process in UiPath Orchestrator and associate it with the published project.
14. Create a new queue in UiPath Orchestrator and configure it with the appropriate settings.
15. Run the project in UiPath Orchestrator and monitor the queue for transactions.

Here are some additional details on a few of the steps:

In Step 9, you would modify the "Get Transaction Data" state to retrieve the transaction items from the queue.

In Step 10, you would modify the "Process State" to perform actions on the transaction item data, such as updating employee records or generating reports.

In Step 12, you would publish the project to UiPath Orchestrator by selecting "Publish" from the "Project" menu in UiPath Studio. You would then select the appropriate Orchestrator environment and configure the package settings.

In Step 14, you would create a new queue in UiPath Orchestrator by selecting "Queues" from the "Automations" menu. You would then select "New Queue" and configure the necessary settings such as queue name, description, and transaction priority.

In Step 15, you would run the project in UiPath Orchestrator by selecting the process and clicking "Start Job". You would then monitor the queue for transactions and verify that the project is performing the necessary actions on the data.

That's it! Your Performer project in the RE Framework is now installed and ready to use. You can customize it further to fit the specific requirements of your application.



### Conclusion
The Dispatcher-Performer model using the RE Framework in UiPath is a powerful automation solution for bulk offer letter generation. The Dispatcher project loads employee data into an Orchestrator queue, while the Performer project retrieves the data from the queue, generates the offer letters, and sends them to the respective employees.

The RE Framework provides a standard structure and workflow for building scalable, reliable, and maintainable automation projects. It includes built-in error handling, logging, and retry mechanisms, which make it easier to develop and manage complex automation processes.

By using the Dispatcher-Performer model with the RE Framework, organizations can significantly reduce the time and effort required to generate offer letters for a large number of employees. This results in faster hiring cycles, increased productivity, and reduced operational costs.

Overall, the Dispatcher-Performer model using the RE Framework is an excellent choice for automating bulk offer letter generation and other similar business processes.
