#SOASUITE 12 c Part 3: BAM Rules Human Workflow
Björn Naeslund R2M
bjorn.naeslund@r2m.se
http://github.com/bjornn


## Day 3 Lab Exercises: The credit rating application
A credit score is a number representing the creditworthiness of a person, the likelihood that person will pay his or her debts. A high credit score is better than a low.

Lenders, such as banks and credit card companies, use credit scores to evaluate the potential risk posed by lending money to consumers.

Our company maintains a rule base for credit score calculations (*business rules*-component).

For some especially tricky cases where not even the rule base is sufficient we need humans to make second opinion decisions. This will be managed by the *human workflow* -component.

We invoice our customers monthly on a per request basis and we want to have a real time view of how much money we earn. This will be implemented with *BAM* -Business Analysis and Monitoring.


## Lab 0: Setup the lab environment
### Objectives
To get everything set up properly in order to be able to focus on the main objectives of the labs.

### Instructions
* Check out the code from here: http://github.com/bjornn/SOASuite12c_Part3
<code>git clone  http://github.com/bjornn/SOASuite12c_Part3</code>

* Alternatively, if you don't want to use git,  download a zip archive of the entire codebase from here:
<code>http://github.com/bjornn/SOASuite12c_Part3/XXX.zip</code>


## Lab 1: Create (or extend) a Rule component
### Objectives
* Learn to navigate the Rule interface in JDeveloper.
* Learn how to implement your own rule base.

### Instructions
* Create a rule component from scratch (or, if pressed for time, reuse an existing rules component under <code>Application/LAB3_2</code> and extend it with a rule.)

####Create a rule composite from scratch
1. Create an empty composite
2. Copy Collaterals/CreditRating.xsd into the schemas directory.
3. Drag in a Business Rule Component from the Components palette.
4. In the configuration wizard, create an input and output that *both* point to the same xml-schema (the CreditRating.xsd imported in step 2).
5. Create a Rule Set.
6. Create General Rules.
7. Deploy the service to the application server.
8. (if time: test the rule base from the gui (designtime) by constructing unit tests)

#### Extend the exiting rule base
1. Import the project <code>Application/LAB3_2</code> into your current JDeveloper Application.
2. Inside the Rule component "CreditRatingRule" under the ruleset named "RuleSet1" Add one general rule that states the following:
<code>IF the uncertainty of the scoring is higher than 50<br/> THEN the credit score shall be lowered with 11 units.</code>


### Configurations

**Business Rule Configuration**

|Parameter|Value|
|----:|-----|
|Name|CreditRatingRule|
|Input|CreditRating.xsd/root|
|Output|CreditRating.xsd/root|
|Expose as Composite Service|YES|

**Rule Set**

|Parameter|Value|
|----:|-----|
|Name            |RuleSet1|
|Effective Date  |Always valid|
|Active          |Yes|

**General Rules**

|Parameter|Value|
|----:|-----|
|Name            |xxxx|
|Advanced Mode| No|
|Tree Mode| No|
|Rule Active| Yes|
|Logical| No|
|Priority| Medium|
|Effective Date  |Always Valid|
|IF Statement &lt;insert test&gt;|Boolean expression|
|Then statement &lt;insert action&gt;|modify root(XXXX) |


#### Rules
* r1
* r2
* r3
* r4

### Questions

* One of the rules exercises the RETE algorithm and motivates the use of a Rules engine. Which one and why?

* Can you see the code that is produced in the GUI in a way similar to the components that you have encountered so far?

* The rule interface has a lot more meta functionality (i.e. descriptions, aliases, lookups, lookup tables) than the interfaces previously encountered. Why is that do you think?

* The rule composite is intended to be used from a BPEL-process. By default two operations are created: one stateless and one stateful. When do you think you should use the one or the other?



## Lab 2: Connect a BPEL Process to an exising decision service
### Objectives
* Learn to integrate with a rule composite from BPEL and retrieve an answer from the rule dictionary.

### Instructions
A rule composite can be connected to a BPEL process Composite by exposing a SOAP interface from the rule composite and importing that same SOAP interface as a partner link in the BPEL Composite. I.e. a rule composite can be treated as any other Web Service.

A skeleton BPEL process is provided (a project named Application/LAB3_1_1). It can be used out of the box as a mock with all the logic hardcoded. In the BPEL process, placeholder activities (Empty activities are used for this purpose) has been inserted to indicate where the call for the Rule Base shall be made.




### Configurations

### Questions


## Lab 3: Add a human workflow to the Main BPEL Process
### Objectives
* Create a simple human workflow component and integrate it with a BPEL Process.
### Instructions
### Configurations
### Questions

## Lab 4: Add sensors to the main BPEL process
### Objectives
### Instructions
### Configurations
### Questions

## Lab 5: Configure a BAM process to consume events from the sensors added in the previous exercise

### Objectives

### Instructions
### Configurations
### Questions
