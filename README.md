# Create-Database-and-Tables-using-Athena

![](https://github.com/sujikathir/Create-a-Database-and-Tables-using-Athena/blob/main/source/Cover%20pic.png)

## Introduction to Amazon Athena

### What is Amazon Athena?
Amazon Athena is an interactive query service that allows you to analyze data in Amazon Simple Storage Service (Amazon S3) using standard SQL. Athena is serverless, so there's no infrastructure to manage, and you can start querying immediately. You simply point Athena at your data stored in Amazon S3, define your schema, and start querying using standard SQL. Athena scales automatically—executing queries in parallel—so results are fast, even with large datasets and complex queries.

### How Can Amazon Athena Be Used?
Amazon Athena can be used for various use cases, including:

- Log Analysis: Analyze logs from web applications, mobile applications, or any other service where logs are generated. For example, you can query Apache access logs stored in S3.

- Data Lake Analytics: Query data stored in your data lake without the need for loading or ETL processes. This is useful for data exploration and ad-hoc querying.

- Business Intelligence: Integrate Athena with business intelligence tools like Amazon QuickSight to visualize data and generate reports.

- Big Data Processing: Combine Athena with other AWS big data services like AWS Glue, Amazon Redshift, and Amazon EMR for comprehensive data processing workflows.

- Security Analysis: Analyze security logs and generate reports to monitor security posture and detect anomalies.

- Cost Management: Query AWS Cost and Usage Reports stored in S3 to analyze spending patterns and optimize costs.

### Integration with Other AWS Services
Amazon Athena integrates seamlessly with various AWS services to enhance its functionality and enable more comprehensive data analytics workflows:

- Amazon S3: The primary storage for data queried by Athena. S3 provides a scalable, durable, and secure location to store data.
  
- AWS Glue: AWS Glue can be used to catalog data in S3, making it easier for Athena to discover and query data. Glue also provides ETL capabilities to transform data before querying.
  
- Amazon QuickSight: A business intelligence service that can directly query data in Athena for visualization and reporting.

- AWS Lambda: Lambda can be used to trigger Athena queries based on events, automating data analysis workflows.

- Amazon Redshift: Data can be queried from Redshift and combined with S3 data in Athena to enable hybrid data analysis.

- Amazon CloudWatch: Athena query logs can be sent to CloudWatch for monitoring and alerting on query performance and errors.

- AWS IAM: IAM provides fine-grained access control to Athena resources, ensuring secure access to data.

## Detailed Explanation of the Assignment
### Objective

Create a database and associated tables using AWS Athena and further optimize the database using partitioning and bucketing. Execute queries against the database tables to retrieve the required data.

### Scenario:
	
You are an analyst in an organization that has a ticketing website that allows users to buy and sell tickets online for various events like sports, music concerts, and live shows. As an analyst, you can monitor and track the rate of success for the sellers, and identify the bestselling events, venues, and seasons. With the help of this data you, as an analyst, can provide incentives to frequent buyers and sellers. You can also use this data to run marketing campaigns and attract prospective users. Using the 7 different data files, your company wants you to create tables and views on this data and then query the data.

### Step-by-Step Guide
#### Step 1: Returning to the AWS Management Console
Login to the AWS Management Console: Use the login ID and password you used in the first assignment via this [link](https://aws.amazon.com/free/?all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free%20Tier%20Types=*all&awsf.Free%20Tier%20Categories=*all).

#### Step 2: Accessing Stored Data
1. Navigate to S3:

In the AWS Management Console, use the Services menu under Storage to select S3 or search for S3 in the search box.
![](https://github.com/sujikathir/Create-a-Database-and-Tables-using-Athena/blob/main/source/1.%20s3%20home.png)

2. Select Your Bucket:

* Click on the Buckets menu on the left of the screen.
* Select the radio button in front of the bucket named "<ID>myawsticketdata" (Refer to S3 Repository to create this bucket).
  
  ![](https://github.com/sujikathir/Create-a-Database-and-Tables-using-Athena/blob/main/source/2%20s3%20bucket.png)
  
* Click on the Copy ARN button to copy the ARN of the bucket.

#### Step 3: Create a Database and Query with Athena
1. Navigate to Athena:

In the AWS Management Console, use the Services menu under Analytics to select Athena or search for Athena in the search box.

![](https://github.com/sujikathir/Create-a-Database-and-Tables-using-Athena/blob/main/source/3.%20athena%20home.png)

2. Set Up Query Result Location:

* Click on the Query Editor.

![](https://github.com/sujikathir/Create-a-Database-and-Tables-using-Athena/blob/main/source/4.%20athena%20home.png)

![](https://github.com/sujikathir/Create-a-Database-and-Tables-using-Athena/blob/main/source/5.click%20query%20editor.png)

![](https://github.com/sujikathir/Create-a-Database-and-Tables-using-Athena/blob/main/source/6.query%20editor%20home.png)
  
* Notice the message “Before you run your first query; you need to set up a query result location in Amazon S3”.
* Click on the Settings tab, then click on the Manage button.

![](https://github.com/sujikathir/Create-a-Database-and-Tables-using-Athena/blob/main/source/7.%20settings%20-%20query%20editor.png)

* Refer to the ARN of the bucket you copied above. In the Location of Query Result, enter your bucket name prefixed with S3:// and ending with a /.
* Enter your Account ID in the ‘Expected Bucket Owner’ field and click Save.

3. Create a Database:

* Select the Editor tab and execute the following SQL command to create a database:
  
  ![](https://github.com/sujikathir/Create-a-Database-and-Tables-using-Athena/blob/main/source/9.%20query.png)

4. Create Tables:

* On the left-hand side of the screen in the Data panel, select the drop-down arrow next to Create beside Tables and View.

![](https://github.com/sujikathir/Create-a-Database-and-Tables-using-Athena/blob/main/source/10.%20data%20source.png)

* Select S3 bucket data under the menu Create a table from the data source.

![](https://github.com/sujikathir/Create-a-Database-and-Tables-using-Athena/blob/main/source/11.%20create%20table%20from%20s3%20data.png)

![](https://github.com/sujikathir/Create-a-Database-and-Tables-using-Athena/blob/main/source/12.%20choose%20existing%20db.png)

![](https://github.com/sujikathir/Create-a-Database-and-Tables-using-Athena/blob/main/source/13.%20browse%20s3%20db.png)

![](https://github.com/sujikathir/Create-a-Database-and-Tables-using-Athena/blob/main/source/14.%20choose%20dataset.png)

5. Create allevents Table

* Navigate to the Data Format section. Change the Data format to Text File with Custom Delimiters and enter a pipe | as the field terminator. Clear the rest of the fields in the Data Format section.

![](https://github.com/sujikathir/Create-a-Database-and-Tables-using-Athena/blob/main/source/15.%20field%20terminator.png)


6. Add Columns:
* Select the Bulk add columns button.

![](https://github.com/sujikathir/Create-a-Database-and-Tables-using-Athena/blob/main/source/16.%20bulk%20add%20columns.png)

* Enter the following column names and data types:

![](https://github.com/sujikathir/Create-a-Database-and-Tables-using-Athena/blob/main/source/17.%20columns%20names%20and%20meta%20data%20type.png)

* Click Add.

7. Create Table:

* Review the create table statement generated in the Preview table query section.

![](https://github.com/sujikathir/Create-a-Database-and-Tables-using-Athena/blob/main/source/18.%20check%20column%20name.png)

![](https://github.com/sujikathir/Create-a-Database-and-Tables-using-Athena/blob/main/source/19.%20preview%20table%20query.png)

Note: Table properties are the properties attached to the tables. Here the has_encrypted_data field is set to false, implying that the data is not encrypted. Serde is a data serialization format, and the property here implies that the data format should be pipe | delimited.


* Select Create table to execute the query.

![](https://github.com/sujikathir/Create-a-Database-and-Tables-using-Athena/blob/main/source/20.%20query%20generated%20and%20executed.png)

8. Create Other Tables
* Follow the same steps to create the remaining tables (allusers, etc.) using the provided data files and appropriate column names and data types.

![](https://github.com/sujikathir/Create-a-Database-and-Tables-using-Athena/blob/main/source/21.%20create%20users%20table.png)

![](https://github.com/sujikathir/Create-a-Database-and-Tables-using-Athena/blob/main/source/22.%20create%20category%20table.png)

![](https://github.com/sujikathir/Create-a-Database-and-Tables-using-Athena/blob/main/source/23.%20create%20venue%20table.png)

![](https://github.com/sujikathir/Create-a-Database-and-Tables-using-Athena/blob/main/source/24.%20create%20listing%20table.png)

![](https://github.com/sujikathir/Create-a-Database-and-Tables-using-Athena/blob/main/source/25.%20create%20dates%20table.png)

9. Creation of Sales Table
  
![](https://github.com/sujikathir/Create-a-Database-and-Tables-using-Athena/blob/main/source/26.%20creation%20of%20sales%20table.png)

![](https://github.com/sujikathir/Create-a-Database-and-Tables-using-Athena/blob/main/source/27.%20creation%20of%20sales%20table.png)

![](https://github.com/sujikathir/Create-a-Database-and-Tables-using-Athena/blob/main/source/28.%20creation%20of%20sales%20table.png)


#### Step 4: Optimizing a Database

Optimizing a database is about minimizing the query response time for a minimum of cost. We are going to compare query response times and the amount of data flow for loading the data using two different approaches. Athena determines the expense for running queries based on usage. Usage translates into the amount of data that is scanned. The next section will develop skills in optimizing the cost of performing cloud analytics queries.


1. Create Texas Users Table:

Execute the following SQL command to create a table for Texas users:
![](https://github.com/sujikathir/Create-a-Database-and-Tables-using-Athena/blob/main/source/29.%20filter%20state%20TX.png)

2. Upload Texas Users Data:

* Download the results of the query and save the file as texas_users.csv.
* Upload this file to the same S3 bucket.
  
![](https://github.com/sujikathir/Create-a-Database-and-Tables-using-Athena/blob/main/source/30.%20texas%20users%20csv.png)

![](https://github.com/sujikathir/Create-a-Database-and-Tables-using-Athena/blob/main/source/31.%20upload%20csv.png)

![](https://github.com/sujikathir/Create-a-Database-and-Tables-using-Athena/blob/main/source/32.%20create%20texas%20users%20table.png)

![](https://github.com/sujikathir/Create-a-Database-and-Tables-using-Athena/blob/main/source/33.%20query%20tx%20table.png)

3. Partitioned Data:

Create a partition for quarter = 4 by executing the following query:

![](https://github.com/sujikathir/Create-a-Database-and-Tables-using-Athena/blob/main/source/34.%20Query%20to%20partition.png)

#### Step 5: Create and Query Views
1. Create Views for Quarterly Sales:
   
![](https://github.com/sujikathir/Create-a-Database-and-Tables-using-Athena/blob/main/source/35.%20query%20for%20sales%20join%20date.png)

2. Create views for total quantity of tickets sold in quarters 1 and 4:
![](https://github.com/sujikathir/Create-a-Database-and-Tables-using-Athena/blob/main/source/36.%20query%20for%20tickets%20in%20q4.png)

![](https://github.com/sujikathir/Create-a-Database-and-Tables-using-Athena/blob/main/source/37.%20total%20sold%20for%20q4.png)

![](https://github.com/sujikathir/Create-a-Database-and-Tables-using-Athena/blob/main/source/38.%20total%20sold%20q1.png)

![](https://github.com/sujikathir/Create-a-Database-and-Tables-using-Athena/blob/main/source/39.%20q1.png)

![](https://github.com/sujikathir/Create-a-Database-and-Tables-using-Athena/blob/main/source/40.%20q4.png)

2. Join Views:

*Create a view that joins the data from these two queries:

![](https://github.com/sujikathir/Create-a-Database-and-Tables-using-Athena/blob/main/source/41.%20join%20query%20for%20q1%20and%20q4.png)

3. Query the View:

Execute the query:

![](https://github.com/sujikathir/Create-a-Database-and-Tables-using-Athena/blob/main/source/42.%20compare%20query.png)

### Conclusion
By following this step-by-step guide, you will have successfully created and optimized a database in AWS Athena, created tables and views, and executed queries to retrieve meaningful data insights. This assignment demonstrates the power and flexibility of AWS Athena for big data analytics, helping you leverage your data for better decision-making and strategic planning.
