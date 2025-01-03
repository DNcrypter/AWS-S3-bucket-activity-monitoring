
## 🍁AWS S3 bucket activity monitoring

[![MIT License](https://img.shields.io/badge/License-MIT-green.svg)](https://choosealicense.com/licenses/mit/)
        [![LinkedIn](https://img.shields.io/badge/LinkedIn-Profile-blue)](https://www.linkedin.com/in/nikhil--chaudhari/)
        [![Medium](https://img.shields.io/badge/Medium-Writeups-black)](https://medium.com/@nikhil-c)


## 🍁Problem 
After creating S3 bucket main challange is to monitor and record its performance and cost efficiency. 

## 🍁Solution 
* We’re using AWS cloudtrail service for monitoring S3 bucket logs.
* Also used Cloudwatch for log analysis and triggering alarms using Lambda fuctions.
* used SNS for notification sending on triggering alarms.


## Key metrics to monitor in AWS S3

When monitoring Amazon S3, there are several key metrics you should keep an eye on to ensure optimal performance, security, and cost management. These metrics can be divided into categories such as usage, performance, and security.

### ◉ Request metrics
#### 1) Get requests :
* Counts the number of GET requests made to S3.

#### 2) Put requests :
* Tracks the number of PUT requests made to S3.

#### 3) Delete requests :
* Counts the number of DELETE requests made to S3.

#### 4) List requests :
* Tracks the number of LIST requests made to S3.


### ◉ Security metrics
#### 1) Bucket policies
* Monitors changes to bucket policies to ensure they comply with security standards.

#### 2) Access control list (ACL) changes
* Tracks changes to ACLs on buckets and objects.

#### 3) Public access
* Monitors whether any buckets or objects are publicly accessible.


### ◉ Performance metrics
#### 1) First byte latency
* Measures the time it takes for the first byte of an object to be received from S3.

#### 2) Total request latency
* Tracks the total time taken for a request, from the moment it is made until the response is fully received.

#### 3) HTTP status codes
* Monitors the distribution of HTTP status codes returned by S3, such as 2xx (successful requests), 3xx (redirects), 4xx (client errors), and 5xx (server errors).


## AWS S3 monitoring using CloudTrial
### ◉ Creating a Trail in CloudTrail
##### 1) Sign in to the AWS Management Console and open the CloudTrail console.

##### 2) Create a trail:
* In the navigation pane, choose Trails, then Create trail.
* Enter a name for the trail.
* For Storage location, choose an existing S3 bucket or create a new one where the logs will be stored.


![img1]()

##### 3) Configure the trail settings:
* Under Management events, ensure that Read/Write events is selected based on your requirements.
* For Data events, select S3 and choose the specific S3 bucket you want to monitor. You can select All current and future S3 buckets to log events for all S3 buckets in the account or select specific buckets.
* Ensure that both Read events and Write events are selected to capture all types of access and changes.

![img1]() 

##### 4) Optional (but recommended) settings:
* Enable Log file validation for additional security.
* Enable CloudWatch Logs to stream CloudTrail logs to CloudWatch for real-time monitoring and alerting.

##### 5) Review and create the trail.

__Note :__ Ensure that the CloudTrail has the necessary permissions to log events to the S3 bucket. If not, configure the necessary bucket policy.


### ◉ Analyzing AWS S3 logs
Once CloudTrail is configured to log S3 bucket events, it's important to note that CloudTrail itself does not perform log analysis. Instead, you can analyze the logs using several methods:

#### 1) AWS CloudWatch Logs:

* If you enabled CloudWatch Logs integration, navigate to the CloudWatch console to access and search through the logs.
* Set up CloudWatch Alarms to receive notifications for specific events or anomalies detected in the CloudTrail logs.

#### 2) AWS Management Console:

* Navigate to the CloudTrail console and select Event history to view recent events.
* Utilize filters to narrow down to specific events related to your S3 bucket, such as ListBucket, GetObject, PutObject, etc.

#### 3) Third-party SIEM

The most effective way to monitor your entire AWS environment, and not just S3, would be to use a third-party SIEM solution that can integrate with your AWS environment. All it takes is one step: Configuring your AWS account, and you’re set to comprehensively monitor and manage your AWS resources.

