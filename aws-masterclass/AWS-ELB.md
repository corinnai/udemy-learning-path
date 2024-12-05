- [Introduction to Monitoring and Alerting for AWS ELB](#introduction-to-monitoring-and-alerting-for-aws-elb)
  - [Introduction to AWS ELB](#introduction-to-aws-elb)
  - [Importance of ELB](#importance-of-elb)
  - [Key Metrics to Monitor](#key-metrics-to-monitor)
  - [Monitoring Procedures](#monitoring-procedures)
- [Deploy AWS ELB](#deploy-aws-elb)
  - [Setting Up a Load Balancer on AWS EC2](#setting-up-a-load-balancer-on-aws-ec2)
    - [1. Steps to Log into AWS EC2 Management Console:](#1-steps-to-log-into-aws-ec2-management-console)
    - [2. Choose Load Balancer Type:](#2-choose-load-balancer-type)
    - [3.  Name Your Load Balancer:](#3--name-your-load-balancer)
    - [4. Assign Security Groups:](#4-assign-security-groups)
    - [5. Configure Security Settings:](#5-configure-security-settings)
    - [6.  Configure Health Check:](#6--configure-health-check)
    - [7.  Add EC2 Instances:](#7--add-ec2-instances)
    - [8.  Add Tags (Optional):](#8--add-tags-optional)
    - [9. Review and Create:](#9-review-and-create)
  - [Monitoring ELB](#monitoring-elb)
- [AWS ELB Metrics](#aws-elb-metrics)
  - [Key Metrics for Monitoring ELB Instances](#key-metrics-for-monitoring-elb-instances)
    - [1. Backend Connection Errors](#1-backend-connection-errors)
    - [2. Latency](#2-latency)
    - [3. Surge Queue Length](#3-surge-queue-length)
    - [4. Spillover Count](#4-spillover-count)
    - [5. HTTP Status Codes](#5-http-status-codes)
    - [6. Request Count](#6-request-count)
    - [7. Healthy Host Count](#7-healthy-host-count)
    - [8. Unhealthy Host Count](#8-unhealthy-host-count)
- [Monitor AWS ELB Metrics](#monitor-aws-elb-metrics)
  - [Checking ELB Metrics in AWS Management Console](#checking-elb-metrics-in-aws-management-console)
    - [Accessing ELB Metrics](#accessing-elb-metrics)
  - [Testing ELB Connection](#testing-elb-connection)
  - [Key Metrics to Monitor](#key-metrics-to-monitor-1)
    - [Healthy and Unhealthy Instances](#healthy-and-unhealthy-instances)
    - [Average Latency](#average-latency)
    - [HTTP Status Codes](#http-status-codes)
  - [Monitoring HTTP Status Metrics](#monitoring-http-status-metrics)
  - [Starting EC2 Instances](#starting-ec2-instances)
  - [Recap](#recap)

# Introduction to Monitoring and Alerting for AWS ELB

## Introduction to AWS ELB
- AWS ELB: Stands for **Elastic Load Balancer**.
- It's a **software load balancer** that **distributes incoming application traffic** across multiple Amazon EC2 instances.
- Ensures **fault tolerance, scalability**, and **optimal performance** for applications.


## Importance of ELB

- **Traffic Distribution**: Automatically distributes incoming traffic to multiple EC2 instances.
- **Fault Tolerance**: Helps achieve fault tolerance by balancing the load across instances.
- **Scalability**: Provides the necessary load balancing capacity to handle varying amounts of traffic.

## Key Metrics to Monitor
- **Availability**: Ensure the load balancer is always available to handle incoming traffic.
- **Performance**: Monitor the performance of the load balancer to ensure it is routing traffic efficiently.
- **Correct Functioning**: Verify that the load balancer is correctly routing traffic to the underlying EC2 instances and other compute resources.

## Monitoring Procedures
- **Set Thresholds**: Establish thresholds for key metrics to ensure the load balancer is performing optimally.
- **Regular Monitoring**: Continuously monitor the load balancer to detect and address any issues promptly.

# Deploy AWS ELB
It distributes incoming application traffic across multiple Amazon EC2 instances to ensure fault tolerance and scalability.




## Setting Up a Load Balancer on AWS EC2

### 1. Steps to Log into AWS EC2 Management Console:
1. **Log into the AWS EC2 Management Console**.
2. Navigate to the **Load Balancers menu**.
3. Click on **"Create Load Balancer"**.

---

### 2. Choose Load Balancer Type:
- **Application Load Balancer**: Operates at the application layer, allows routing based on content.
- **Classic Load Balancer**: Routes traffic based on application or network-level information. Ideal for simple load balancing across multiple EC2 instances.

---

### 3.  Name Your Load Balancer:
- Example: Name it **"Alert ELB"**.

---

### 4. Assign Security Groups:
- Security groups act as virtual firewalls controlling traffic for EC2 instances.
- Choose appropriate security groups based on the type of application (e.g., web application, FTP server).

---

### 5. Configure Security Settings:
- Option to configure **SSL encrypted traffic** for secure connections (recommended for production).

---

### 6.  Configure Health Check:
1. **Health Checks**: Automated tests to verify if instances are functioning as expected.
2. **Ping Protocol**: Choose from HTTP, TCP, HTTPS, or SSL.
3. **Ping Port**: Specify the port (e.g., port 80 for HTTP).
4. **Ping Path**: Target URL path (e.g., `/index.html`).
5. **Response Timeout**: Time in seconds to wait for a response (e.g., 5 seconds).
6. **Interval**: Time between health checks (e.g., 30 seconds).
7. **Unhealthy Threshold**: Number of failed checks before marking an instance as unhealthy.
8. **Healthy Threshold**: Number of successful checks before marking an instance as healthy.

---

### 7.  Add EC2 Instances:
- Select the EC2 instances to serve the application behind the ELB.

---

### 8.  Add Tags (Optional):
- Tags can be used for organising and managing resources.

---

### 9. Review and Create:
- Review all settings and click **"Create"** to deploy the load balancer.

## Monitoring ELB
- **Health Checks**: Ensure only healthy instances receive traffic.
- **Metrics**: Monitor key metrics such as availability, performance, and correct functioning.
- **Thresholds**: Set thresholds for key metrics to maintain optimal performance.


# AWS ELB Metrics

## Key Metrics for Monitoring ELB Instances

### 1. Backend Connection Errors
- This metric represents the number of unsuccessful connections between the Elastic Load Balancer (ELB) and the registered EC2 instances.
- **Significance**: 
  - Indicates connectivity issues between the ELB and backend EC2 instances.
  - Monitoring this metric ensures flawless connectivity and prevents unnecessary latency.

---

### 2. Latency
- Latency refers to the time it takes to receive a response from the backend EC2 instance.
- **Significance**:
  - Provides insights into application performance.
  - Use average historic values and compare them against maximum values to identify slow response periods or bottlenecks.
  - Helps diagnose performance tuning needs or configuration issues causing application slowdown.

---

### 3. Surge Queue Length
- This metric tracks the total number of requests waiting to be routed by the load balancer.
- **Significance**:
  - Requests are queued if the ELB cannot establish a connection with a healthy instance.
  - The queue has a maximum size of 1024 requests. Additional requests are rejected when the queue is full.
  - A higher surge queue length may indicate capacity overload or configuration problems.

---

### 4. Spillover Count
- Spillover occurs when requests are dropped due to the surge queue being full.
- **Significance**:
  - Provides the count of requests that were dropped.
  - High spillover count indicates a need to scale the backend infrastructure or investigate configuration issues.

---

### 5. HTTP Status Codes
- Tracks specific HTTP status codes from backend EC2 instances or the ELB itself.
- **Significance**:
  - Helps identify the types of responses users are receiving.
  - Provides application-level health insights and aids in detecting issues like errors or timeouts.

---

### 6. Request Count
- The total number of requests received by the ELB.
- **Significance**:
  - Indicates the volume of incoming traffic.
  - Useful for understanding usage patterns and planning for scaling.

---

### 7. Healthy Host Count
- The number of EC2 instances that are functioning properly and registered with the ELB.
- **Significance**:
  - Indicates the availability of backend resources to handle incoming traffic.

---

### 8. Unhealthy Host Count
- The number of EC2 instances registered with the ELB but deemed unhealthy due to health check failures.
- **Significance**:
  - Alerts about problematic instances.
  - Helps ensure quick remediation to maintain application reliability.


# Monitor AWS ELB Metrics

## Checking ELB Metrics in AWS Management Console

### Accessing ELB Metrics
1. Navigate to the **AWS Management Console**.
2. Select the **Load Balancer** that was deployed in the previous session.
3. Review the available tabs to monitor and configure the ELB:
   - **Instances Tab**: Details of EC2 instances backing the ELB.
   - **Health Check Tab**: Configured health check settings.
   - **Listeners Tab**: Ports configured for incoming connections.
   - **Monitoring Tab**: Metrics provided by AWS for the ELB.
   - **DNS URL**: The assigned URL for external clients to connect to the ELB.

---

## Testing ELB Connection
1. Copy the DNS URL provided for the ELB.
2. Paste it into a browser to simulate a client request.
3. If no healthy instances are available:
   - The request will time out after waiting for a valid connection.
   - This demonstrates the ELB’s inability to route requests to unhealthy or stopped instances.

---

## Key Metrics to Monitor

### Healthy and Unhealthy Instances
- **Healthy Instances**: Number of instances passing health checks.
- **Unhealthy Instances**: Number of instances failing health checks due to:
  - Not listening on the expected port.
  - Not serving the expected content (e.g., `index.html`).

### Average Latency
- Time taken to route a request and receive a response from backend EC2 instances.
- Helps identify bottlenecks or configuration issues affecting application performance.

### HTTP Status Codes
- **2XX (OK)**: Indicates successful requests.
- **4XX (Client Errors)**: Indicates client-side issues (e.g., bad request, file not found).
- **5XX (Server Errors)**: Indicates server-side issues or exceptional behaviors.
- Monitor these metrics for spikes, which can indicate application or configuration problems.

---

## Monitoring HTTP Status Metrics
1. HTTP status metrics (2XX, 4XX, 5XX) can be plotted in **CloudWatch Dashboards**.
2. Create alarms for threshold breaches, e.g.,:
   - Excessive 4XX or 5XX errors.
   - Low 2XX responses.

---

## Starting EC2 Instances
1. Navigate to the **EC2 Dashboard** in the AWS Management Console.
2. Start one or more instances backing the ELB:
   - Verify that the instance is listening on the expected port (e.g., port 80).
   - Ensure a valid web server is running and serving the required content (e.g., `index.html`).
3. If health checks fail:
   - Hover over the information icon in the **Instances Tab** for details.
   - Review and address health check failures (e.g., instance not started, incorrect configuration).

---

## Recap
- Deployed and configured an ELB instance.
- Reviewed ELB metrics for monitoring and troubleshooting.
- Learned how ELB performs health checks on EC2 instances to ensure requests are routed to healthy resources.
- Verified how ELB metrics provide insights into application health and performance.
- Explored the process of starting instances and addressing health check failures.


