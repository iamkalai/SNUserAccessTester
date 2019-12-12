# **SNUserAccessTester**

## Description

**_A ServiceNow Application that lets you test the access of a user_**

ServiceNow is a highly customizable application with numerous user personas, roles and their specific accesses.

- Have you ever needed to find what level of access does a user have in ServiceNow? 
- Have you ever needed to find what all tables can be accessed with a given role?
- This application will allow you to test your instance and find out what table access does a user have in your instances. 

The setup is extremely simple and the updateset creates a new application called '**Access Testing**'. The application uses ATF to determine the access and hence ATF should be enabled in your instance before you can use this application. 

![User Access Tester Application](https://github.com/iamkalai/SNUserAccessTester/blob/master/doc/images/user_access_tester_.png)

Follow the below steps after installing the updateset.

- Open the ATF test called '**Access Test**' which can be found under the new Application '**Access Testing**'. 
- Define the user you want to test the access for in 'Test Run Data Sets' related list along with its persona.
- Run the test. 
- After the test completes running (which is quick), the results of the test are documented in Access Test Results (u_access_test_results) table. The application can be found under the new application.
- The application also creates a new property called **access.test.parameters**. The property uses JSON object and defines the filter that you want to use, to narrow down the tables in your instances that you want the access test to be run against. The property also contains a parameter called excluded_tables_prefix, which will allow you to exclude system tables from the user access testing.
- You can extend the application and add as many user personas you want. Add the corresponding personas to the choice list of persona field on Access Test Results table and the choice list of Persona parameter in **Access Test** (ATF Test).

### Installation

- Install the updateset found in **dist** folder. Installing the updateset will create a new application along with modules for easy accessibility.

**Note**: The application is still in its infancy and might give false positives results like if there are scripted ACLs which restricts read access based on who is the creator of record, the access test might ignore that and give false results.