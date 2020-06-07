# **SN User Access Tester**

## Description

**_A ServiceNow Application that lets you test the access of a user on different ServiceNow tables._**

ServiceNow is a highly customizable application with numerous user personas, roles and their specific accesses.

- Have you ever needed to find what level of access does a user have in ServiceNow?
- Have you ever needed to find what all tables can be accessed with a given role?
- This application will allow you to test your instance and find out what tables to which a user has access to in your instance.

![User Access Tester Application](/doc/images/user_access_tester_.png)

### Installation

- Import and commit the updateset found in [**dist**](/dist) folder.
- **Dependency:** This requires that the [SNCommonLibraryFunctions](https://github.com/iamkalai/SNCommonLibraryFunctions) is already installed and available in the instance.

### Usage

- The updateset creates a new application called '**Access Testing**' and a record producer called **Access Tester**.
- Use **Access Tester** module to perform access related actions and view the access results using **Access Results** module.
  
- To find the access of a user, click _Access Tester_ module. Let the action be 'Find Access' and select the user, click submit. The job will be scheduled in background and will take few minutes to complete.
  
![Find Access](/doc/images/find_access_.png)

- If we are making large number of security changes and want to validate if the user access has changed, we can do so using _Compare Access_ option. Select two access results, pre (old results) and post making the changes (new results) and choose the action as 'Compare Access'. Submit the form to schedule access comparison. The job will be kicked off in the background and will take few minutes to complete.
- While comparison, if the system finds any tables in new results that are not in old results selected, such entries are added in the results and mentioned in the comments field automatically.
- In the comparison results, for columns create/update/read/delete, true indicates that the access has changed between 'old' and 'new' results selected. False indicates that the access remains same.

![Find Access](/doc/images/compare_access_.png)

- Access Test Results (u_access_test_results) are used to store both the access and access comparison results. The access result numbers are prefixed with **ACC** and the comparison results are prefixed with **RACC**.

- The application also creates a new property called **access.test.parameters**. The property uses JSON object and defines the filter that you can use to narrow down the tables in your instances that you want the access search to be run against. The property also contains a parameter called excluded_tables_prefix, which will allow you to exclude system tables from the user access testing using prefixes (such as table name starting with sys, log, etc).

### License

GNU General Public License v3.0
