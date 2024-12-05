- [Introduction to Monitoring and Alerting for AWS RDS](#introduction-to-monitoring-and-alerting-for-aws-rds)
  - [Introduction to AWS RDS](#introduction-to-aws-rds)
  - [Key Learning Objectives](#key-learning-objectives)
  - [Importance of Monitoring RDS](#importance-of-monitoring-rds)
  - [Monitoring Tools and Features](#monitoring-tools-and-features)
    - [CloudWatch Metrics](#cloudwatch-metrics)
    - [Events](#events)
    - [Database Logs](#database-logs)
  - [Practical Steps](#practical-steps)
    - [Viewing Metrics](#viewing-metrics)
    - [Setting Up Event Notifications](#setting-up-event-notifications)
    - [Accessing Logs](#accessing-logs)
- [Monitoring AWS RDS Metrics](#monitoring-aws-rds-metrics)
  - [Core Metrics for AWS RDS](#core-metrics-for-aws-rds)
    - [CPU Utilisation](#cpu-utilisation)
    - [Database Connections](#database-connections)
    - [Freeable Memory](#freeable-memory)
    - [Free Storage Space](#free-storage-space)
  - [IOPS and Latency Metrics](#iops-and-latency-metrics)
    - [Read IOPS and Write IOPS](#read-iops-and-write-iops)
    - [Read Latency and Write Latency](#read-latency-and-write-latency)
  - [Monitoring and Alarms](#monitoring-and-alarms)
    - [Viewing Metrics](#viewing-metrics-1)
  - [Creating Alarms](#creating-alarms)
  - [Practical Steps](#practical-steps-1)
    - [Accessing Metrics](#accessing-metrics)
    - [Setting Up Notifications](#setting-up-notifications)
    - [Importance of Monitoring](#importance-of-monitoring)
  - [AWS RDS Events](#aws-rds-events)
    - [Monitoring Key Metrics](#monitoring-key-metrics)
    - [Key Metrics to Monitor](#key-metrics-to-monitor)
    - [CloudWatch Events for RDS](#cloudwatch-events-for-rds)
    - [Setting Up Event Subscriptions](#setting-up-event-subscriptions)
    - [Verifying Event Notifications](#verifying-event-notifications)

# Introduction to Monitoring and Alerting for AWS RDS

## Introduction to AWS RDS
- **AWS RDS**: Stands for **Relational Database Service**.
- **Type**: Platform as a Service (PaaS).
- **Purpose**: Provides **scalable** and **managed** relational database **services**.
- **Supported Databases**: MySQL, PostgreSQL, SQL Server, Oracle, and Aurora (AWS's optimised MySQL clone).


## Key Learning Objectives
- **Familiarise with AWS RDS**: Understand what RDS is and its role.
- **Key Metrics**: Learn about important metrics like CPU utilisation, database connections, and free memory.
- **Monitoring and Alerts**: Set up alarms and notifications to ensure high availability and performance.

## Importance of Monitoring RDS
- Databases are **crucial** for **application functionality** and user **experience**.
- **High Availability**: RDS can automatically failover to a healthy replica in case of failures.
- **Monitoring Tools**: AWS and CloudWatch provide various tools to monitor and manage RDS instances.



## Monitoring Tools and Features
### CloudWatch Metrics
- **Basic Metrics**: Available every 5 minutes.
- **Detailed Metrics**: Available every 1 minute.
- **Example Metrics**: CPU utilisation, database connections, free memory.
### Events
- It keeps **track of changes** and **actions** related to DB instances, snapshots, security groups, and parameter groups.
- **Notifications**: Set up event subscriptions to get notified via email, SMS, etc.
### Database Logs
- **Access**: View logs by navigating to the detailed view of the database instance.
- **Types of Logs**: Error log, slow query log, general log (varies by database engine).
- **Real-Time Monitoring**: Logs refresh every 5 seconds for real-time insights.
- **Download Logs**: Option to download logs for further analysis.


## Practical Steps
### Viewing Metrics
1. Navigate to the **AWS console** and select the "RDS dashboard".
2. Select the **database instance** and click on "Show Monitoring" to view metrics.
### Setting Up Event Notifications
1. Use the "Events" feature to track changes and set up notifications.
### Accessing Logs
1. Scroll down to the "Logs" section in the detailed view of the database instance.
2. Click on the **log type** to view or download.


# Monitoring AWS RDS Metrics
## Core Metrics for AWS RDS
### CPU Utilisation
- Measures the percentage of CPU used by the server running the database.
### Database Connections
- Shows the number of active connections to the RDS instance.
### Freeable Memory
- Indicates the amount of RAM available.
### Free Storage Space
- Shows the amount of available storage space.
  

## IOPS and Latency Metrics
### Read IOPS and Write IOPS
- Measures the number of input/output operations per second.
- High IOPS usage can indicate potential overload and slower responses.


### Read Latency and Write Latency
- Tracks the average **time taken** per **disk input/output** operation.
- High latency values indicate performance degradation.


## Monitoring and Alarms

### Viewing Metrics
1. Navigate to the **AWS console** and select the **RDS instance**.
2. Go to the "Alarm and Monitoring" section to view key metrics and recent events.


## Creating Alarms
1. Click on "Create Alarm" to set up **notifications** for specific metrics.
     - Example: Set an alarm for CPU utilisation with a threshold value.
2. **Configure** the alarm to send **notifications** to an email address or distribution list.


## Practical Steps
### Accessing Metrics
1. Select the **RDS instance** and click on "Show Monitoring" for detailed metrics.
2. View metrics like CPU utilisation, DB connections, freeable memory, read IOPS, and write IOPS.


### Setting Up Notifications
1. Use CloudWatch to create alarms and set up notifications for important metrics.
    - Example: Create an alarm for CPU utilisation and configure it to send email notifications.  

### Importance of Monitoring
- **Real-Time Insights**: Monitoring provides a real-time view of the database's health and performance.
- **Proactive Management**: Setting up alarms helps in taking corrective actions before issues escalate.
- **Avoiding Downtime**: Timely notifications about critical metrics like free storage space can prevent unexpected downtime.


## AWS RDS Events

### Monitoring Key Metrics
- For **mission-critical databases**, it's essential to monitor key metrics and set up alarms to maintain database **health** and **minimise downtime**.
- **Operational Policies**: Implement policies to respond to alarms promptly to **ensure consistent user experience**.

### Key Metrics to Monitor
- **Resource Utilisation**: Track CPU, memory, and storage usage.
- **System Errors**: Monitor for any errors that could affect database performance.
- **Accidental Termination**: Ensure instances are not accidentally terminated.
- **Cluster Health**: Monitor the health of database clusters.
- **Maintenance Windows**: Keep track of scheduled maintenance.
- **Query Logs**: Monitor logs for slow or problematic queries.
- **Instance-Level Metrics**: Track metrics specific to each database instance.
- **Resource Modification**: Monitor changes to database resources.


### CloudWatch Events for RDS

- CloudWatch events help **track configuration changes** and **important actions** within RDS instances.

**Event Retrieval**:
- **AWS Management Console**: Shows events from the past 24 hours.
- **AWS CLI/ API**: Retrieve events for up to the past 14 days.


### Setting Up Event Subscriptions
1. In the **AWS management console**, go to the "Events" menu.
2. Create **Event Subscription**:
   1. Click on "Event Subscriptions" and then "Create Event Subscription".
   2. **Name** the subscription (e.g., "event").
   3. Select the **target topic** (e.g., "my alerting admins").
   4. Choose the **source type** (e.g., instances).
   5. Select **event categories** (e.g., availability, backup, configuration change).
   6. Select the **instances to monitor**.
   7. Click "Create" to finalise the subscription.

### Verifying Event Notifications

- **Check Email Inbox**: Look for confirmation emails about the new event subscription.
- **Trigger an Event**: Manually reboot the database instance to generate events.
- **View Events**: Check the Events and Logs screen in the AWS console to see logged events.
- **Receive Notifications**: Confirm that notifications are received for the triggered events.

