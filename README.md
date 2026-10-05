# AWS Auto Scaling & Load Balancing

A hands-on AWS project demonstrating how to build a scalable and reliable infrastructure that automatically responds to changing application traffic.

Imagine an application suddenly getting more users. The infrastructure needs to distribute traffic across healthy servers and automatically add or remove instances based on workload.

This project demonstrates that real-world DevOps scenario using AWS.

## Architecture

```text
                    Users
                      |
                      v
              ┌───────────────┐
              │      ALB      │
              │ Load Balancer │
              └───────┬───────┘
                      |
                Target Group
                  /       \
                 v         v
             EC2 + Nginx  EC2 + Nginx
                  \       /
                   \     /
                Auto Scaling
                     |
                     v
                 CloudWatch
                     |
              Scale Out / In
```

## Tech Stack

<p align="left">
  <img src="https://skillicons.dev/icons?i=aws,linux,nginx" />
</p>

**AWS Services**

`EC2` `ALB` `Auto Scaling` `Target Groups` `CloudWatch` `Security Groups` `Launch Templates`

## What I Built

* Application Load Balancer for traffic distribution
* EC2 Auto Scaling Group with Target Tracking
* Launch Template with Nginx
* CloudWatch monitoring and scaling alarms
* Health checks through Target Group
* Automatic scale-out and scale-in testing

## Scaling Flow

```text
CPU Increases
     ↓
CloudWatch Alarm
     ↓
Auto Scaling
     ↓
New EC2 Instance
     ↓
Target Group
     ↓
ALB distributes traffic
```

When the workload decreases, Auto Scaling automatically scales the infrastructure back down.

## Testing

I tested both:

**Scale Out**

`1 EC2 → 2 EC2`

**Scale In**

`2 EC2 → 1 EC2`

I also troubleshot real setup issues including ALB access, EC2 SSH connectivity, Security Groups, and Target Group health.

## Key Learnings

* Load balancing
* Auto scaling
* CloudWatch monitoring
* EC2 health checks
* AWS networking and security
* Infrastructure reliability

## Project Demo

The project was tested directly on AWS using the Console, including ALB, Target Groups, EC2, Auto Scaling and CloudWatch.

## Author

Tanjim Ahmed

[GitHub](https://github.com/tanahmeeedsx)
