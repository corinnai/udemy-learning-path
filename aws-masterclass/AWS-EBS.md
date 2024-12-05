- [Monitoring and Alerting for AWS EBS](#monitoring-and-alerting-for-aws-ebs)
  - [EBS Overview](#ebs-overview)
  - [EBS Volume Types](#ebs-volume-types)
  - [Performance Factors](#performance-factors)
  - [EBS SSD Volume Types](#ebs-ssd-volume-types)
  - [IO Credits](#io-credits)
- [AWS EBS Volume Types](#aws-ebs-volume-types)
  - [Io1 (Provisioned IOPS SSD)](#io1-provisioned-iops-ssd)
  - [Hard Disk Volumes](#hard-disk-volumes)
    - [Throughput Optimised HDD (st1)](#throughput-optimised-hdd-st1)
    - [Cold HDD (sc1)](#cold-hdd-sc1)
      - [Performance Comparison](#performance-comparison)
  - [Monitoring AWS EBS Volumes](#monitoring-aws-ebs-volumes)
      - [Understanding EBS Metrics](#understanding-ebs-metrics)
  - [EBS Volume Types](#ebs-volume-types-1)
  - [Status Checks](#status-checks)
  - [Monitoring EBS Volumes](#monitoring-ebs-volumes)
    - [Accessing EBS Volumes](#accessing-ebs-volumes)
    - [Viewing Metrics](#viewing-metrics)
  - [Important Metrics](#important-metrics)
    - [Read and Write Bandwidth](#read-and-write-bandwidth)
    - [Burst Balance](#burst-balance)
  - [Handling Inconsistencies](#handling-inconsistencies)
- [Summary of Module](#summary-of-module)


# Monitoring and Alerting for AWS EBS

Overview:
- **AWS EBS**: Stands for Elastic Block Storage Service.
- Provides block-level storage volumes for EC2 instances.
- Commonly used for general-purpose EC2 instances.

## EBS Overview
- Block-Level Storage: Used for additional storage capacity for EC2 instances.
- Instance Store: Provides temporary block-level storage, physically attached to the host computer.
- Attachment: EBS volumes can be attached, detached, and reattached to instances within the same availability zone.


## EBS Volume Types
- **General Purpose (GP2)**: Fast storage using Solid-state drive (SSD) volumes.
- **Provisioned IOPS (io1)**: Even faster SSDs for high-performance SSD volumes.
- **Throughput Optimised (st1)**: Hard disk drive (HDD) volumes, good for large, sequential data.
- **Cold HDD (sc1)**: HDD volumes for less frequently accessed data.


## Performance Factors
- IOPS (Input/Output Operations Per Second): Primary unit of measure for EBS volume performance. Measures how fast the storage can read/write data.
    - SSD Volumes: Measured in 256 KB (smaller) chunks (random operations).
    - HDD Volumes: Measured in 1024 KB (larger) chunks (sequential operations).
- Throughput: Maximum throughput for GP2 is 160 MB/s. How much data can be read/written per second.



## EBS SSD Volume Types
**GP2** (General Purpose SSD):
- **Baseline Performance**: 3 IOPS per GB up to 10,000 IOPS.
- **Burst Performance**: Up to 3,000 IOPS.
- **Minimum Volume Size**: 8 GB with a minimum of 100 IOPS.


**io1** (Provisioned IOPS SSD):
- **High Performance**: Suitable for mission-critical applications needing fast storage.
- **Cost**: More expensive than GP2 volumes.


## IO Credits
- Represent available bandwidth for burst IO operations: Extra speed you can use when needed.
- Accumulation: Volumes accumulate IO credits at a rate of 3 IOPS per GB. **Initial Credit Balance**: 5.4 million credits, enough for 30 minutes of maximum burst performance.
- Usage: Draws on IO credits when performance exceeds baseline level: Use credits when you need more speed than the baseline.


# AWS EBS Volume Types

## Io1 (Provisioned IOPS SSD)
- Best Suited For: **Workloads** that need to **read/write** a lot of **data** quickly.
- Provides 30 IOPS (Input/Output Operations Per Second) per gigabyte, up to 20,000 IOPS.
This is 10 times more than the General Purpose (GP2) volumes.
- **Consistency**: Always performs at the same speed, unlike GP2 which can speed up temporarily.
- **Use Case**: Great for applications that need to handle a lot of data quickly, like databases.
- **Maximum Speed**: Can handle up to 320 MB of data per second, which is twice as fast as GP2.

## Hard Disk Volumes
### Throughput Optimised HDD (st1)
- **Ideal For**: Data that you need to access often.
- **Optimisation**: Designed to handle large amounts of data being read or written in sequence.
### Cold HDD (sc1)
- **Ideal For**: Data that you don't need to access very often.
- **Cost**: The cheapest option for EBS volumes.
- **Use Case**: Perfect for storing data that you don't need to access frequently and doesn't need to be read or written quickly.
#### Performance Comparison
- **Traditional Hard Disk Volumes**: Good for **handling large amounts of data** but not as fast as SSDs for random data access.
- **Importance of IOPS**: IOPS is a measure of **how quickly the storage can read/write data**. Higher IOPS means better performance for applications that need to access data quickly.


## Monitoring AWS EBS Volumes

#### Understanding EBS Metrics
- **Basic Metrics**: Available every 5 minutes.
- **Detailed Metrics**: Available every 1 minute (default for Io1 volumes).


## EBS Volume Types
- **GP2**: General-purpose SSD, minimum 100 IOPS, minimum size 8 GB.
- **Io1**: High-performance SSD, detailed monitoring by default.
- **SC1**: Cold HDD, for less frequently accessed data.
- **ST1**: Throughput-optimised HDD, for frequently accessed data.



## Status Checks
- **Automated tests** to ensure EBS volumes are **working correctly**.
- Run every **5 minutes**.
- **Results**: Pass or fail status.
- **Actions**: Helps **manage potential data inconsistencies**.


## Monitoring EBS Volumes
### Accessing EBS Volumes
1. Navigate to the **EC2 console**.
2. Click on "Volumes" to see the list of attached volumes.

### Viewing Metrics
1. Select a **volume** and go to the "Status Checks" tab.
2. Check if the **volume status** is "OK".
3. Go to the "Monitoring" section to view various metrics.

## Important Metrics
### Read and Write Bandwidth
- Measures the **data transfer rate** for reading and writing.
- **Unit**: Kibibytes (similar to kilobytes).

### Burst Balance
- **Credits accumulated** for **handling bursts of activity**.
- Accumulated at 3 IOPS per GB per second.


## Handling Inconsistencies
- **Default Action**: AWS disables I/O between the volume and EC2 instance if inconsistencies are found.
- **Override**: Enable the "Auto-Enabled Volume Attribute" to continue using the volume despite inconsistencies.


# Summary of Module

- **EBS Storage Service**: Provides additional storage for EC2 instances.
- **Types of EBS Volumes**: GP2, Io1, SC1, ST1.
- **Monitoring Metrics**: Read/write bandwidth, burst balance, status checks

