---
title: Autolaunched Flows
date: 2021-10-25
categories: Salesforce Admin
tags: [Salesforce, Admin, Flows, github, blogging]
---

# Autolaunched Flows

Autolaunched Flows
As per latest update from Dreamforce 2K21, Salesforce has announced that workflow and process builder will no longer be available after 2023. So, Flows are the future.

Autolaunched Flow(No Trigger)
As the name suggests Autolaunched Flows can be launched when invoked by Apex classes, process builders or REST API. These flows are launched automatically based on certain events or conditions. Autolaunched flows provide abstraction, as you can define the complex processes to be carried out in the background without a user knowing the details.

Business Scenario
Marvel Industries is focusing on improving their customer experience and wants to ensure whenever the new Opportunity arises with the type as a New Customer, 
Opportunity should be changed to the Qualification stage so that VP of sales can have a better understanding of the Sales process.
Task should be created for the Sales Rep who owns the opportunity to call the customer and get more details
Welcome email should be sent to the customer notifying the call is scheduled with Sales Rep

Solution
In order to solve the above requirements we would call an autolaunched flow using the Process builder whenever the new opportunity is created with type as New customer. This flow will update the Opportunity stage to Qualification, create a task for the Sales Rep and send a welcome email to the customer.

How should we implement it?
Create an email alert with Welcome Customers email template
Create an autolaunched flow
Create a record type variable with available for input to get the opportunity record from the Process builder
Create a data element of type Update records to update the Opportunity stage
Then create a task of type call and enter the details like Due date, Assigned to, Related to etc.
Create an action element to send an email alert created in step 1 and assign the Opportunity Id as a record
Debug(if required), Save and then Activate the flow
Create a Process builder on Opportunity
Select the Opportunity as an object and Start process as only when a record is created
Define a new criteria to check if the Opportunity type is New Customer
If yes, set an action to call the flow created in step 2

Action Time

Autolaunched Flow(Scheduled Flow)
As the name suggests these flows only run from specified time and frequency(once/ daily/ weekly) that the user sets. It provides Salesforce users an ability to run declarative logic on multiple records at a scheduled time. Yes, you heard it right; Schedule triggered flows can also run for a batch of records if the filter conditions are specified.

Little Insights 

Scheduled flows are bulkified and run for each record in the batch( 200 records per batch) and store all of the record’s field values in the $Record global variable. You can refer to the $Record global variable to access the record’s field values.
Monitor scheduled flows from the Setup -> Scheduled Jobs page.
The organisation’s default time zone is used for the scheduled start time.
The running user for scheduled flows is the Automated Process user.
To debug scheduled flows, set the debug log on the Automated Process entity type.
Business Scenario
Marvel Industries is focusing on improving their customer experience and wants to ensure their customers get the feedback email notification every week.

Solution
In order to solve the above requirements we would create a scheduled flow on the Account to send all the Marvel related customers a feedback email. 

How should we implement it?
Create an scheduled flow
Select the Flow start date and time with today's time and frequency as Weekly
Select object as an Account and add a condition to get only account with name as Marvel
Create a Get record element to get all the customers related to the Marvel account
Create a loop element to iterate through list of customers
Then create a variable resource, Customer emails of type text to capture all the customer emails 
Create an assignment element to add the each contacts email to the above list
Create an action element of type send email and select the resource into Email Addresses (collection)
Debug(if required), Save and then Activate the flow

Tip: Create an error handling strategy for your flow-based automations by building in fault paths

SEO Title:

An Ultimate Guide on Autolaunched Flows in Salesforce

Slug:

auto-launch-flows-
