# DevOps, Azure DevOps, and Jira Interview Notes

## 1. Overview of DevOps

### What is DevOps?
DevOps is a combination of practices, tools, and cultural principles that brings development and operations teams together to deliver software faster, more reliably, and with better quality.

It focuses on:
- Continuous Integration (CI)
- Continuous Delivery/Deployment (CD)
- Automation
- Monitoring and feedback
- Collaboration between developers and operations teams

### Why is DevOps important?
- Faster delivery of software
- Reduced manual effort and human errors
- Better collaboration and shared ownership
- Faster detection and recovery from failures
- Consistent deployments across environments
- Better traceability and accountability

### Disadvantages of DevOps
| Disadvantage | Explanation | Example |
|---|---|---|
| High initial cost | Requires tools, cloud resources, and training | Setting up CI/CD pipelines, cloud infrastructure, monitoring |
| Skill requirements | Teams need knowledge of automation, scripting, cloud, security, and monitoring | Debugging a failed pipeline |
| Complex implementation | Integrating multiple tools and workflows can be difficult | Connecting Git, testing, Docker, deployments, and monitoring |
| Security risks | Misconfigured pipelines or exposed credentials can create vulnerabilities | Leaked deployment token |
| Maintenance overhead | Pipelines, dependencies, and infrastructure require constant updates | Fixing a broken build agent |
| Resistance to change | Teams may struggle to adapt to shared ownership and automation | Developers and operations still work in silos |
| Automation failures | A broken pipeline can deliver faulty software repeatedly | Weak test automation lets bad code reach production |

### Interview point
DevOps is not just a set of tools. It requires the right culture, process, automation, security, and monitoring. Poor implementation can increase complexity instead of improving delivery.

---

## 2. Azure DevOps, Jira, and Trello

### Azure Boards
Azure Boards is a work-tracking service in Azure DevOps used to plan, assign, prioritize, and track tasks using work items, boards, backlogs, and sprints.

Example:
- Create a User Story for student registration
- Assign tasks to developers
- Track progress from To Do to Done

### Jira
Jira is an issue-tracking and project-management tool by Atlassian. It supports Agile workflows such as Scrum and Kanban, sprint planning, bug tracking, and reporting.

Example:
- A developer logs a bug for failed login
- It is assigned to the backend team
- Status is tracked until fixed and verified

### Trello
Trello is a simple visual project-management tool built with boards, lists, and cards. It is ideal for small teams and straightforward task management.

Example:
- Board: To Do, In Progress, Done
- Cards: Design login page, build API, review code

### Comparison
| Feature | Azure Boards | Jira | Trello |
|---|---|---|---|
| Main purpose | Work tracking integrated with Azure DevOps | Issue tracking and Agile project management | Visual task management |
| Agile support | Scrum and Kanban | Scrum and Kanban | Mostly Kanban |
| Integration | Strong Azure ecosystem | Strong Atlassian ecosystem | Simple collaboration and integrations |
| Best suited for | Teams using Azure DevOps | Teams needing detailed issue workflows | Small teams and simple workflows |

### Interview tip
All three tools can track work, but the choice depends on workflow complexity, reporting needs, integrations, and the team’s existing technology stack.

---

## 3. Work Item Types and Their Meaning

### Epic
A large business objective that can be broken into smaller features and tasks.

Example:
- Build a complete Student Management System

### Feature
A major capability that delivers business or user value.

Example:
- Student registration and profile management

### User Story
A requirement written from the user’s perspective.

Format:
- As a student, I want to register an account so that I can access my academic details.

Purpose:
- Clarifies business value and acceptance criteria

### Spike
A time-boxed research or investigation task used to reduce uncertainty before implementation.

Example:
- Compare JWT authentication vs session-based authentication

Purpose:
- Produce findings, recommendation, or proof of concept

### Bug
A defect where the system does not work as expected.

Example:
- A student enters valid login credentials, but the app shows an error

### Issue
A tracked item representing a problem, concern, or work item. Its exact meaning depends on the tool and workflow.

Example:
- A third-party API is unavailable, blocking registration

### Quick Comparison
| Type | Main Purpose | Example |
|---|---|---|
| Epic | Large objective | Build a student management system |
| Feature | Major capability | Student registration |
| User Story | User requirement | Student can create an account |
| Spike | Research/investigation | Compare authentication approaches |
| Bug | Fix incorrect behavior | Login fails with valid credentials |
| Issue | Track a problem or work item | External API is unavailable |

### Typical hierarchy
Epic → Feature → User Story → Task

A Bug or Spike may be linked to a story or feature, but they do not always fit into a fixed hierarchy.

### Interview tip
- Epic = large business goal
- Feature = major capability
- User Story = user need
- Spike = investigation
- Bug = defect
- Issue = general tracked problem/work item

---

## 4. Statuses on Jira and Azure DevOps Boards

### Common board statuses
- To Do / New
- In Progress / Active
- In Review / Testing
- Done / Closed

### Typical workflow
To Do → In Progress → Review/Testing → Done

### Jira vs Azure DevOps
| Work Item | Jira (common examples) | Azure DevOps (common examples) |
|---|---|---|
| Epic | To Do → In Progress → Done | New → Active → Resolved → Closed |
| Feature | To Do → In Progress → Done | New → Active → Resolved → Closed |
| User Story | To Do → In Progress → Done | New → Active → Resolved → Closed |
| Spike | To Do → In Progress → Done | New → Active → Resolved → Closed |
| Bug | To Do → In Progress → Testing → Done | New → Active → Resolved → Closed |
| Issue | Depends on configured workflow | Depends on the selected process template |

### Important distinction
- A work-item type tells you what the item is (Bug, User Story, Epic).
- A status tells you where it is in the workflow (New, In Progress, Done).

### Example
| Work Item | Example | Possible Status |
|---|---|---|
| Epic | Student Management System | In Progress |
| Feature | Student Registration | In Progress |
| User Story | Student can register | Done |
| Spike | Research email verification options | Done |
| Bug | Registration API returns HTTP 500 | In Testing |
| Issue | Email service dependency is unavailable | Blocked |

### Technical note
- In Jira, workflows define statuses and transitions.
- In Azure DevOps, status states depend on the selected process template, such as Agile, Scrum, Basic, or CMMI.
- A status like Testing may need to be configured depending on the team.

---

## 5. Azure DevOps Fundamentals

### What is Azure DevOps?
Azure DevOps is a Microsoft platform that supports the software development lifecycle through planning, source control, automation, testing, package management, and deployment.

Main services:
- Azure Boards: plan and track work
- Azure Repos: store source code using Git
- Azure Pipelines: automate builds, tests, and deployment
- Azure Test Plans: manage testing
- Azure Artifacts: store packages and dependencies

### Why is Azure DevOps useful?
It helps teams collaborate and automate delivery, improving quality, consistency, traceability, and deployment speed.

---

## 6. Pipelines and CI/CD

### What is a pipeline?
A pipeline is an automated workflow that executes predefined steps to build, test, package, or deploy an application.

### CI (Continuous Integration)
Frequent integration of code changes with automated builds and tests.

Example:
- Developer pushes code
- Pipeline runs tests automatically
- Build fails if checks fail

### CD (Continuous Delivery / Continuous Deployment)
Automated preparation or release of validated code.

- Continuous Delivery: code is ready to deploy, but a human may approve production release
- Continuous Deployment: production deployment happens automatically after validation

### Azure Pipelines Example
```yaml
trigger:
  - main

pool:
  vmImage: ubuntu-latest

steps:
  - script: npm ci
    displayName: Install dependencies

  - script: npm test --if-present
    displayName: Run tests

  - script: npm run build
    displayName: Build application
```

### How to create a pipeline in Azure DevOps
1. Create an Azure DevOps organization and project
2. Push code to Azure Repos or connect an existing repository
3. Create a pipeline using YAML or the visual editor
4. Add triggers, dependencies, tests, and build steps
5. Configure secrets and variables securely
6. Select an agent or pool
7. Add deployment stages and approvals
8. Run the pipeline and fix failures

### How Azure Repos connects to Azure Pipelines
1. Open Azure DevOps project
2. Go to Pipelines
3. Select Azure Repos Git
4. Choose the repository
5. Configure YAML pipeline
6. Set branch triggers
7. Authorize service connections
8. Run and monitor results

### Interview distinction
- Azure Repos stores the code
- Azure Pipelines automates the build, test, and deployment workflow

---

## 7. DevOps Process Lifecycle

### DevOps lifecycle
1. Plan
2. Code
3. Build
4. Test
5. Release
6. Deploy
7. Operate
8. Monitor

### Practical example
For a student management application built with React, Node.js, and MySQL:

| Stage | What happens |
|---|---|
| Plan | Create User Stories and Tasks in Azure Boards or Jira |
| Code | Developers write frontend and backend code and commit to Git |
| Build | Install dependencies and package the application |
| Test | Run automated tests and validation checks |
| Release | Prepare versioned build or artifact |
| Deploy | Publish to test or production environment |
| Operate | Maintain application uptime and configuration |
| Monitor | Review logs, metrics, alerts, and errors |

### Continuous feedback
The DevOps lifecycle is continuous, not strictly linear. Monitoring and feedback from production feed back into planning and development.

---

## 8. DevOps vs Azure DevOps vs GitOps

### DevOps
The broader culture and set of practices for software delivery and operations.

### Azure DevOps
Microsoft’s platform that provides tools for implementing DevOps practices.

### GitOps
A Git-centered operational model where Git is treated as the source of truth for desired system state.

| Topic | Azure DevOps | GitOps |
|---|---|---|
| Purpose | Planning, source control, CI/CD, testing, project delivery | Managing infrastructure and app state via Git |
| Tools | Azure Boards, Repos, Pipelines, Artifacts | Argo CD, Flux, Kubernetes |
| Core idea | Delivery platform | Desired-state automation |

### How they work together
Azure Pipelines can build and test an application, then update a Git repository with the deployment version. A GitOps controller then reconciles the environment with the desired state.

---

## 9. Version Control and Why It Matters

### What is version control?
Version control tracks changes to code and configuration files over time.

### Why it is important in DevOps
- Tracks changes and accountability
- Enables branching and collaboration
- Supports code review and approvals
- Helps reproduce builds and deployments
- Provides a foundation for CI/CD pipelines

### Example
Git enables developers to:
- Work on separate feature branches
- Open pull requests
- Review code before merging
- Revert to earlier versions if needed

### Interview distinction
- Git = version-control system
- GitHub, GitLab, Azure Repos = platforms for hosting Git repositories and collaboration

---

## 10. Docker and Containers

### Difference between Docker and a container
| Term | Meaning |
|---|---|
| Docker | Platform and ecosystem for building and running containers |
| Container | Isolated running instance of an application and its dependencies |

### Example commands
```bash
docker build -t student-api .
docker run -p 3000:3000 student-api
docker ps
```

### Why containers matter in DevOps
Containers make applications portable and consistent across environments.

Benefits:
- Consistent behavior between development and production
- Faster environment setup
- Efficient resource usage
- Easier automation in pipelines

### Virtual Machine vs Container
| Virtual Machine | Container |
|---|---|
| Virtualizes hardware via hypervisor | Isolates processes using OS features |
| Runs a full guest OS | Shares host OS kernel |
| Higher overhead | Lower overhead and faster startup |
| Stronger VM-level isolation boundary | Isolation depends on configuration |

---

## 11. DevOps Architecture

### Azure DevOps architecture
Developers and project managers interact through browser or IDE tools.

Azure DevOps services include:
- Boards: work planning
- Repos: source control
- Pipelines: automation and deployment
- Test Plans: testing
- Artifacts: package management

These services work with self-hosted or Microsoft-hosted build agents and target deployment environments.

### Azure DevOps Services vs Azure DevOps Server
- Azure DevOps Services: cloud-hosted offering from Microsoft
- Azure DevOps Server: self-hosted deployment for internal infrastructure

---

## 12. Security and DevSecOps

### What is a CVE?
CVE stands for Common Vulnerabilities and Exposures. It is a standardized identifier for a publicly disclosed vulnerability.

Example:
- CVE-2026-XXXXX

### What is a vulnerability?
A vulnerability is a weakness in software, configuration, infrastructure, or a process that an attacker could exploit.

Examples:
- Outdated dependencies
- Exposed secrets
- Insecure API authorization
- Unsecured cloud storage

### How DevOps helps manage vulnerabilities
DevSecOps integrates security into the DevOps process.

Key practices:
- Scan dependencies
- Scan container images
- Detect leaked secrets
- Run SAST and DAST
- Apply security patches
- Enforce least privilege and access control
- Monitor systems and investigate alerts

### Example
If a Node.js dependency contains a known CVE, the pipeline can fail the build or block release based on the team’s security policy.

### Interview distinction
- CVE = identifier of a vulnerability
- CVSS = severity score
- A CVE does not automatically mean every application is affected

---

## 13. DevSecOps and Security Practices

### What is DevSecOps?
DevSecOps is the practice of integrating security throughout the software lifecycle rather than as a final step.

It includes:
- Secure coding practices
- Automated security scanning
- Secret protection
- Access control
- Dependency and image scanning
- Continuous monitoring

### Interview point
DevOps emphasizes speed and collaboration; DevSecOps adds security as a shared responsibility across the entire delivery lifecycle.

---

## 14. Common Interview Questions and Answers

### 1. What are the disadvantages of DevOps?
DevOps can be expensive, require strong technical skills, involve complex tool integration, create security risks if pipelines are misconfigured, and need ongoing maintenance.

### 2. What is the difference between a User Story, Spike, Issue, Bug, Feature, and Epic?
- Epic: large objective
- Feature: major capability
- User Story: user need
- Spike: investigation/research
- Bug: defect
- Issue: generic tracked problem

### 3. What are the common statuses on a Jira or Azure DevOps board?
Typical statuses are:
- To Do / New
- In Progress / Active
- In Review / Testing
- Done / Closed

### 4. If I mention DevOps on my resume, will it help me?
Yes, if the role matches the skills you actually have. It helps with ATS alignment, but it must be supported by real knowledge and practical examples.

### 5. What is the DevOps process?
It includes planning, coding, building, testing, releasing, deploying, operating, and monitoring software with continuous feedback.

### 6. What is the difference between CI, CD, and Continuous Deployment?
- CI: build and test code automatically
- CD: prepare validated changes for release
- Continuous Deployment: automatically deploy validated changes to production

### 7. What is Infrastructure as Code (IaC)?
Infrastructure as Code means defining infrastructure in configuration files rather than manually creating it. Tools include Terraform and Bicep.

### 8. What is the difference between Docker and Kubernetes?
- Docker packages and runs containers
- Kubernetes orchestrates and manages containers across a cluster

### 9. What is a build agent in Azure Pipelines?
An agent is the environment that runs pipeline jobs, executes scripts, builds code, runs tests, and publishes artifacts.

### 10. What happens when a pipeline fails?
Investigate the failed step, check logs, identify configuration or dependency issues, fix the root cause, and rerun after verification.

### 11. What is Azure Boards?
Azure Boards is the work-tracking service for planning, backlog management, sprint tracking, and task management.

### 12. What is Jira?
Jira is Atlassian’s project and issue-tracking platform for Agile teams.

### 13. What is Trello?
Trello is a simple board-based task management tool for visual workflows.

### 14. Who owns Jira? Is Atlassian a product-based company?
Jira is owned by Atlassian, a product-based software company that builds software products such as Jira, Confluence, and Trello.

---

## 15. Quick Practice Questions

### Multiple-choice practice
1. A developer pushes code and automated tests run immediately. Which practice is this?
- Continuous Integration

2. What is the difference between a Bug and a User Story?
- A Bug tracks incorrect behavior; a User Story describes a user need.

3. In Jira, is “In Progress” a work-item type?
- No, it is typically a status.

4. What does a Spike primarily help a team do?
- Investigate an uncertain technical or business question.

---

## 16. Resume Guidance for Freshers

### Should you mention DevOps in your resume?
Yes, if you have actually studied or practiced it. It can help with ATS and role relevance, but it should match your real skills.

### How to mention it correctly
#### If you only studied fundamentals
- DevOps Fundamentals: CI/CD concepts, Git, Azure DevOps basics, software deployment workflows

#### If you practiced Azure Pipelines
- DevOps: Azure Repos, YAML CI pipelines, automated build and test workflows, Git, CI/CD fundamentals

#### If you also practiced Docker
- DevOps: Git, Azure DevOps, CI/CD automation, Docker containers, application deployment workflows

### Recommendation for BCA freshers
Before listing advanced DevOps tools, build one small project using:
- Git
- Automated CI pipeline
- Automated tests
- Docker or deployment workflow

A project you can explain confidently is stronger than a long list of tools without real understanding.

---

## 17. Preparation Priority for Placements

For a fresher, the best order is:
1. Git and GitHub
2. CI/CD fundamentals
3. Azure DevOps basics
4. Docker and Linux
5. Cloud and security fundamentals
6. Practical troubleshooting scenarios

### High-value topics to prepare
- Git: commits, branches, merges, pull requests, conflicts
- CI/CD: triggers, stages, artifacts, pipeline failures
- Azure DevOps: Boards, Repos, Pipelines
- Linux: commands, permissions, logs, processes
- Docker: images, containers, volumes, ports
- Cloud basics: VMs, networking, IAM, storage
- Security: CVEs, secrets, dependency scanning, least privilege
- Monitoring: logs, metrics, alerts, incident response

---

## 18. Final Interview Summary

DevOps is a delivery approach that combines tools, automation, collaboration, security, and feedback loops to improve software quality and speed. Azure DevOps provides a practical platform for implementing this workflow using Boards, Repos, Pipelines, Artifacts, and Test Plans. Jira is a popular alternative for Agile planning and issue management. Trello is a lightweight visual planning tool for simpler workflows.

### Core message to remember
DevOps is not only about automation. It is about improving how teams plan, build, test, deploy, monitor, and learn from software delivery.

