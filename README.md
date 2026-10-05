# AWS Auto Scaling & Load Balancing Infrastructure

A hands-on AWS project that demonstrates how to build a scalable and reliable infrastructure for applications with changing traffic.

The infrastructure uses an Application Load Balancer to distribute traffic across healthy EC2 instances, while an Auto Scaling Group automatically adjusts the number of instances based on CPU utilization.

## Real-World Scenario

Imagine an application suddenly gets more users and traffic starts increasing.

Running everything on a single EC2 instance can create a bottleneck and affect application availability. A better approach is to distribute traffic across multiple healthy instances and automatically add or remove instances based on workload.

This project demonstrates that workflow using AWS.

## Architecture

```text
                    Internet Users
                          |
                          v
              +-----------------------+
              | Application Load      |
              | Balancer (ALB)        |
              +-----------+-----------+
                          |
                          v
                 +----------------+
                 |  Target Group  |
                 +-------+--------+
                         |
              +----------+----------+
              |                     |
              v                     v
        +-----------+         +-----------+
        | EC2       |         | EC2       |
        | Nginx     |         | Nginx     |
        +-----------+         +-----------+
              |                     |
              +----------+----------+
                         |
                         v
                Auto Scaling Group
                         |
                         v
                CloudWatch Monitoring
                         |
                  CPU Utilization
                         |
                         v
                 Scale Out / Scale In
```

## AWS Services Used

* Amazon EC2
* Application Load Balancer (ALB)
* Auto Scaling Group (ASG)
* Launch Template
* Target Group
* Amazon CloudWatch
* Security Groups
* Nginx

## How It Works

1. Users send requests to the Application Load Balancer.
2. The ALB forwards traffic to healthy EC2 instances through the Target Group.
3. Nginx serves the application from the EC2 instances.
4. CloudWatch monitors CPU utilization.
5. When CPU usage increases, the Auto Scaling policy launches a new EC2 instance.
6. The new instance is automatically registered with the Target Group.
7. The ALB distributes traffic across the healthy instances.
8. When the workload decreases, Auto Scaling removes the extra instance.

## Auto Scaling Configuration

| Set
