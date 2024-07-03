# Create-a-Database-and-Tables-using-Athena

## Introduction to Amazon Athena
* What is Amazon Athena?
Amazon Athena is an interactive query service that allows you to analyze data in Amazon Simple Storage Service (Amazon S3) using standard SQL. Athena is serverless, so there's no infrastructure to manage, and you can start querying immediately. You simply point Athena at your data stored in Amazon S3, define your schema, and start querying using standard SQL. Athena scales automatically—executing queries in parallel—so results are fast, even with large datasets and complex queries.

* How Can Amazon Athena Be Used?
Amazon Athena can be used for various use cases, including:

- Log Analysis: Analyze logs from web applications, mobile applications, or any other service where logs are generated. For example, you can query Apache access logs stored in S3.
- Data Lake Analytics: Query data stored in your data lake without the need for loading or ETL processes. This is useful for data exploration and ad-hoc querying.
- Business Intelligence: Integrate Athena with business intelligence tools like Amazon QuickSight to visualize data and generate reports.
- Big Data Processing: Combine Athena with other AWS big data services like AWS Glue, Amazon Redshift, and Amazon EMR for comprehensive data processing workflows.
- Security Analysis: Analyze security logs and generate reports to monitor security posture and detect anomalies.
- Cost Management: Query AWS Cost and Usage Reports stored in S3 to analyze spending patterns and optimize costs.
* Integration with Other AWS Services
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

2. Select Your Bucket:

* Click on the Buckets menu on the left of the screen.
* Select the radio button in front of the bucket named "<ID>myawsticketdata" (Refer to S3 Repository to create this bucket).
* Click on the Copy ARN button to copy the ARN of the bucket.

#### Step 3: Create a Database and Query with Athena
1. Navigate to Athena:

In the AWS Management Console, use the Services menu under Analytics to select Athena or search for Athena in the search box.

2. Set Up Query Result Location:

* Click on the Query Editor.
* Notice the message “Before you run your first query; you need to set up a query result location in Amazon S3”.
* Click on the Settings tab, then click on the Manage button.
* Refer to the ARN of the bucket you copied above. In the Location of Query Result, enter your bucket name prefixed with S3:// and ending with a /.
* Enter your Account ID in the ‘Expected Bucket Owner’ field and click Save.

3. Create a Database:

* Select the Editor tab and execute the following SQL command to create a database:

4. Create Tables:

* On the left-hand side of the screen in the Data panel, select the drop-down arrow next to Create beside Tables and View.
* Select S3 bucket data under the menu Create a table from the data source.

5. Create allevents Table

* Data Format:

* Change the Data format to Text File with Custom Delimiters and enter a pipe | as the field terminator.
* Clear the rest of the fields in the Data Format section.

6. Add Columns:
* Select the Bulk add columns button.
* Enter the following column names and data types:

* Click Add.

7. Create Table:

* Review the create table statement generated in the Preview table query section.
* Select Create table to execute the query.

8. Create Other Tables
* Follow the same steps to create the remaining tables (allusers, etc.) using the provided data files and appropriate column names and data types.
