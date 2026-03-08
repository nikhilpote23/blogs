---
title: Autolaunched Flows
date: 2021-10-25
categories: [Salesforce, Admin]
tags: [Salesforce, Admin, Flows, github, blogging]
slug: autolaunched-flows
description: Ultimate guide to Salesforce Autolaunched Flows with business scenarios and implementation steps.
---

# Autolaunched Flows in Salesforce

## Overview

As per the latest update from Dreamforce 2K21, Salesforce will retire **Workflow** and **Process Builder** after 2023. Flows are now the recommended automation tool.

Autolaunched Flows allow you to define background processes without user interaction.

---

## Autolaunched Flow (No Trigger)

* Invoked by **Apex classes**, **Process Builder**, or **REST API**.
* Runs automatically based on conditions.
* Provides abstraction for complex background processes.

**Business Scenario:**

Marvel Industries wants to automate Opportunity handling:

1. When a new Opportunity is created with type "New Customer":

   * Update Opportunity stage to **Qualification**.
   * Create a task for the Sales Rep.
   * Send a welcome email to the customer.

**Solution Steps:**

1. Create an **Email Alert** with a "Welcome Customers" template.
2. Create an **Autolaunched Flow**:

   * Add a **record variable** (input) to get Opportunity from Process Builder.
   * Use **Update Records** to set Opportunity stage.
   * Create a **Task** with Due Date, Assigned To, Related To.
   * Add an **Action** to send the Email Alert.
3. Debug, Save, and **Activate** the flow.
4. Create a **Process Builder** on Opportunity:

   * Start process only when a record is created.
   * Criteria: Opportunity type = New Customer.
   * Action: Call the Autolaunched Flow.

---

## Autolaunched Flow (Scheduled Flow)

* Runs at a **specified time and frequency** (once, daily, weekly).
* Can process **batches of records**.
* Access record values via `$Record` global variable.

**Business Scenario:**

Marvel Industries wants to send weekly feedback emails to all customers.

**Solution Steps:**

1. Create a **Scheduled Flow**:

   * Start date/time: Today
   * Frequency: Weekly
   * Object: Account
   * Condition: Account name = Marvel
2. Use **Get Records** to fetch customers.
3. Use **Loop** to iterate customer list.
4. Assign emails to a **text variable collection**.
5. Use **Send Email** action with the email collection.
6. Debug, Save, and **Activate** the flow.

**Tip:** Always build **fault paths** for error handling.

---
