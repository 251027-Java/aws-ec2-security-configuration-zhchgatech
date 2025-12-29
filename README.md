[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/XBc83fT1)
# Lab: AWS EC2 Security Configuration

## Goal
Configure security groups and understand AWS networking for EC2 instances.

## Learning Objectives
- Understand Security Group rules
- Configure inbound/outbound traffic
- Practice with AWS CLI commands
- Troubleshoot connectivity issues

## Pre-requisites
- AWS Account (Free Tier)
- AWS CLI installed and configured (optional but recommended)

## Scenario
You are deploying a web application that needs:
1. SSH access for administration (from your IP only)
2. HTTP access for web traffic (from anywhere)
3. HTTPS access for secure traffic (from anywhere)
4. Custom port 8080 for API (from specific CIDR)

## Tasks

### Task 1: Design Security Group Rules
Fill in the following table with appropriate values:

| Rule | Type | Protocol | Port | Source | Purpose |
|------|------|----------|------|--------|---------|
| 1    | SSH  | TCP      | ?    | ?      | Admin access |
| 2    | ?    | TCP      | 80   | ?      | Web traffic |
| 3    | ?    | TCP      | 443  | ?      | Secure web |
| 4    | Custom TCP | TCP | ?  | 10.0.0.0/8 | Internal API |

### Task 2: Create Security Group (Console)
1. Navigate to EC2 → Security Groups → Create
2. Name: `web-app-sg`
3. Description: `Security group for web application`
4. VPC: Default VPC

### Task 3: Add Inbound Rules
Add rules based on your Task 1 design:
- SSH from your IP (`x.x.x.x/32`)
- HTTP from anywhere (`0.0.0.0/0`)
- HTTPS from anywhere (`0.0.0.0/0`)
- Port 8080 from internal network (`10.0.0.0/8`)

### Task 4: AWS CLI Commands (Optional)
Practice creating the same security group using CLI:

```bash
# Create security group
aws ec2 create-security-group \
    --group-name web-app-sg-cli \
    --description "Security group via CLI" \
    --vpc-id <your-vpc-id>

# Add SSH rule
aws ec2 authorize-security-group-ingress \
    --group-id <sg-id> \
    --protocol tcp \
    --port 22 \
    --cidr <your-ip>/32

# Add HTTP rule
aws ec2 authorize-security-group-ingress \
    --group-id <sg-id> \
    --protocol tcp \
    --port 80 \
    --cidr 0.0.0.0/0
```

### Task 5: Troubleshooting Exercise
Given these symptoms, identify the likely cause:

| Symptom | Likely Cause | Solution |
|---------|--------------|----------|
| Can't SSH to instance | ? | ? |
| Website not loading | ? | ? |
| API calls timing out | ? | ? |

## Deliverables
1. Completed security group rules table (Task 1)
2. Screenshot of created security group
3. CLI commands used (if applicable)
4. Troubleshooting answers (Task 5)

## Reference
- [AWS Security Groups Documentation](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-security-groups.html)
