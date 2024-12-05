- [Monitoring and Alerting for AWS EC2 Instance](#monitoring-and-alerting-for-aws-ec2-instance)
  - [Monitoring EC2 instance](#monitoring-ec2-instance)
  - [Monitoring EC2: Key Features](#monitoring-ec2-key-features)
    - [**CloudWatch Alarms**](#cloudwatch-alarms)
  - [CloudWatch metrics and alarms for AWS EC2](#cloudwatch-metrics-and-alarms-for-aws-ec2)
  - [Setting Up CloudWatch Alarms](#setting-up-cloudwatch-alarms)
    - [1. Navigate to CloudWatch Console](#1-navigate-to-cloudwatch-console)
    - [2. Select Metrics](#2-select-metrics)
  - [Configuring the Alarm](#configuring-the-alarm)
    - [**1. Select Metric**](#1-select-metric)
    - [**2. Create Alarm**](#2-create-alarm)
  - [Configuring Actions for the Alarm](#configuring-actions-for-the-alarm)
    - [**1. Notifications**](#1-notifications)
    - [**2. Auto Scaling**](#2-auto-scaling)
    - [**3. EC2 Actions**](#3-ec2-actions)
  - [Finalising the Alarm](#finalising-the-alarm)
    - [**1. Set Conditions**](#1-set-conditions)
    - [**2. Create IAM Role**](#2-create-iam-role)
    - [**3. Create Alarm**](#3-create-alarm)
  - [Monitoring the Alarm](#monitoring-the-alarm)
- [AWS EC2 System Checks and Metrics](#aws-ec2-system-checks-and-metrics)
  - [Types of Status Checks](#types-of-status-checks)
    - [**1. System Status Checks**](#1-system-status-checks)
    - [**2. Instance Status Checks**](#2-instance-status-checks)
  - [Monitoring Status Checks](#monitoring-status-checks)
  - [Important Metrics for EC2 Instances](#important-metrics-for-ec2-instances)
    - [**1. CPU Utilisation**](#1-cpu-utilisation)
    - [**2. Disk Read Ops and Disk Write Ops**](#2-disk-read-ops-and-disk-write-ops)
    - [**3. Network In/Out**](#3-network-inout)
    - [**4. Status Check Failed**](#4-status-check-failed)
  - [Viewing Metrics](#viewing-metrics)
  - [Custom Metrics for EC2](#custom-metrics-for-ec2)
    - [**1. Publishing Custom Metrics**](#1-publishing-custom-metrics)
    - [**2. Viewing Custom Metrics**](#2-viewing-custom-metrics)
    - [**3. Using Custom Metrics**](#3-using-custom-metrics)
  - [Custom Metrics for AWS EC2](#custom-metrics-for-aws-ec2)
    - [Custom Metrics in AWS CloudWatch](#custom-metrics-in-aws-cloudwatch)
    - [Creating an IAM Role](#creating-an-iam-role)
    - [Launching a New EC2 Instance](#launching-a-new-ec2-instance)
    - [Connecting to the EC2 Instance](#connecting-to-the-ec2-instance)
    - [Downloading and Running Perl Scripts](#downloading-and-running-perl-scripts)
      - [Installing Mandatory Perl Packages](#installing-mandatory-perl-packages)
      - [Downloading and Running Perl Scripts](#downloading-and-running-perl-scripts-1)
  - [Push Custom Metrics from AWS EC2 to AWS CloudWatch](#push-custom-metrics-from-aws-ec2-to-aws-cloudwatch)
    - [Important Files and Their Functions](#important-files-and-their-functions)
      - [mon-put-instance-data.pl](#mon-put-instance-datapl)
      - [mon-get-instance-stats.pl](#mon-get-instance-statspl)
      - [creds-template](#creds-template)
    - [Running Perl Scripts](#running-perl-scripts)
      - [Execution](#execution)
      - [Viewing Metrics](#viewing-metrics-1)
      - [Automating Metric Collection](#automating-metric-collection)


# Monitoring and Alerting for AWS EC2 Instance

## Monitoring EC2 instance
- AWS EC2 stands for Elastic Cloud Compute
- EC2 is one of the key IaaS Services available on AWS
- EC2 provides a variety of key metrics out of the box for free
- AWS EC2 basic metrics provide metrics at 5 minute interval
- Advanced metrics is available at 1 min interval for an extra charge 


## Monitoring EC2: Key Features  
### **CloudWatch Alarms**

- **AWS CloudWatch** can track various standard metrics for EC2 instances.  
- **AWS CloudWatch** can also monitor custom metrics for AWS EC2 instances.  
- **AWS CloudWatch alarm actions** can automatically stop, terminate, reboot, or recover EC2 instances.  
- **Two key status checks** for AWS EC2 are provided for each instance.


## CloudWatch metrics and alarms for AWS EC2

## Setting Up CloudWatch Alarms

### 1. Navigate to CloudWatch Console
- Search for **"CloudWatch"** in the AWS Management Console.
- Click on the **CloudWatch** entry to access the dashboard.

### 2. Select Metrics
- Navigate to the **Metrics** section in the CloudWatch dashboard.
- Choose **EC2** and select **Per Instance Metrics** to view individual metrics for each EC2 instance.
- Filter metrics by the specific **EC2 instance ID**.

---

## Configuring the Alarm

### **1. Select Metric**
- Choose the **CPU Utilisation** metric for the EC2 instance.
- CPU Utilisation measures the percentage of allocated EC2 compute units currently in use.

### **2. Create Alarm**
- Navigate to the **Alarms** menu and click **Create Alarm**.
- Select the specific per-instance metric (e.g., **CPU Utilisation**).
- Provide a name for the alarm (e.g., `Test Alarm`) and a description.
- Set the threshold for the alarm (e.g., **0% CPU utilisation**) to trigger the alarm quickly for testing or demonstration purposes.

---

## Configuring Actions for the Alarm

### **1. Notifications**
- Use **Amazon SNS** to send notifications via email, SMS, or mobile push to operational staff.

### **2. Auto Scaling**
- Integrate CloudWatch alarms with EC2 Auto Scaling to automatically scale instances.
  - **Example:** Add an instance to the Auto Scaling group when **CPU Utilisation** exceeds 60%.

### **3. EC2 Actions**
- Configure actions like stopping, starting, rebooting, or terminating EC2 instances.
  - **Example:** Stop the instance when **CPU Utilisation** reaches 0%.

---

## Finalising the Alarm

### **1. Set Conditions**
- Define the period (e.g., 1 minute) and the number of consecutive periods for the threshold to trigger.

### **2. Create IAM Role**
- Check the box to create an IAM role, allowing CloudWatch to access EC2 services.

### **3. Create Alarm**
- Click **Create Alarm** to complete the setup.

---

## Monitoring the Alarm

- **Alarm State:**
  - The alarm state changes to **"ALARM"** when the threshold is breached.
- **Instance State:**
  - The EC2 instance state changes based on the configured action (e.g., stopping the instance).

---

# AWS EC2 System Checks and Metrics

## Types of Status Checks

### **1. System Status Checks**
- Monitors the physical hardware and infrastructure behind EC2 instances.
- **Examples of Failures:**
  - Loss of network connectivity.
  - Loss of system power.
  - Hardware issues.
- **Actions:**
  - Terminate and relaunch instances to migrate to healthy hardware.

### **2. Instance Status Checks**
- Monitors the software and network configuration of individual EC2 instances.
- **Examples of Failures:**
  - Failed system status checks.
  - Incorrect networking or startup configuration.
  - Exhausted memory or corrupted file systems.
  - Incompatible kernel versions.
- **Actions:**
  - Reboot the instance or make configuration changes to resolve issues.

---

## Monitoring Status Checks

- **Frequency:** Status checks are performed every minute.
- **Results:** Each status check returns either a **pass** or **fail** status.
- **Viewing Status Checks:**
  - View results directly in the **EC2 Console** under the **Monitoring tab**.

---

## Important Metrics for EC2 Instances

### **1. CPU Utilisation**
- Measures the percentage of allocated EC2 compute units in use.

### **2. Disk Read Ops and Disk Write Ops**
- Measures completed read/write operations from all instance store volumes.

### **3. Network In/Out**
- Measures the number of bytes received or sent across all network interfaces.

### **4. Status Check Failed**
- Indicates whether the instance has passed both system and instance status checks:
  - **Value 0:** Both status checks passed.
  - **Value 1:** One or both status checks failed.

---

## Viewing Metrics

1. **EC2 Console:**
   - View metrics for individual EC2 instances in the **Monitoring tab**.
2. **CloudWatch Metrics Section:**
   - Analyze detailed metrics in the **CloudWatch dashboard**.

---

## Custom Metrics for EC2

### **1. Publishing Custom Metrics**
- Use the AWS CLI or API to publish application-specific custom metrics.
  - **Example Command:**
    ```bash
    aws cloudwatch put-metric-data --namespace "CustomMetrics" --metric-name "RequestCount" --value 10
    ```

### **2. Viewing Custom Metrics**
- Navigate to the **CloudWatch Metrics** section to view custom metrics.
- Use statistical graphs to analyze trends and performance.

### **3. Using Custom Metrics**
- Create alarms for custom metrics in CloudWatch to trigger notifications or automated actions.

---


## Custom Metrics for AWS EC2
Overview: 
- Track specific metrics for EC2 instances not provided by CloudWatch out of the box.
- Example: Monitor memory consumption of EC2 instances.

### Custom Metrics in AWS CloudWatch
- **Open Monitoring Platform**: CloudWatch allows the addition of custom metrics for AWS cloud infrastructure.
- **Limited Default Metrics**: Out-of-the-box, CloudWatch provides a limited number of metrics for EC2 instances.
- **Diverse EC2 Configurations**: EC2 instances may have different operating systems, runtime libraries, scripts, and application domains.
- **Custom Metrics**: Necessary to track specific metrics to ensure applications are working correctly.

### Creating an IAM Role
- Enable EC2 instances to report custom metrics to CloudWatch.
Steps:

1. Navigate to the **IAM management console**.
2. Click on "Roles" and then "Create New Role".
3. **Name** the role (e.g., custom metrics role).
4. Choose **AWS Service role** type and **Amazon EC2**.
5. Attach a custom policy with necessary permissions:
   - cloudwatch:PutMetricData
   - cloudwatch:GetMetricStatistics
   - cloudwatch:ListMetrics
   - ec2:DescribeTags
6. **Review** and **create** the role.


### Launching a New EC2 Instance
Steps:
1. Navigate to the EC2 Management Console
    - Log in to the [AWS Management Console](https://aws.amazon.com/console/).
   - Search for **EC2** in the search bar and select **EC2**.
2. Launch an Instance
   - Click on **Launch Instance**.

3. Select Amazon Linux AMI
   - Choose **Amazon Linux AMI** as the operating system for the instance.

4. Choose Instance Type
   - Select the instance type:
     - **T2 Micro** (Free tier eligible for small workloads).


5. Assign the IAM Role
   - Under the **IAM Role** section, select the previously created IAM role (e.g., `CustomMetricsRole`).

6. Configure Instance Details
   - Specify the number of instances and other configurations as required.
   - Add networking settings, such as VPC, subnet, and security groups.


7. Add Storage**
   - Configure storage for the instance:
     - Add the desired size of root volume (e.g., 8 GiB).

8. Add Tags
   - Add tags to identify your instance (e.g., `Key: Name`, `Value: CustomMetricsInstance`).

9. Create a New Key Pair
  - Select **Create a new key pair**.
  - Name the key pair and download it to your local machine (e.g., `custom-metrics-key.pem`).

10. Launch the Instance
    - Review all configurations and click **Launch**.
    - The instance will begin the initialization process.



### Connecting to the EC2 Instance
Steps:

1. Connect to the EC2 instance via SSH.
2. Install mandatory Perl packages using yum install command.


### Downloading and Running Perl Scripts
#### Installing Mandatory Perl Packages
Steps:
1. Update the Package Manager
    ```bash
    sudo yum update -y
    ```

2. Install Perl and Required Packages
    ```bash
    sudo yum install -y perl
    ```


#### Downloading and Running Perl Scripts
Objective:

- Publish custom memory-related metrics to CloudWatch.

Steps:
1. Download Perl Scripts
    ```bash
    curl https://aws-cloudwatch.s3.amazonaws.com/downloads/CloudWatchMonitoringScripts.zip -O
    # Use the curl command to download the CloudWatch monitoring scripts
    ```


2. Unzip the Downloaded Scripts
   1. Unzip the downloaded file
        ```bash
            unzip CloudWatchMonitoringScripts.zip
        ```
    2. Move to the extracted directory:
        ```bash
        cd aws-scripts-mon
        ```


3.  Key Files in the Directory
    1. mon-get-instance-stats.pl
        - Used to retrieve instance statistics.
    2. mon-put-instance-data.pl
        - Publishes custom metrics, such as memory usage, to CloudWatch.

4. **Provide AWS credentials** if IAM role is **not used** (not needed in this demonstration).


## Push Custom Metrics from AWS EC2 to AWS CloudWatch
### Important Files and Their Functions
#### mon-put-instance-data.pl
- Collects system metrics on an AWS EC2 instance (e.g., memory swap, disk space utilisation).
- Sends the collected metrics to Amazon CloudWatch.

#### mon-get-instance-stats.pl
- Queries Amazon CloudWatch.
- Displays the most recent utilisation statistics for the EC2 instance on which the script is executed.

#### creds-template
- Template for credentials storing access key ID and secret access key.
- Needed only if the AWS EC2 instance does not have the necessary IAM permissions to communicate with AWS CloudWatch.



### Running Perl Scripts
#### Execution
- Run the Perl script to collect memory-related metrics and send them to CloudWatch.
  ```bash
  ./mon-put-instance-data.pl --mem-util --mem-used --mem-avail
  ```
- Confirmation message: "Successfully reported metrics to CloudWatch" with a reference number.
    ```css
    Successfully reported metrics to CloudWatch
    ```
#### Viewing Metrics
- Navigate to AWS CloudWatch management console.
- Switch to the metrics section and click on "All" to view all metrics.
- New category "Linux System" for custom metrics.
Metrics available: memory utilisation, memory available, and memory used.


#### Automating Metric Collection
**Issue**:
- Running the script manually is not ideal for regular data collection.

**Solution**:
- Schedule the script to run regularly using a cron job.


**Setting Up Cron Job**:
- Execute the command `crontab -e` to open crontab.
- Add a new command to run the script every five minutes.
    ```bash
    */5 * * * * /path/to/mon-put-instance-data.pl --mem-util --mem-used --mem-avail --disk-space-util --disk-path=/ --disk-space-avail --disk-space-used
    ```
- Save and exit crontab.
- Verify Cron Job:
    ```bash
    crontab -l
    ```