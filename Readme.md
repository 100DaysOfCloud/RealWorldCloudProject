# Real World AWS Cloud Project


The purpose of this project is to simulate real-world architecture of a cloud project.
If you can complete all of these tasks you can proclaim yourself a Professional Cloud Engineer


# Sample Scenario

Build a clone of Github Issues and Projects but for AWS CodeCommit.

- Solution Architecting
  - Technical Diagaram
  - Technical Roadmap
  - Cost Analysis
  - Research and Development — Technical Uncertainty
- DevOps
  - Infrastructure as Code (IaC)
  - Application Configuration Delivery
  - Golden Image
  - Playbooks, Runbooks and OpsItems
  - Log Collection
  - Multi-Cloud Monitoring
  - Log Analysis
- Development
  - Emails
  - Queueing
  - Code Management
  - Globally Avaliable, Distrubuted Database
- Security
  - Principle of Least Permission (PolP)
  - MFA Hardware Device
  - SOC 2
  - Application Firewall
- Governance
  - Multi-Account
  - Tagging and Resource Groups
  - Single Sign On
  - Inventory
- Development
  - Sythentic Testing
  - Instrumentation and Monitoring
  - Queueing
  - Decenteralized Authenication
  - Accessibility
- Product Marketing
  - Marketing Email/SMS Notifications
  - Conversion Tracking

# Solution Architecting

## Technical Diagaram

### Pre-Sales Architecture
As a Solutions Architect we need to best guess what our possible architecture will look like.

- [ ] Using software such as Adobe XD, Sketch, Figma or otherwise create an
architectural digram of the planned project before the construction of any code.

Try to be as through as possible to show you are aware of the underlying resources.
https://aws.amazon.com/architecture/icons/

### Revised Architecture
As a Solutions Architect we don't always guess right, its important that
we show growth in our knowledge. Update your technical architecture
diagram with the new kwoledge after you have direct experience
implementing your original plan.

## Technical Roadmap
As a Solutions Architect we want to best steer our technology choices so
we do not meet a technical deadend because the time and effort to adjust
the architecture would doom the business but would leave our technical
evolution stagenent for a long period of time.


- [] Evaluate solutions such as AWS Amplify, Google Firebase, Elastic Beastalk,
AWS CodeStore, Azure App Services, and determine the possible technical deadend
or business limations for adopting these convenient solutions.

Its also important that we approach development as a series of milestones and
put these milestones into production. Our cost and technical maintaince
needs to scale with the growth of the company and we need to contiously
ship features to production for customer use.


- [ ] Create a technical roadmap that gradully introduces features and infrastructure.

## Cost Analysis

A Solution Architecture needs to consider the cost of a solution.

- [ ] Utilizing your technical roadmap, calculate the montly cost of cloud services we'll adopt and show
the budget scales over the span of 3 years. Make adjustments to your technical roadmap.

- 1-2 months we only have free-tier and $300 USD AWS credits in total
- 4-8 months we have been given $2500 USD AWS Credits from the Banana Accelereator
- 8+ months we no longer have AWS Credits, but we are generating revenue with about 20 signup daily and only %12 of those users are paying
- 2+ years we have customers 500,000+ paying customers distrubted in three distinct geographical locations

### Research and Development

Our company wants to take advantage of a goverment program that will reimburse the cost of the advancemen of our technical knowledge.
- [ ] You need to present technical uncertainty by hypothesising possible solutions
- [ ] you then need to carry out experiements to determine if it is or is not possible.
- [ ] You need to track your hours when conducting these experiments and researching a solution
- [ ] You need to collect evidence (screenshots there are not googlable solutions), timesheets, experiments run (eg Git repo or a research@ email)

https://www.canada.ca/en/revenue-agency/services/scientific-research-experimental-development-tax-incentive-program.html

#### Example Research

Amazon Congito is an Decenteralization Authennication Service, You want to utilize Cognito because you are breaking your app into multiple apps and you don't want a single point of failure for your users by making my one app soely responsible for authenication. You also want all the built benifits of a managed service like Cognito advanced security features.

Your company wants to utilize LinkedIn, Github or Twitter as a method of Oauth, Whatever they can get working. Cognito does not appear to directly support these methods but the documentation suggets via Custom Authorizers:

Someone suggests its possible

https://stackoverflow.com/questions/44397268/how-could-we-use-github-account-as-an-aws-cognito-identity-provider

And you see a possible solution for Github but appears untested and missing steps
https://github.com/TimothyJones/github-cognito-openid-wrapper

# DevOps

## Infrastructure as Code (IaC)

Our CEO has decided that our application is currently a SaaS offering
but large enterprises already utilizing AWS are interested in having a
single tenant version of our software within their own AWS Account.

So we need to ensure that all of our infrastructure is managed by AWS
CloudFormation.

- [ ] Nested Stacks
- [ ] Cross Refernecing Stacks
- [ ] We should defined Outputs on key resources
- [ ] We should use --no-execute-changeset and always formally review
  our ChangeSets before deploying
- [ ] We should apply tagging to all of our resources
- [ ] Apply Drift Detection
- [ ] Utilize Dynamic Variables for SSM Parameter Store and Secrets
  Manager

> You can use CDK or Terraform but CloudFormation and SAM will better
> demostrate through knowledge of underlying resources.

## Application Configuration Delivery

Developers keep introducing syntax mistakes to the application
configuration variables and this causes our deploys to fail and a
manuall rollback or worst, our app does deploy and it breaks the
experience for users on some critical business workflows.

- [ ] Use AppConfig to validate our application configuration values are
  valid

## Golden Image

We need to keep our Image/Container up-to-date with the latest patches.

- [ ] Create an Automation Document
- [ ] Create a series of Run Commandas

> For serverless we might skip this step if we are using the AWS Managed
> Instances

## Playbooks, Runbooks and OpsItems

You need to choose the scenario based on your choosen compute architecture.

### (EC2 Scenario)
Our Developers keep using SSH to debug servers, introduces uncertainty
if the state of the servers are exactly as we expect them to be.


- [ ] Create a series of run commands for common operations so
  developers can debug or fix the server

### (Container Scenario)

### (Serverless Scenario)

## Log Collection

- [ ] Stream CodeDeploy logs to CloudWatch Logs
- [ ] Stream Application logs to CloudWatch Logs
- [ ] Configure CodeBuild to stream to CloudWatch Logs
- [ ] Configure Run Command Documents to stream to CloudWatch Logs

## Multi-Cloud Monitoring

Our DevOps team wants to evaluate Azure Monitor as more robust solution
for monitoring of our compute

- [ ] Intrument our AWS resources and observe the data in Azure Monitor
- [ ] Write up a report of the different offerings between CloudWatch
  Services and Azure Monitor and make a recommendation of whether to
adopt or stick with AWS tooling

## Log Analysis

- [ ] Use CloudWawtch Log Insights to investigate a 500 error within
  your application code
- [ ] Create a Cloud Log Insights Rule so you are alerted whenever a 500
  error occurs within your application

# Development

## Emails

- [ ] When a user leaves a comment on an issue the web-application should send
an email via SES

## Queueing

- [ ] Emails be sent from the web-application should be queued within
  SES to ensure the primary application thread doesn't hang when
recieving too many email requests at the same time.

## Code Management

- [ ] Store your code within in AWS CodeBuild
- [ ] Use a Gitflow workflow and use sementic tagging eg. 1.0.0 to denote
  versions
- [ ] Your commits should reference issues in an issue tracker

## Globally Avaliable, Distrubuted Database

Our product is has grown to be utilized in the Asia, North America and India
geographic areas. Our database resides within a single region and this
is causing latency issues.

Global writes are as important and reads.

- [ ] Between DynamoDB and Aurora implement the best possible solution
  that allows for both global reads and writes
- [ ] Consider implmenting a third-party distrubted database if you
  cannot meet the use case

# Security

## Principle of Least Privilege (PolP)

- [ ] Use the least amount of permissions possible when creating
  policies and roles
- [ ] Use permission boundaries to limit the scope of use
- [ ] Use Service Control Policies to lock out unused regions and
  services
- [ ] Grant access to services to your developer account via Resource Group tagging

## SOC-2

Investigate SOC2 Compliance Program

- [ ] How much does it cost?
- [ ] What do you need be compliant with?
- [ ] What is the process?
- [ ] Are there any proactive measures to align with the program?

## MFA Hardware Device

- [ ] Apply MFA to your AWS Accounts using a Hardware Device such as Yubi Key

## Application Firewall

- [ ] Apply AWS WAF to your admin panel


# Governance

## Multi-Account

Your web-application should be divided into three components:
* Admin Panel — The web
* User Panel — The primary web-application users use

- [ ] Create an AWS Organization
- [ ] Deploy Admin Panel in one account
- [ ] Deploy User  Panel in another account

# Developer

## WSAG 2.0/30

Investigate WSACG 2.0/3.0 Level II Requirements
