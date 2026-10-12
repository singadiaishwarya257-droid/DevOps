# DevOps Fundamentals

## Overview

DevOps is a way of working where development and operations teams collaborate to deliver software faster, more reliably, and with more automation.

A simple example:
- Developers write code.
- Testers verify whether it works correctly.
- Operations teams manage servers and deployment.
- DevOps connects and automates these activities.

Important:
- DevOps is not just one tool.
- It is a combination of practices, automation, collaboration, and tools used throughout the software delivery process.

---

## Day 1: DevOps Fundamentals

### 1. What is DevOps?

DevOps is a culture and practice that brings together software development and IT operations.

The goal is to:
- reduce delays between coding and deployment,
- improve quality,
- automate repetitive work,
- detect problems earlier,
- release updates more frequently and safely.

Example:
A company builds a shopping application.
- Developers write the code.
- Testers validate the features.
- Operations manages the servers.
- DevOps ensures these tasks are connected and automated.

### 2. Why do companies need DevOps?

Without DevOps, teams often:
- deploy manually,
- wait on other teams,
- face more errors,
- release changes less often.

With DevOps, teams can:
- automate testing and deployment,
- release updates more frequently,
- detect failures faster,
- reduce downtime and risk.

### 3. End-to-end software delivery process

1. Developer writes code
   - Example: adding a payment feature.

2. Code is stored in GitHub
   - Version control and collaboration.

3. CI/CD pipeline runs
   - Build and automated tests start.

4. Application is deployed
   - Example: to a cloud server or Kubernetes cluster.

5. Application is monitored
   - Check for errors, performance issues, and availability.

### 4. Daily learning method

Follow this routine for every topic:
1. 10 minutes: Understand the concept in simple English.
2. 15 minutes: Learn a real-world example and why companies use it.
3. 20 minutes: Practice the command or tool in a lab or internship environment.
4. 10 minutes: Answer 5 interview MCQs and explain the concept aloud without looking at your notes.

Important rule:
Do not memorize answers blindly. Try to explain:
- what the tool does,
- why it is used,
- how it works,
- how you would troubleshoot it if it failed.

### 5. Study plan checklist

Before you start, decide:
- Beginner, intermediate, or advanced knowledge
- AWS, Azure, or both
- Daily study time: 30 minutes, 45–60 minutes, or 1.5–2 hours

This helps you build a learning plan that matches your current level.

---

## Day 2: SDLC, Environments, and Deployment

### 1. What is SDLC?

SDLC stands for Software Development Life Cycle.

It is the step-by-step process used to build, test, release, and maintain software.

Example:
A company wants to build a shopping app like Amazon. It does not develop randomly; it follows a process.

### 2. Six stages of SDLC

1. Planning
   - Decide what application to build.

2. Design
   - Plan how the system will work.

3. Development
   - Developers write the code.

4. Testing
   - Testers check for bugs and errors.

5. Deployment
   - Make the application available to users.

6. Maintenance
   - Fix issues and release updates.

### 3. Real-life example: Food delivery app

- Planning: Decide to build an app for ordering food.
- Design: Plan login, menu, and payment screens.
- Development: Write code using Python, Java, or JavaScript.
- Testing: Check whether login and payments work correctly.
- Deployment: Release the app so customers can use it.
- Maintenance: Fix bugs and add new features.

Interview point:
SDLC describes the overall process of developing and maintaining software. DevOps practices improve this process by automating and speeding up build, test, deployment, and monitoring.

### 4. Development vs Testing vs Production

These are very important terms in DevOps interviews.

#### Development environment (Dev)
- Developers write code and try new features here.
- Example: A developer builds a new payment button.

#### Testing environment (Test)
- The team checks whether the software works correctly before release.
- Example: Testers verify the payment button works properly.

#### Production environment (Prod)
- This is the live environment used by real customers.
- Example: Customers use the payment button to buy products.

Simple difference:
- Dev = Build and change
- Test = Check and verify
- Prod = Real users use the application

Companies keep these environments separate to reduce the risk of faulty code reaching customers.

### 5. What is deployment?

Deployment means putting an application or a new version of it into an environment where it can run.

Example:
A developer completes a login feature. After required checks, the team deploys the updated version to a server so users can access it.

In DevOps, deployment can be automated using tools such as:
- Jenkins
- Azure Pipelines
- GitHub Actions

---

## Day 2: Interview MCQs

### 1. What does SDLC stand for?
A. Software Development Life Cycle
B. System Deployment Linux Command
C. Software Data Link Connection
D. Server Development Level Control

Correct answer: A

### 2. A developer creates a new feature. Where should they normally work first?
A. Production
B. Development
C. Customer environment
D. Live server only

Correct answer: B

### 3. Why do teams use a testing environment?
A. To store passwords publicly
B. To replace developers
C. To verify software before release
D. To avoid all documentation

Correct answer: C

### 4. A new version is released for customers. What is this process called?
A. Planning
B. Coding
C. Deployment
D. Requirement gathering

Correct answer: C

### 5. A live application has a bug reported by customers. What stage addresses this ongoing issue?
A. Design only
B. Maintenance
C. Initial planning only
D. Requirement gathering only

Correct answer: B

### 6. Which statement about DevOps and SDLC is correct?
A. They mean exactly the same thing
B. SDLC is only about servers
C. DevOps replaces all testing
D. DevOps practices improve collaboration and automate parts of software delivery

Correct answer: D

### Day 2 revision notes

Before moving to Day 3, make sure you can explain these without looking at your notes:
- What is SDLC?
- What are the six stages of SDLC?
- What is the difference between Dev, Test, and Prod?
- What is deployment?
- How do DevOps practices improve software delivery?

Practical task:
Explain the food delivery app example in your own words, then complete all six MCQs above.

---

## Day 3: DevOps Lifecycle and CI/CD

### 1. What is the DevOps lifecycle?

The DevOps lifecycle is a continuous process of developing, delivering, operating, and improving software.

Example:
A company develops a food delivery application. Whenever developers update the code, the company must test it, deploy it, and monitor whether it works correctly.

### 2. DevOps lifecycle stages

1. Plan
   - Decide which feature to build.
   - Example: Jira

2. Code
   - Developers write application code.
   - Example: VS Code, Git

3. Build
   - Prepare the application for testing.
   - Example: build tools

4. Test
   - Automatically check code for errors.
   - Example: testing tools

5. Release and Deploy
   - Prepare and deliver a new version.
   - Example: Jenkins, Azure Pipelines

6. Operate
   - Run the application on servers or cloud.
   - Example: Linux, AWS, Azure

7. Monitor
   - Track errors, performance, and availability.
   - Example: Prometheus, Grafana

Feedback loop:
Monitoring results help the team improve the next release.

These stages are not always a strict one-way sequence. Teams repeat them continuously, and monitoring feedback can lead to new code changes.

### 3. What is CI/CD?

CI/CD is one of the most important DevOps interview topics.

#### CI — Continuous Integration
Developers frequently add code changes to a shared repository. Automated builds and tests help detect issues early.

Example:
A developer pushes code to GitHub, and automated tests start immediately.

#### CD — Continuous Delivery or Continuous Deployment
Both automate work after integration, but they differ in how releases happen.

- Continuous Delivery: The application is prepared for release and often requires manual approval before production.
- Continuous Deployment: Every change that passes required checks is deployed to production automatically.

Easy way to remember:
- CI = Integrate code and test it.
- Continuous Delivery = Keep software ready to release.
- Continuous Deployment = Automatically release changes when checks pass.

### 4. Real CI/CD pipeline example

Suppose you change the login page of an application.

Flow:
1. Developer changes code
2. Updated login page is saved
3. GitHub stores the updated code
4. CI/CD pipeline starts
5. Jenkins or Azure Pipelines runs the workflow
6. Build and tests run
7. The app is deployed to the target environment
8. Monitoring checks application health and errors

The pipeline is the automated workflow connecting these steps.
It can also include:
- security scanning,
- approval checks,
- artifact storage,
- rollback steps.

### 5. What if a test fails?

The pipeline should normally stop before deployment, notify the team, and show the failure logs.

Then:
- the developer fixes the issue,
- the code is updated,
- the pipeline is re-run.

This is a common interview scenario.

### 6. Where do the DevOps tools fit?

| Tool | Main purpose |
| --- | --- |
| Jira | Plan and track work |
| Git | Track code changes |
| GitHub | Host repositories and collaborate |
| Jenkins | Automate CI/CD pipelines |
| Azure Pipelines | Build and deploy applications |
| Docker | Package applications and dependencies into containers |
| Kubernetes | Manage containerized applications at scale |
| AWS / Azure | Provide cloud infrastructure and services |
| Prometheus / Grafana | Monitor metrics and visualize system health |

Note:
Tools can support multiple stages. For example, GitHub can host code and also run workflows through GitHub Actions.

---

## Day 3: Interview MCQs

### 1. A developer pushes code to GitHub. The system automatically runs tests. Which concept is this?
A. Continuous Integration
B. Manual deployment
C. Monitoring
D. Maintenance

Correct answer: A

### 2. A pipeline's automated test fails. What should normally happen next?
A. Deploy immediately
B. Ignore the error
C. Stop the affected pipeline before deployment and investigate
D. Delete the repository

Correct answer: C

### 3. Which tool is commonly used to automate CI/CD pipelines?
A. Jira only
B. Jenkins
C. Microsoft Word
D. Photoshop

Correct answer: B

### 4. A company wants every change that passes all required checks to go live automatically. Which CD approach is this?
A. Continuous Delivery only
B. Continuous Deployment
C. Manual testing only
D. Planning

Correct answer: B

### 5. Why is monitoring important after deployment?
A. To write the original code
B. To remove the need for testing
C. To replace Git
D. To detect errors and performance problems

Correct answer: D

### 6. Which statement about Docker and Kubernetes is correct?
A. They are exactly the same tool
B. Docker packages applications into containers; Kubernetes orchestrates containers
C. Kubernetes is only a code editor
D. Docker is a project-management tool

Correct answer: B

### Practical task

Try this simple exercise with your existing GitHub repository:
1. Open your DevOps learning repository.
2. Add a small change to a README file.
3. Commit and push the change.
4. Identify what would happen if a CI/CD workflow were configured for that repository.
5. Explain where automated testing and deployment would fit.

You do not need a complete pipeline today. First, understand the flow.

### Day 3 revision checklist

Before moving forward, make sure you can explain:
- the DevOps lifecycle,
- the difference between CI and CD,
- what a pipeline does,
- what happens when a test fails,
- why monitoring is necessary.

---

## Final Summary

DevOps is the practice of combining software development and operations to deliver software faster, more reliably, and with less manual work.

Core ideas to remember:
- SDLC explains the software lifecycle.
- Dev, Test, and Prod environments serve different purposes.
- Deployment means releasing software to an environment.
- CI/CD automates integration, testing, and release.
- Monitoring helps teams keep applications healthy after deployment.
- DevOps is about people, processes, and tools working together.

This is the foundation you need before you move into specific tools like Git, Jenkins, Docker, Kubernetes, AWS, and Azure.