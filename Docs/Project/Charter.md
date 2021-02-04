# Project Charter

## Problem Description

* What is the data science problem we are solving, why is it important?

## Scope
* What data science solutions are we trying to build?
* What will we do?
* How is it going to be consumed by the customer?

## Personnel
* Who are on this project:
	* Microsoft:
		* Project lead
		* PM
		* Data scientist(s)
		* Account manager
	* Client:
		* Data administrator
		* Business contact
	
## Metrics
* What are the qualitative objectives? (e.g. reduce user churn)
* What is a quantifiable metric  (e.g. reduce the fraction of users with 4-week inactivity)
* Quantify what improvement in the values of the metrics are useful for the customer scenario (e.g. reduce the  fraction of users with 4-week inactivity by 20%) 
* What is the baseline (current) value of the metric? (e.g. current fraction of users with 4-week inactivity = 60%)
* How will we measure the metric? (e.g. A/B test on a specified subset for a specified period; or comparison of performance after implementation to baseline)

## Plan
* Phases (milestones), timeline, short description of what we'll do in each phase.

## Architecture
* Data
  * What data do we expect? Raw data in the customer data sources (e.g. on-prem files, SQL, on-prem Hadoop etc.)
* Data movement from on-prem to Azure using ADF or other data movement tools (Azcopy, EventHub etc.) to move either
  * all the data, 
  * after some pre-aggregation on-prem,
  * Sampled data enough for modeling 

* What tools and data storage/analytics resources will be used in the solution e.g.,
  * ASA for stream aggregation
  * HDI/Hive/R/Python for feature construction, aggregation and sampling
  * AzureML for modeling and web service operationalization
* How will the score or operationalized web service(s) (RRS and/or BES) be consumed in the business workflow of the customer? If applicable, write down pseudo code for the APIs of the web service calls.
  * How will the customer use the model results to make decisions
  * Data movement pipeline in production
  * Make a 1 slide diagram showing the end to end data flow and decision architecture
    * If there is a substantial change in the customer's business workflow, make a before/after diagram showing the data flow.

## Communication
* How will we keep in touch? Weekly meetings?
	* Currently running a Discord server which enables us to talk to each other very quickly and set up meetings as needed.
	* Discord chat functionality also allows us to chat about anything going on with the project at any time.
	* Github commit messages are an easy way of checking what work was done to prevent overlapping.
	* Jira task completions
* Who are the contact persons on both sides?
	* Project development contacts: Thuc Duong(tug98850@temple.edu), Dodge Hill(tuh33009@temple.edu), Jonathan Oberst(tug93898@temple.edu), Marinos Rrapaj(tuf61948@temple.edu)
	* Shareholder contacts: Abha Belorkar, Sam Black
