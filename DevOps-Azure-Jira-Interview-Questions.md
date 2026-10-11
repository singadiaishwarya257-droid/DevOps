# DevOps Interview Questions and Answers

## 1. Project Tracking Tools

### 1. What is Azure Boards?

**Answer:** Azure Boards is the work-tracking service in Azure DevOps. Teams use it to plan, assign, prioritize, and track development work through work items, backlogs, Kanban boards, and sprints.

Depending on the process template, work-item types can include Epics, Features, User Stories, Tasks, Bugs, and Issues.

**Example:** For a student management application, a team can create a User Story for student registration, assign implementation Tasks to developers, and track progress from To Do to Done.

### 2. What is Jira?

**Answer:** Jira is a project and issue-tracking tool developed by Atlassian. It supports Agile methods, Scrum and Kanban boards, sprint planning, bug tracking, configurable workflows, and reporting.

**Example:** A developer creates a Bug for a failed login API, assigns it to the backend developer, tracks its status, and verifies the fix.

### 3. What is Trello?

**Answer:** Trello is a visual project-management tool that organizes work using boards, lists, and cards. It is particularly useful for straightforward task management and collaborative workflows.

**Example:** A board can have three lists — To Do, In Progress, and Done. Each card represents a task such as designing a login page.

### 4. What is the difference between Azure Boards, Jira, and Trello?

| Feature | Azure Boards | Jira | Trello |
| --- | --- | --- | --- |
| Main purpose | Work tracking integrated with Azure DevOps | Issue tracking and Agile project management | Visual task management |
| Agile support | Scrum and Kanban | Scrum and Kanban | Primarily visual Kanban workflows |
| Integration strength | Azure Repos, Pipelines, and the Microsoft ecosystem | Atlassian ecosystem and integrations | Simple collaboration and integrations |
| Best suited for | Teams using Azure DevOps | Teams needing detailed issue tracking and configurable workflows | Small teams and simple projects |

**Interview tip:** All three can track work. The best choice depends on workflow complexity, reporting needs, integrations, and the team's existing tools.

### 5. What are Epics, Features, User Stories, Tasks, Bugs, Spikes, and Issues?

**Answer:** These work-item types represent different kinds or sizes of work. Their exact names and behavior can vary by tool and process template.

| Type | Meaning | Example |
| --- | --- | --- |
| Epic | A large business objective that can be divided into smaller items | Build an online student management system |
| Feature | A major capability that delivers user or business value | Student registration and profile management |
| User Story | A requirement expressed from the user's perspective | “As a student, I want to register so that I can access my account.” |
| Task | A specific unit of implementation work | Create the registration API and validate input fields |
| Bug | A defect in existing or expected behavior | Registration fails even when all fields are valid |
| Spike | A time-boxed research or investigation task used to reduce uncertainty | Compare JWT and session-based authentication |
| Issue | A general tracked item for work, a problem, or a concern; its meaning depends on the tool and workflow | A third-party API is unavailable and blocks registration |

A User Story typically describes what a user needs and why and may include acceptance criteria. A Spike should produce findings, a recommendation, or a proof of concept; it does not necessarily produce a production feature. A Bug records behavior that needs to be fixed and verified.

**Typical planning hierarchy:**

```text
Epic
└── Feature
    └── User Story
        └── Task / implementation work
```

Bugs and Spikes can be linked to relevant Stories or Features, but they do not necessarily occupy a fixed level in this hierarchy. An Issue is a general term in Jira; in Azure DevOps, formal work-item types depend on the selected process template.

### 6. What statuses are used on Jira or Azure DevOps boards?

**Answer:** A status represents the current state of a work item. The available statuses and transitions depend on the team's workflow and tool configuration.

| Common stage | Jira example | Azure Boards example | Meaning |
| --- | --- | --- | --- |
| Waiting to start | To Do | New | Work is created and waiting |
| Being worked on | In Progress | Active | A team member is working on it |
| Review or validation | In Review or Testing | Resolved or a configured state | Work is being reviewed or tested |
| Complete | Done | Closed | Work meets the team's completion criteria |

Teams may also use statuses such as Blocked, Reopened, Resolved, or Ready for Deployment. These examples are illustrative, not universal defaults.

- **Jira:** Workflows define statuses and transitions. Teams can customize them, and different issue types can use different workflows.
- **Azure DevOps:** Work-item states depend on the selected process, such as Basic, Agile, Scrum, or CMMI. The Agile process commonly uses New, Active, Resolved, and Closed for User Stories and Bugs.
- A status such as Testing is not guaranteed to exist by default; it may need to be configured.
- Issue is a standard work-item type in the Azure DevOps Basic process. Agile commonly uses User Story, while Scrum uses Product Backlog Item.

**Example:** In a student registration project, a Bug for an API returning HTTP 500 might be In Testing, while an Epic for the full Student Management System remains In Progress.

**Is a status the same as a work-item type?** No. A type describes what an item represents, such as a Bug or User Story. A status describes its current progress, such as New, In Progress, or Done.

**Important:** A sprint is a time-boxed iteration, not a status. A board displays work status; a sprint defines a period for completing planned work.

---

## 2. Azure DevOps Fundamentals

### 7. What is Azure DevOps?

**Answer:** Azure DevOps is a Microsoft platform that supports the software development lifecycle through planning, source control, build automation, testing, package management, and deployment.

Its main services are:

- **Azure Boards:** Plan and track work.
- **Azure Repos:** Store and manage source code using Git or Team Foundation Version Control.
- **Azure Pipelines:** Automate builds, tests, and deployments.
- **Azure Test Plans:** Manage and execute manual and exploratory testing.
- **Azure Artifacts:** Host and share packages such as NuGet, npm, and Maven packages.

**Interview answer:** Azure DevOps helps teams collaborate and automate software delivery, enabling repeatable builds, faster releases, traceability, and more reliable deployments.

### 8. What is a pipeline?

**Answer:** A pipeline is an automated workflow that executes predefined steps to build, test, package, or deploy an application.

Two commonly discussed pipeline practices are:

- **Continuous Integration (CI):** Frequently integrates code changes and runs automated builds and tests.
- **Continuous Delivery or Continuous Deployment (CD):** Automates preparing validated software for release or releasing it to target environments.

**Example:** When a developer pushes code to Git, a pipeline can install dependencies, run tests, build a React frontend and Node.js backend, and deploy the application if all checks pass.

### 9. How do you create a pipeline in Azure DevOps?

**Answer:** I would follow these steps:

1. Create an Azure DevOps organization and project.
2. Push the application code to Azure Repos, or connect another supported repository.
3. Configure a pipeline using the visual editor or a YAML file.
4. Define triggers, dependencies, build steps, and automated tests.
5. Configure required variables and secrets securely.
6. Select an agent or agent pool to run the job.
7. Add deployment stages and environment approvals if required.
8. Run the pipeline, inspect logs, and fix failures.
9. Configure branch policies and monitoring for reliable delivery.

A YAML pipeline is useful because its configuration can be version-controlled alongside the application code.

**Simplified YAML example:**

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

This example assumes the repository root contains a suitable `package.json`. A real deployment pipeline would add application-specific configuration, artifacts, and deployment steps.

### 10. How do you connect Azure Repos to Azure Pipelines?

**Answer:** Azure Repos can be connected to Azure Pipelines so that code changes automatically trigger builds and tests.

**Workflow:**

1. Open the Azure DevOps project and select Pipelines.
2. Create a new pipeline and select Azure Repos Git.
3. Choose the repository containing the application.
4. Configure the YAML pipeline file.
5. Set the branch trigger, such as `main`.
6. Authorize required service connections and permissions.
7. Run the pipeline and verify its logs.

**Example:** A developer pushes a Node.js API update to the `main` branch. Azure Pipelines detects the change, runs tests, builds the application, and proceeds with deployment if configured.

**Interview distinction:** Azure Repos stores the code; Azure Pipelines automates what happens after code changes.

### 11. What is the difference between Azure DevOps and GitOps?

**Answer:** Azure DevOps is a software delivery platform. GitOps is an operational approach in which Git stores the desired state of a system and automated controllers reconcile the actual environment with that state.

| Azure DevOps | GitOps |
| --- | --- |
| A platform with planning, source control, CI/CD, testing, and packages | A Git-centered operational methodology |
| Can run CI/CD pipelines | Commonly uses reconciliation controllers to apply desired state |
| Supports many deployment methods | Often used for Kubernetes and infrastructure configuration |
| Example: Azure Pipelines | Examples: Argo CD and Flux |

**How they work together:** Azure Pipelines can test an application and update a Git repository with a new deployment image version. A GitOps controller then detects the change and reconciles the target environment.

**High-level point:** GitOps is not a replacement for all of Azure DevOps. The two can complement each other.

### 12. What are the advantages of DevOps?

**Answer:** DevOps combines development and operations practices to improve the speed, quality, and reliability of software delivery.

- **Faster delivery:** Automated builds, tests, and deployments reduce manual work.
- **Improved quality:** Automated testing identifies defects earlier.
- **Better collaboration:** Developers and operations teams share responsibility.
- **Consistency:** Infrastructure as Code and repeatable pipelines reduce configuration differences.
- **Faster recovery:** Monitoring, rollback strategies, and smaller releases help teams respond to failures.
- **Traceability:** Version control and pipeline logs help teams investigate changes.

**Example:** Instead of manually copying application files to a server after every code change, a team can use a pipeline to test, package, and deploy the application consistently.

### 13. What is version control, and why is it important in DevOps?

**Answer:** Version control tracks changes to source code and configuration files over time. It lets teams collaborate, compare changes, create branches, and restore earlier versions when necessary.

**Example:** Git enables developers to work on separate feature branches, submit pull requests, review code, and merge approved changes.

Version control provides:

- Change history and accountability.
- Branching and collaboration.
- Code review and approval workflows.
- Reproducible builds and deployment configurations.
- A foundation for automated CI/CD pipelines.

**Interview distinction:** Git is a version-control system. GitHub, GitLab, and Azure Repos are platforms that host repositories and provide collaboration features.

---

## 3. Docker, Containers, and Deployment

### 14. What is the difference between Docker and a container?

**Answer:** Docker is a platform and ecosystem for building, distributing, and running containerized applications. A container is an isolated running instance of an application and its required dependencies.

| Docker | Container |
| --- | --- |
| Tools and platform for container workflows | The running, isolated application environment |
| Builds images and runs containers | Executes the application from an image |
| Provides commands and container-management capabilities | Uses the host operating system's kernel |
| Example: `docker build` | Example: a running Node.js API container |

A Docker image is the packaged, largely immutable template from which containers are created.

**Useful commands:**

```sh
docker build -t student-api .
docker run -p 3000:3000 student-api
docker ps
```

The first command builds an image, the second starts a container and maps port 3000, and the third lists running containers.

### 15. What is a container, and how does it help in DevOps?

**Answer:** A container packages an application and its dependencies into an isolated runtime environment. It helps DevOps teams run applications consistently across development, testing, and production.

- **Without containers:** An application might work on a developer's laptop but fail on a server because of differences in dependencies or runtime versions.
- **With containers:** Teams can package the required Node.js runtime and application dependencies into an image and use that image across supported environments.

Benefits include portability, faster environment setup, efficient resource usage, and easier integration with automated pipelines.

### 16. What is the difference between a virtual machine and a container?

| Virtual machine (VM) | Container |
| --- | --- |
| Virtualizes hardware through a hypervisor | Isolates processes using operating-system features |
| Usually runs a full guest OS | Shares the host kernel |
| Generally has higher resource overhead | Generally has lower overhead and starts faster |
| Provides a VM-level isolation boundary | Isolation depends on container and host configuration |

**Interview-level point:** Containers are not inherently equivalent to virtual machines in security isolation. Both need appropriate configuration and security controls.

---

## 4. DevOps Process and Architecture

### 17. What is the DevOps process, and how does it work?

**Answer:** The DevOps process is a continuous lifecycle of planning, coding, building, testing, releasing, deploying, operating, and monitoring software. Feedback from production is used to improve the next development cycle.

| Stage | Example tools or activity |
| --- | --- |
| Plan | Azure Boards or Jira |
| Code | Git or Azure Repos |
| Build and test | Azure Pipelines and automated tests |
| Package | Versioned artifacts or container images |
| Deploy | Test, staging, or production environments |
| Operate and monitor | Logs, metrics, and alerts |

**Example:** For a React frontend and Node.js backend, a developer pushes a change to Git. The pipeline installs dependencies, runs tests, builds the application, creates an artifact or image, and deploys it to a test environment. After validation, it can promote the release to production.

These stages are commonly shown as a lifecycle, but real DevOps workflows are continuous rather than strictly linear. Security, testing, and monitoring can span multiple stages.

### 18. What is the architecture of Azure DevOps?

**Answer:** Azure DevOps uses a service-oriented architecture in which different services support work planning, source control, automated delivery, testing, and package management.

```text
Developers and project managers
  Browser, IDE, or Git client
                |
                v
         Azure DevOps
  Boards      - Planning
  Repos       - Source control
  Pipelines   - CI/CD
  Test Plans  - Testing
  Artifacts   - Package management
                |
                v
Build agents and target environments
  Build, test, deploy, and operate applications
```

Additional components include identity and access management, service connections, permissions, audit capabilities, and integrations.

**Important distinction:** Azure DevOps Services is Microsoft's cloud-hosted offering. Azure DevOps Server is the self-hosted product for organizations that need to operate it within their own infrastructure. Exact architecture and integrations vary by deployment model.

### 19. How can Azure DevOps and GitOps work together in a deployment architecture?

**Answer:** Consider an application deployed to Kubernetes:

1. A developer pushes source code to Azure Repos.
2. Azure Pipelines builds the application, runs tests, and creates a container image.
3. The pipeline publishes the image to a container registry.
4. A deployment configuration in Git is updated with the approved image version.
5. A GitOps controller, such as Argo CD or Flux, detects the desired-state change.
6. The controller reconciles the Kubernetes cluster with that configuration.
7. Monitoring identifies issues, and the team uses feedback to improve or roll back the release.

**Why this matters:** CI verifies and packages application changes; GitOps continuously reconciles the target environment with version-controlled desired state.

### 20. What are the disadvantages or challenges of DevOps?

**Answer:** DevOps improves collaboration and automates software delivery, but implementation can introduce challenges involving cost, skills, security, and process management.

| Challenge | Explanation | Practical example |
| --- | --- | --- |
| High initial cost | Tools, cloud infrastructure, and training can require investment | Setting up cloud environments and CI/CD pipelines |
| Skill requirements | Teams need knowledge of automation, scripting, cloud, security, and monitoring | Debugging a failed deployment pipeline |
| Complex implementation | Integrating multiple tools and workflows can be difficult | Connecting Git, automated tests, container registries, and deployments |
| Security risks | Misconfigured pipelines or exposed credentials can create vulnerabilities | A leaked deployment token gives unauthorized access |
| Maintenance overhead | Pipelines, dependencies, infrastructure, and monitoring require ongoing maintenance | Updating an outdated build agent or fixing a broken pipeline |
| Resistance to change | Teams may struggle to adopt shared ownership and automation | Developers and operations teams continue working in isolated silos |
| Automation failures | A faulty pipeline can repeatedly deploy an incorrect build | An inadequate test suite allows a defective release into production |

**High-level interview point:** DevOps is not just a collection of tools. It requires the right culture, processes, automation, security practices, and monitoring. Poor implementation can increase complexity instead of improving delivery.

---

## 5. Security Fundamentals

### 21. What is a CVE?

**Answer:** CVE stands for Common Vulnerabilities and Exposures. It is a standardized identifier assigned to a publicly disclosed cybersecurity vulnerability.

**Example format:** `CVE-2026-XXXXX` (the exact identifier depends on the vulnerability).

A CVE identifies a specific vulnerability; it does not itself describe every detail of its severity or provide a fix.

### 22. What is a vulnerability, and how does DevOps help manage it?

**Answer:** A vulnerability is a weakness in software, configuration, infrastructure, or a process that an attacker could exploit.

Examples include outdated dependencies, exposed credentials, insecure API authorization, and misconfigured cloud storage.

DevOps teams address vulnerabilities through DevSecOps practices:

- Scan dependencies and container images.
- Detect leaked secrets.
- Run static application security testing (SAST).
- Scan running applications using dynamic application security testing (DAST).
- Apply security patches and update vulnerable dependencies.
- Enforce access controls and secure deployment configurations.
- Monitor systems and investigate security alerts.

**Example:** If a Node.js dependency has a known vulnerability, a pipeline can detect the affected package, fail a security gate based on the team's policy, and require remediation before release.

**Interview distinction:** A CVE is an identifier for a publicly disclosed vulnerability; a CVSS score assesses its severity. A CVE identifier alone does not mean every application is affected.

### 23. What is DevSecOps?

**Answer:** DevSecOps integrates security practices throughout the software development and delivery lifecycle rather than treating security as a final checkpoint.

It includes secure coding, automated security scanning, dependency management, secrets protection, access control, and continuous monitoring.

**Interview point:** DevOps emphasizes collaboration and delivery automation; DevSecOps makes security a shared responsibility throughout that process.

---

## 6. CI/CD and Interview Practice

### 24. What is the difference between Continuous Integration, Continuous Delivery, and Continuous Deployment?

| Concept | Meaning |
| --- | --- |
| Continuous Integration (CI) | Frequently integrates code and automatically builds and tests changes |
| Continuous Delivery | Keeps validated changes ready for release, typically with a manual production approval |
| Continuous Deployment | Automatically releases every change that passes the required checks to production |

**Interview example:** If every successful build is ready to deploy but a manager must approve the production release, that is continuous delivery. If validated changes automatically go to production, that is continuous deployment.

### 25. What is Infrastructure as Code (IaC)?

**Answer:** Infrastructure as Code means defining and managing infrastructure using machine-readable configuration files rather than relying entirely on manual setup.

Tools include Terraform, Azure Bicep, and Azure Resource Manager templates.

**Example:** Instead of manually creating a virtual network and virtual machines, a team defines them in configuration files, reviews the changes, and deploys them consistently.

Benefits include repeatability, version control, easier recovery, and reduced configuration drift.

### 26. What is the difference between Docker and Kubernetes?

**Answer:** Docker provides tools for building and running containers, while Kubernetes orchestrates containerized applications across a cluster of machines.

- **Docker:** Build an image and run a container.
- **Kubernetes:** Manage container scheduling, scaling, service discovery, and recovery across a cluster.

**Example:** Docker packages a Node.js application into a container image. Kubernetes manages multiple instances of that application and replaces failed instances according to its configuration.

### 27. What is a build agent in Azure Pipelines?

**Answer:** An agent is the computing environment that executes pipeline jobs and steps.

Azure Pipelines supports:

- **Microsoft-hosted agents:** Microsoft provides and manages the build environment.
- **Self-hosted agents:** The organization manages the machine or environment used to run jobs.

Agents can execute commands, run tests, build applications, and publish artifacts according to the pipeline definition.

### 28. What happens when an Azure DevOps pipeline fails?

**Answer:** I would investigate the failed stage and identify the root cause rather than rerunning the pipeline blindly.

**Troubleshooting process:**

1. Identify the failed job and step.
2. Inspect logs and error messages.
3. Check dependencies, configuration, environment variables, and permissions.
4. Reproduce the failure locally when possible.
5. Fix the issue and run the pipeline again.
6. Verify that the change passes tests and does not introduce regressions.

**Example:** A Node.js pipeline may fail because `npm ci` cannot resolve dependencies, a test assertion fails, or the build command is incorrect.

---

## 7. Company and Placement Preparation

### 29. Who owns Jira? Is Atlassian a product-based company?

**Answer:** Jira is developed by Atlassian. Atlassian is a software company that develops products such as Jira, Confluence, and Trello.

Jira is a product, while Atlassian is the company behind it. Atlassian is commonly described as a product-based software company because it develops and sells software products to customers.

### 30. What is the difference between a product-based and a service-based company?

| Product-based company | Service-based company |
| --- | --- |
| Develops and maintains its own products or platforms | Provides technology services and solutions to clients |
| Product roadmap and customer adoption are important | Client requirements and project delivery are important |
| Examples: Atlassian, Microsoft, Adobe | Examples: Accenture, TCS, Infosys |

These are broad categories, not strict boundaries. Many companies operate both product and service businesses.

### 31. What DevOps questions should a fresher prepare for placements?

**Answer:** Focus on these high-value topics:

- **Git fundamentals:** Commits, branches, merging, and pull requests.
- **CI/CD:** Pipeline stages, triggers, artifacts, and build failures.
- **Azure DevOps:** Boards, Repos, Pipelines, and service connections.
- **Linux:** Common commands, permissions, processes, and logs.
- **Docker:** Images, containers, volumes, and port mapping.
- **Cloud fundamentals:** Virtual machines, networking, storage, and IAM.
- **Networking:** DNS, HTTP/HTTPS, ports, and load balancing.
- **Security:** CVEs, secrets, dependency scanning, and least privilege.
- **Monitoring:** Logs, metrics, alerts, and incident response.
- **Practical troubleshooting:** Identifying the cause of a failed build or deployment.

For higher-level interviews, also prepare branching strategies, environment promotion, rollback strategies, Infrastructure as Code, deployment approvals, and Kubernetes fundamentals.

### 32. Will BCA freshers get DevOps questions during placements?

**Answer:** It is possible. BCA freshers may be asked DevOps questions when applying for cloud, software development, platform engineering, or DevOps-related roles. The exact questions depend on the company, job description, and interview round.

Interviewers commonly assess foundational knowledge and the ability to explain a practical workflow. Advanced production architecture is more likely to be emphasized in roles that specifically require prior DevOps experience.

### 33. Should you mention DevOps and Azure DevOps on your resume?

**Answer:** Yes, if you have actually learned or practiced them. Listing a technology can help with relevant ATS keywords, but interviewers may ask follow-up questions about anything you mention. Use wording that matches your actual experience.

**If you have studied the fundamentals:**

> Familiarity with DevOps principles, CI/CD concepts, Git-based version control, and Azure DevOps fundamentals.

**If you have created and tested a pipeline:**

> Hands-on experience configuring CI pipelines, automating application builds and tests, and managing source code using Git and Azure DevOps.

**If you have also practiced Docker:**

> Familiarity with Docker image creation, container execution, and integrating container builds into CI/CD workflows.

Do not claim hands-on experience with Azure, Docker, Kubernetes, or GitOps solely because you studied their definitions.

**Will it improve your ATS score?** It may improve keyword alignment when the job description asks for those skills, but adding the word “DevOps” alone does not guarantee a higher ATS score or an interview call.

For a BCA fresher targeting software development roles, prioritize:

1. Git and GitHub: commits, branches, merges, conflicts, and pull requests.
2. CI/CD fundamentals: how code moves from commit to testing and deployment.
3. Azure DevOps: Boards, Repos, Pipelines, and YAML.
4. Docker and Linux: container basics, commands, permissions, and logs.
5. Cloud and security fundamentals: deployment, IAM, CVEs, and secret management.
6. Practical scenarios: failed pipelines, deployment errors, and rollback decisions.

For a full-stack developer role, prioritize programming and problem-solving, React or Node.js, REST APIs, SQL, testing, and debugging. DevOps, CI/CD, Docker, and cloud deployment are supporting skills.

**Recommendation:** Build and document one small project using Git, a CI pipeline, automated tests, and Docker. A project you can explain confidently is more valuable than listing many tools without practical understanding.

### 34. What is the DevOps lifecycle, and what happens at each stage?

**Interview-ready answer:** DevOps is a combination of practices, tools, and cultural principles that brings development and operations teams together to deliver software faster and more reliably. It uses automation, continuous feedback, and monitoring throughout the software development lifecycle.

| Stage | What happens | Example tools or outputs |
| --- | --- | --- |
| Plan | Create and prioritize work | User Stories and tasks in Azure Boards or Jira |
| Code | Develop and commit application changes | Git or Azure Repos |
| Build | Install dependencies and compile or package the application | Azure Pipelines |
| Test | Run automated tests and check application behavior | Unit, integration, and other automated tests |
| Release | Prepare and version the validated build | Versioned artifacts |
| Deploy | Publish the application to a test or production environment | Cloud or server environment |
| Operate | Run the application and manage configuration and availability | Application and infrastructure operations |
| Monitor | Track logs, errors, performance, and availability | Logs, metrics, and alerts |

**Example:** Suppose you are developing a student management application using React, Node.js, and MySQL. A developer commits a change using Git; the pipeline builds and tests it, creates a versioned artifact, and deploys it to a test environment. After validation, the release can be promoted to production. Monitoring provides feedback for the next planning and development cycle.

**How does Azure DevOps support this process?**

- Azure Boards plans and tracks work.
- Azure Repos stores source code.
- Azure Pipelines automates builds, tests, and deployments.
- Azure Test Plans supports test management.
- Azure Artifacts stores and shares packages.

**What is the difference between DevOps and Azure DevOps?** DevOps is the broader culture and set of practices for improving software delivery and operations. Azure DevOps is Microsoft's platform that provides tools to implement many of those practices.

**Why is DevOps important?** It reduces repetitive manual work, enables faster feedback, improves collaboration, supports consistent deployments, and helps teams detect and recover from failures more effectively.

---

## 8. Practice Questions

Choose the best answer for each question.

### 1. A developer pushes code, and automated tests run immediately. Which practice is this?

- A. Continuous Integration (CI)
- B. Continuous Deployment
- C. Monitoring

**Correct answer:** A. Continuous Integration (CI)

### 2. What is the difference between a Bug and a User Story?

- A. They mean the same thing.
- B. A Bug tracks incorrect behavior; a User Story describes a user need.
- C. A User Story only describes technical errors.

**Correct answer:** B. A Bug tracks incorrect behavior; a User Story describes a user need.

### 3. In Jira, is “In Progress” a work-item type?

- A. Yes.
- B. No, it is typically a status.
- C. It is always an Epic.

**Correct answer:** B. No, it is typically a status.

### 4. What does a Spike primarily help a team do?

- A. Release every change to production.
- B. Investigate an uncertain technical or business question.
- C. Close all Bugs.

**Correct answer:** B. Investigate an uncertain technical or business question.

---

## Final Summary

DevOps is a delivery approach that combines tools, automation, collaboration, security, and feedback loops to improve software quality and speed. Azure DevOps provides a practical platform for implementing this workflow using Boards, Repos, Pipelines, Artifacts, and Test Plans. Jira is a popular alternative for Agile planning and issue management. Trello is a lightweight visual planning tool for simpler workflows.

### Core message to remember
DevOps is not only about automation. It is about improving how teams plan, build, test, deploy, monitor, and learn from software delivery.
