# Making an app highly available and scalable
## High Availability
- High Availability (HA) describes systems that are dependable enough to operate continuously without failing. They are well-tested and sometimes equipped with redundant components.
- To achieve high availability, first identify and eliminate single points of failure in the operating system’s infrastructure. Any point that would trigger a mission critical service interruption if it was unavailable qualifies here.
- https://avinetworks.com/glossary/high-availability/
### High Availability in AWS
- create an autoscaling group with min capacity=1 and max capacity=1. So whenever your instance fails, the autoscaling group will create a new one. The autoscaling group comes for free, so this is not a bad solution depending on your SLA.
- use ec2 auto-recovery feature by creating a cloudwatch alarm that would replace your instance if failed.
- create two EC2 instances and use Route 53 DNS failover to resolve to an healthy instance
Last but not least: the best solution is definitely to create several instances across several availability zones and to use an elastic load balancer to distribute the traffic. This way, even if an instance fails, you already have other ones available. AWS recommends this solution as they have an SLA of 99.95% for their instance in an AZ. By putting in several AZs you can have 100% availability
- https://stackoverflow.com/questions/36709830/ec2-amazon-high-availability-always-on
## Scalability
- Ability to increase or decrease IT resources as needed to meet changing demand
### Scalability in AWS
- AWS Auto Scaling, it’s easy to setup application scaling for multiple resources across multiple services in minutes

# Creating a Launch template
- Go to Launch Templates on the EC2 sidenav
- Give a sensible name e.g. eng_99_delwar_app_ASG_LT
- Ensure to tick "Provide guidance to help me set up a template that I can use with EC2 Auto Scaling"
- Assign the AMI, note should have been set up previously
- Assign instance type e.g. t2.micro
- Assign key pair, this should be the same as the AMI to enable simplicity
- Keep Network setting as a VPC (in this case)
- Assign the security group used in AMI
- In advanced details, run the commands required to install dependencies e.g. sudo apt-get update -y
- create template

# Auto Scaling
- Go to Auto Scaling --> Auto Scaling Groups on the EC2 sidenav
- Click "Create an Auto Scaling Group"
- Give a sensible name (NOTE that you shouldn't use underscores here) e.g. eng99-delwar-app-asg
- Select launch template
- Change version to Latest to receive updates
- Choose the default VPC
- Select the availability zones, in this case default 1a default 1b and default 1c
- Attach a new load balancer
- Ensure Application Load Balancer is selected
- Name the load balancer something sensible e.g. eng99-delwar-app-asg-ALB
- Change load balancer scheme to Internet-facing
- Create a new target group with e.g. eng99-delwar-app-asg-tg
- Enable group metrics collection with CloudWatch
- Change the desired capacity, minimum capacity and maximum capacity to 2,2,3 respectively (for this example)
- Select Target tracking scaling policy for the scaling policies. Ensure that "disable scale in to create only a scale-out policy" is NOT selected
- Set the metric to type etc to whatever
- Do NOT selected enable instance scale-in protection
- Add whatever notifications
- Attach name tag e.g. {Name: eng99_delwar_ASG}
- Review and Create
