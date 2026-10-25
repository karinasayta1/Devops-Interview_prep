# **Core Concepts - DevOps, SRE & Platform Engineering (200 Questions)**

Welcome to the **Core Concepts** master collection containing **200 comprehensive interview questions and detailed answers** covering DevOps Fundamentals, Site Reliability Engineering (SRE), Platform Engineering, DORA Metrics, Cloud FinOps, SDLC Integration, and Architectural Frameworks.

---

## 🟢 **Part 1: DevOps Fundamentals & Culture (Questions 1–50)**

### **1. What is DevOps and what core problem does it solve?**
**Answer:** DevOps is a culture and set of practices that brings Development and IT Operations together. It solves the problem of silos and poor collaboration between these teams by promoting automation, continuous integration and delivery, and shared responsibility. This helps organizations release software faster and more reliably.

### **2. What are the Three Ways of DevOps?**
**Answer:**
The Three Ways of DevOps are Flow, Feedback, and Continuous Learning and Experimentation. Flow focuses on moving work quickly from Development to Operations and customers by reducing bottlenecks and automating delivery. Feedback focuses on creating fast feedback loops from production to Development through monitoring and telemetry. Continuous Learning and Experimentation encourages teams to learn from failures, share knowledge, and experiment to improve reliability and performance.

### **3. What is the difference between DevOps and Agile?**
**Answer:** Agile is a software development approach that focuses on iterative development, rapid customer feedback, and adapting to changing requirements. DevOps extends collaboration beyond development into testing, infrastructure provisioning, deployment, monitoring, and operations. In simple terms, Agile helps teams develop software incrementally, while DevOps helps them deliver, operate, and maintain that software reliably. They complement each other.

### **4. What are DORA Metrics? List all four core metrics.**
**Answer:**
1. **Deployment Frequency (DF):** How often an organization deploys code to production.
2. **Lead Time for Changes (LTFC):** Time from code commit to running in production.
3. **Change Failure Rate (CFR):** Percentage of deployments requiring immediate hotfix/rollback.
4. **Time to Restore Service (TTRS / MTTR):** Time to recover from a production outage.

DORA metrics are used to measure software delivery performance and operational stability. The four traditional core metrics are Deployment Frequency, which measures how often code is deployed to production; Lead Time for Changes, which measures the time from code commit to production; Change Failure Rate, which measures the percentage of deployments that require remediation; and Time to Restore Service, which measures how quickly service is recovered after a production failure.

### **5. What benchmarks define an "Elite" DORA performer?**
**Answer:** Elite teams achieve: Deployment Frequency on-demand (multiple times per day), Lead Time for Changes $< 1$ hour, Change Failure Rate between 0%–15%, and Time to Restore Service $< 1$ hour.

### **6. What is Continuous Integration (CI)?**
**Answer:** Continuous Integration (CI) is an engineering practice in which developers frequently integrate their code into a shared repository. Each integration triggers automated processes such as building the application, linting, and running unit and integration tests. CI helps detect bugs and integration issues early, reducing the cost of fixing them and keeping the codebase healthy.

### **7. What is Continuous Delivery (CD) vs Continuous Deployment (CD)?**
**Answer:** Continuous Delivery automates the build, testing, and preparation of software so that it is always ready for release, but production deployment typically requires manual approval. Continuous Deployment goes one step further by automatically deploying every change that passes the required checks directly to production without manual release approval. The key difference is the manual approval gate.

### **8. What is Infrastructure as Code (IaC)?**
**Answer:** Infrastructure as Code (IaC) is the practice of provisioning and managing infrastructure using machine-readable configuration files instead of manually configuring resources through a console. It allows infrastructure to be automated, version-controlled, repeatable, and consistent. Common examples include Terraform HCL, AWS CloudFormation templates, and Kubernetes YAML manifests.

### **9. What is Configuration Drift?**
**Answer:** Configuration drift occurs when the actual state of infrastructure differs from its desired state defined in Infrastructure as Code. It can happen when someone manually changes resources through a cloud console or server, or when systems change outside the IaC workflow. Drift can be detected by comparing the actual infrastructure with the declared configuration, for example, using Terraform plan.

### **10. What is Immutable Infrastructure?**
**Answer:** Immutable Infrastructure is an approach in which existing servers or infrastructure instances are not modified in place after deployment. When an update is required, a new image or instance is built, tested, and deployed, and the old instance is replaced. This improves consistency, repeatability, and rollback capabilities.

### **11. What is the "You Build It, You Run It" model?**
**Answer:** You Build It, You Run It’ is a DevOps ownership model associated with Werner Vogels, CTO of Amazon. It means the engineering team that builds a service is also responsible for deploying, operating, monitoring, and supporting it in production. This encourages end-to-end ownership, faster feedback, and greater accountability for service reliability.

### **12. What is Shift-Left Security (DevSecOps)?**
**Answer:** Shift-Left Security, also known as a key practice in DevSecOps, means integrating security checks early in the software development lifecycle instead of leaving them until the end. Teams automate checks such as SAST, SCA, secret scanning, and container image scanning in their development workflow and CI/CD pipelines. This helps identify and fix vulnerabilities earlier, reducing remediation costs and security risks.

### **13. What is a Monolith vs Microservices Architecture?**
**Answer:** monolithic architecture packages an application's components, such as UI, business logic, and data access, into a single application and deployment unit. Microservices architecture breaks the application into smaller, loosely coupled services that can be developed, deployed, and scaled independently. These services communicate through network APIs or messaging systems such as REST, gRPC, or Kafka. Monoliths are often simpler to start with, while microservices offer greater deployment and scaling flexibility at the cost of additional distributed-system complexity.

### **14. What are the Twelve Factors of the 12-Factor App?**
**Answer:** 1. Codebase, 2. Dependencies, 3. Config, 4. Backing Services, 5. Build/Release/Run, 6. Processes, 7. Port Binding, 8. Concurrency, 9. Disposability, 10. Dev/Prod Parity, 11. Logs, 12. Admin Processes.

### **15. What is Trunk-Based Development?**
**Answer:** A branching strategy where all developers commit small, frequent changes directly to a single shared branch (`main`), avoiding long-lived feature branches and merge conflicts.

### **16. What is GitFlow and why is it often considered an anti-pattern for CI/CD?**
**Answer:** GitFlow is a branching model that uses separate branches for development, features, releases, and hotfixes. It can slow CI/CD when branches live too long because integration happens less frequently, increasing merge conflicts and delaying feedback. Trunk-Based Development is often preferred for continuous delivery.

### **17. What is a Blue-Green Deployment?**
**Answer:** Blue-Green Deployment uses two production-like environments. One serves live traffic while the new version is deployed and verified in the other. Traffic is then switched to the new environment, and rollback can be quick by switching back, provided the old version remains compatible.

### **18. What is a Canary Deployment?**
**Answer:** Canary Deployment releases a new version to a small subset of users first. The team monitors metrics such as error rate and latency, then gradually increases traffic if the release is healthy. If problems occur, the rollout can be stopped or rolled back.

### **19. What is a Feature Flag (Toggle)?**
**Answer:** A Feature Flag is a mechanism that controls whether a feature is enabled at runtime. It separates deployment from release, allowing teams to enable, disable, or gradually roll out features without necessarily redeploying the application.

### **20. What is Dark Launching?**
**Answer:** Dark Launching introduces new functionality into production without exposing it to users. The new system may process shadow traffic or live data in the background so the team can validate performance and behavior before enabling the feature.

### **21. What is Observability vs Monitoring?**
**Answer:** Monitoring tracks predefined metrics and alerts on known conditions, while observability helps engineers understand a system’s internal state from its outputs, such as metrics, logs, and traces, including when the cause of a problem is not known in advance.

### **22. What are the Three Pillars of Observability?**
**Answer:** The three traditional pillars of observability are metrics, logs, and distributed traces. Metrics show numerical trends, logs provide event details, and traces help follow a request across multiple services.

### **23. What is Chaos Engineering?**
**Answer:** Chaos Engineering is the practice of deliberately introducing controlled failures into a system to test its resilience, validate recovery mechanisms, and identify weaknesses before unexpected incidents occur.

### **24. What is FinOps?**
**Answer:** FinOps is a collaborative approach to managing and optimizing cloud costs. It brings engineering, finance, and business teams together to improve cost visibility, accountability, and cloud spending efficiency while meeting performance and business goals.

### **25. What is SRE (Site Reliability Engineering)?**
**Answer:** Site Reliability Engineering applies software engineering principles to operations problems to improve system reliability, availability, and scalability. SRE uses automation, monitoring, SLOs, and error budgets to balance reliability with the pace of change.

### **26. What is an Internal Developer Platform (IDP)?**
**Answer:** A self-service portal (e.g., Backstage) providing "Golden Paths" that automate infrastructure provisioning, CI/CD, and compliance to reduce developer cognitive load.

### **27. What is a Golden Path (Paved Road)?**
**Answer:** A supported, standardized, and automated route for building and deploying software that incorporates all organizational security, infrastructure, and compliance best practices by default.

### **28. What is Cognitive Load in software engineering?**
**Answer:** Cognitive load is the mental effort required to understand and perform a task. Platform Engineering reduces unnecessary cognitive load by providing self-service tools, standardized workflows, and reusable automation, allowing developers to focus more on delivering business value.

### **29. What is Conway’s Law?**
**Answer:** Conway’s Law states that organizations tend to design systems that mirror their communication structures. Therefore, team boundaries and communication patterns should be considered when designing software architecture.

### **30. What is Idempotency?**
**Answer:** A property of an operation where executing it once or multiple times produces the exact same end-state result without side effects.

### **31. What is Configuration Management?**
**Answer:** Configuration Management is the practice of automating and maintaining consistent system configurations across servers. Tools like Ansible and Puppet help manage packages, configuration files, and system settings in a repeatable way.

### **32. What is a Deployment Pipeline?**
**Answer:** A Deployment Pipeline is an automated sequence of stages that validates, builds, tests, packages, and deploys software from source control toward production. It improves repeatability, quality, and release speed.

### **33. What is a Rollback Strategy?**
**Answer:** A Rollback Strategy defines how to restore a system to a known stable version when a deployment causes problems. It should include clear rollback triggers, an execution procedure, and validation that the service has recovered.

### **34. What is Artifact Repository Management?**
**Answer:** Artifact Repository Management involves storing, versioning, and distributing build artifacts in a centralized repository. It allows CI/CD pipelines to retrieve consistent, traceable artifacts for testing and deployment.

### **35. What is Continuous Feedback?**
**Answer:** Continuous Feedback is the ongoing collection and analysis of production telemetry and user feedback. Teams use these insights to identify problems, prioritize improvements, and make future releases more reliable.

### **36. What is the Single Source of Truth principle?**
**Answer:** The Single Source of Truth principle means maintaining one authoritative source for a given set of information, such as infrastructure definitions or application configuration. Version control and review processes help teams track changes and avoid conflicting copies.

### **37. What is Technical Debt in DevOps?**
**Answer:** Technical Debt is the future cost created by choosing a quick or suboptimal solution instead of a more maintainable one. In DevOps, it can include manual configuration, fragile pipelines, and missing automation, increasing operational risk and maintenance effort.

### **38. What is Zero-Downtime Deployment?**
**Answer:** Deploying new application versions without interrupting active user requests or causing connection drops (achieved via Rolling Updates, Blue-Green, or Canary deployments).

### **39. What is Backward Compatibility in API design?**
**Answer:** Ensuring that updates to APIs or database schemas do not break older client applications or existing data consumers.

### **40. What is Semantic Versioning (SemVer)?**
**Answer:** A standard versioning convention: `MAJOR.MINOR.PATCH` (e.g., `2.1.0`), where MAJOR indicates breaking changes, MINOR indicates backward-compatible features, and PATCH indicates bug fixes.

### **41. What is Self-Healing Infrastructure?**
**Answer:** Self-Healing Infrastructure automatically detects failures and takes predefined corrective actions to restore service health. Examples include Kubernetes restarting failed containers and cloud Auto Scaling Groups replacing unhealthy instances.

### **42. What is a Monorepo vs Polyrepo?**
**Answer:** A Monorepo stores multiple projects or services in a single version-controlled repository, whereas a Polyrepo approach gives each project or service its own repository. The choice depends on team structure, tooling, access control, and build and release requirements.

### **43. What is Shift-Right Testing?**
**Answer:** Shift-Right Testing validates software in production or production-like conditions after deployment. It uses techniques such as canary releases, feature flags, synthetic monitoring, and controlled experiments to evaluate real-world reliability and behavior.

### **44. What is Telemetry in DevOps?**
**Answer:** Telemetry is the automated collection and transmission of operational data from applications and infrastructure. Metrics, logs, and traces help teams monitor system health, investigate incidents, and understand performance.

### **45. What is a Blameless Culture?**
**Answer:** A high-trust workplace culture that treats errors as systemic opportunities to improve tooling and processes rather than punishing individual human mistakes.

### **46. What is a GameDay in SRE?**
**Answer:** A GameDay is a planned resilience exercise in which teams simulate failures or disaster scenarios to validate monitoring, alerting, incident response procedures, and recovery mechanisms.

### **47. What is a Dead Letter Queue (DLQ)?**
**Answer:** A dedicated message queue that isolates unprocessable or malformed messages after repeated retry failures to prevent consumer queue blocking.

### **48. What is the Bulkhead Pattern?**
**Answer:** Isolating critical system resources (thread pools, memory, database connections) into distinct compartments so failure of one dependency does not crash the entire application.

### **49. What is Circuit Breaking?**
**Answer:** A design pattern that prevents an application from repeatedly executing an operation that is failing, allowing downstream dependencies time to recover.

### **50. What is Rate Limiting vs Throttling?**
**Answer:** Rate limiting restricts how many requests a specific user/IP can make in a given time window; throttling regulates server-side processing speed to match downstream resource capacity.

---

## 🟡 **Part 2: Site Reliability Engineering (SRE) & Reliability (Questions 51–100)**

### **51. What is an SLI (Service Level Indicator)?**
**Answer:** A quantifiable metric that measures service performance at a specific moment in time (e.g., Proportion of HTTP requests returning status 200 in $< 200\text{ms}$).

### **52. What is an SLO (Service Level Objective)?**
**Answer:** An internal reliability target agreed upon between Dev and SRE teams (e.g., 99.9% of requests must meet the SLI over a rolling 30-day window).

### **53. What is an SLA (Service Level Agreement)?**
**Answer:** A legally binding contract with customers specifying penalties (financial credits, refunds) if the service fails to meet agreed uptime levels.

### **54. What is an Error Budget?**
**Answer:** The exact mathematical inverse of an SLO: $\text{Error Budget} = 100\% - \text{SLO}$. It defines the acceptable headroom of downtime or failures a service can accumulate without breaching user trust.

### **55. What happens when an Error Budget is exhausted (0%)?**
**Answer:** Non-critical feature deployments are frozen, and 100% of engineering bandwidth shifts to bug fixing, technical debt reduction, and reliability engineering.

### **56. What is Toil in SRE?**
**Answer:** Toil is repetitive, manual operational work that can often be automated and provides little long-term value.

### **57. What is the Google SRE 50% Rule for Toil?**
**Answer:** A maximum of 50% of an SRE's time should be spent on operational toil and on-call duties; the remaining 50%+ must be dedicated to software engineering projects that permanently eliminate toil.

### **58. What are the Four Golden Signals of Monitoring?**
**Answer:** Latency (time to process requests), Traffic (demand/throughput), Errors (rate of failed requests), and Saturation (how close resources are to full capacity).

### **59. What is the RED Method?**
**Answer:** A monitoring framework for request-driven microservices: **R**ate (req/sec), **E**rrors (failed req/sec), and **D**uration (latency distribution). The RED Method monitors Rate of requests, Errors, and Duration of requests.

### **60. What is the USE Method?**
**Answer:** The USE Method monitors resource Utilization, Saturation, and Errors.A monitoring framework for infrastructure resources: **U**tilization (time resource was busy), **S**aturation (queue depth), and **E**rrors (error counts).

### **61. What is MTTD (Mean Time to Detect)?**
**Answer:** The average time elapsed between the inception of a system incident and when the engineering team or monitoring system detects it. MTTD is the average time taken to detect a system incident after it starts.

### **62. What is MTTR (Mean Time to Resolve / Restore)?**
**Answer:** The average time taken from detecting a production failure to completely restoring normal system operations for users.

### **63. What is MTBF (Mean Time Between Failures)?**
**Answer:** The average time elapsed between operational system failures, measuring overall infrastructure stability.

### **64. What is MTTF (Mean Time to Failure)?**
**Answer:** The expected operating time of a non-repairable system or hardware component before it completely fails.

### **65. What is a Blameless Post-Mortem?**
**Answer:** blameless post-mortem is a review after an incident that focuses on finding the root cause and preventing future incidents instead of blaming people.”

### **66. What are the core sections of a Post-Mortem document?**
**Answer:** 1. Executive Summary & Impact, 2. UTC Incident Timeline, 3. Root Cause Analysis (5 Whys), 4. What Went Well / Poorly, 5. SMART Action Items with owners. A post-mortem includes the incident summary, impact, timeline, root cause, lessons learned, and action items with owners.

### **67. What is the 5 Whys technique in root cause analysis?**
**Answer:** The 5 Whys technique means repeatedly asking why to identify the root cause of a problem.

### **68. What is Alert Fatigue and how do you prevent it?**
**Answer:** Overwhelming on-call engineers with noisy, non-actionable alerts, leading to missed critical incidents. Prevented by alerting strictly on user-facing SLO symptoms and dynamic burn rates. Alert fatigue happens when engineers receive too many unnecessary alerts, and we prevent it by sending meaningful, actionable alerts.

### **69. What is a Multi-Window Multi-Burn-Rate Alert?**
**Answer:** Google SRE alerting standard that calculates the consumption speed of an error budget across short (1 hour) and long (6 hours) windows to page engineers only when error budget is rapidly burning.

### **70. What is RTO (Recovery Time Objective)?**
**Answer:** RTO is the maximum acceptable downtime after a disaster before the service must be restored.

### **71. What is RPO (Recovery Point Objective)?**
**Answer:** RPO is the maximum acceptable amount of data loss measured in time after a disaster

### **72. What is an On-Call Escalation Policy?**
**Answer:** A predefined workflow in paging systems (PagerDuty, Opsgenie) that routes alerts to a primary on-call engineer, escalating to secondary engineers or engineering managers if unacknowledged within 5–10 minutes.

### **73. What is an Incident Commander (IC)?**
**Answer:** The designated leader during a critical production outage responsible for coordinating investigation tasks, assigning roles, managing communications, and making high-level recovery decisions.

### **74. What is a Runbook (Playbook)?**
**Answer:** A documented, step-by-step technical guide for on-call engineers describing how to diagnose, triage, and resolve specific alert conditions or system failures.

### **75. What is Automated Remediation?**
**Answer:** Automated remediation detects known failures and automatically performs predefined corrective actions to restore service.

### **76. What is Capacity Planning in SRE?**
**Answer:** Capacity planning means estimating future resource requirements and scaling systems before demand exceeds available capacity.”

### **77. What is Load Shedding?**
**Answer:** Load shedding protects critical operations by rejecting low-priority requests when a system is overloaded.

### **78. What is Graceful Degradation?**
**Answer:** Graceful degradation allows an application to keep its core features working when non-essential services fail.

### **79. What is the Thundering Herd Problem?**
**Answer:** The Thundering Herd Problem occurs when many clients retry at the same time and overload a recovering server.**.

### **80. What is Exponential Backoff with Jitter?**
**Answer:** Exponential backoff with jitter increases retry delays and adds randomness to prevent many clients from retrying simultaneously.”

### **81. What is High Availability (HA)?**
**Answer:** Designing systems with redundant components across multiple fault domains (Availability Zones, regions) to ensure continuous operation without a Single Point of Failure (SPOF). High Availability means designing a system with redundant components so that the service continues working even if one component fails

### **82. What does "Three Nines" vs "Four Nines" vs "Five Nines" uptime mean?**
**Answer:** 99.9% (Three Nines) = max 43.2 min downtime/month; 99.99% (Four Nines) = max 4.32 min downtime/month; 99.999% (Five Nines) = max 25.9 sec downtime/month.

### **83. What is Active-Active vs Active-Passive High Availability?**
**Answer:** Active-Active runs multiple redundant systems processing live traffic simultaneously; Active-Passive runs a primary active system while a secondary standby system remains idle, ready to take over on failover.

### **84. What is Split-Brain in distributed systems?**
**Answer:** A state where a network partition isolates nodes in a cluster, causing both sides to believe the other has failed and independently elect leaders, leading to severe data corruption.

### **85. How is Split-Brain prevented?**
**Answer:** Split-brain can be prevented using quorum-based leader election, consensus protocols and fencing to ensure only one valid leader can perform writes.

### **86. What is the CAP Theorem?**
**Answer:** The CAP theorem states that during a network partition, a distributed system must trade off strong consistency against availability.

### **87. What is the PACELC Theorem?**
**Answer:** An extension of CAP: If there is a **P**artition, choose **A**vailability or **C**onsistency; **E**lse (normal state), choose **L**atency or **C**onsistency.

### **88. What is Eventual Consistency?**
**Answer:** A consistency model where, given no new updates, all replicas across a distributed system will eventually converge and return the latest value.

### **89. What is Distributed Tracing?**
**Answer:** Distributed tracing follows a request across multiple services to identify latency bottlenecks and failures.

### **90. What is Continuous Profiling?**
**Answer:** Continuous profiling continuously collects performance data from running applications to identify CPU, memory and execution bottlenecks.

### **91. What is Blackbox Probing?**
**Answer:** Pinging external endpoints (HTTP GET, TCP SYN, DNS lookup) from outside the infrastructure to verify user-facing service availability. Blackbox probing checks service availability from outside the system using HTTP, TCP or DNS requests.

### **92. What is Whitebox Monitoring?**
**Answer:** Whitebox monitoring uses internal application metrics and runtime data to understand system health and performance.


### **93. What is High Cardinality in metrics?**
**Answer:** A High cardinality occurs when metrics have too many unique label combinations, increasing storage and memory usage and potentially slowing queries.

### **94. What is Synthetic Monitoring?**
**Answer:** Running automated scripts or headless browser bots that periodically execute user journeys (e.g., searching, adding to cart, checking out) to detect failures before real users encounter them.

### **95. What is Real User Monitoring (RUM)?**
**Answer:** Real User Monitoring collects performance and error data from actual users’ browsers or mobile applications.

### **96. What is a Service Dependency Graph?**
**Answer:** A service dependency graph visually shows how microservices, databases and external APIs depend on one another.

### **97. What is Dark Traffic Mirroring (Shadowing)?**
**Answer:** Traffic mirroring copies live production requests to another version for testing without returning that version’s responses to users.

### **98. What is an SRE Error Budget Policy?**
**Answer:** An SRE error budget policy defines the actions a team takes when its error budget is exhausted, such as pausing non-critical releases and prioritizing reliability work.

### **99. What is Chaos Mesh?**
**Answer:** Chaos Mesh is a Kubernetes chaos engineering platform used to inject controlled failures and test application resilience.

### **100. What is Observability as Code (OaC)?**
**Answer:** Observability as Code means defining monitoring dashboards, alert rules and telemetry configurations as version-controlled code.

---

## 🔴 **Part 3: Platform Engineering, FinOps & Architecture (Questions 101–200)**

### **101. What is Platform Engineering?**
**Answer:** Platform Engineering builds self-service tools and workflows that help developers build, test, deploy, and operate applications independently.

### **102. What is "Platform as a Product"?**
**Answer:** Platform as a Product means treating the internal developer platform as a product, with developers as customers whose feedback guides continuous improvement.

### **103. What is Spotify Backstage?**
**Answer:** Spotify Backstage is an open-source framework for building developer portals with a software catalog, documentation, and reusable project templates.

### **104. What is a Software Template in Platform Engineering?**
**Answer:** A software template provides a reusable project structure with standard configurations and automation to help developers create new services quickly and consistently.

### **105. What is Developer Experience (DevEx)?**
**Answer:** Developer Experience measures how easy and efficient it is for developers to write, test, debug, and deploy software.

### **106. What is Developer Velocity Index (DVI)?**
**Answer:** Developer Velocity Index measures how effectively an organization’s tools, culture, and processes help developers deliver business value.

### **107. What is Crossplane?**
**Answer:** Crossplane extends Kubernetes to manage cloud infrastructure resources through declarative configurations and Kubernetes APIs.

### **108. What is a Composite Resource Definition (XRD) in Crossplane?**
**Answer:** A custom Kubernetes API defined by a platform team that bundles multiple cloud resources into a single self-service abstraction for developers (e.g., `kind: DatabaseInstance`).

### **109. What is Kratix?**
**Answer:** A framework for building multi-cloud, multi-cluster platforms on Kubernetes that delivers reusable infrastructure and service "Promises" to development teams.

### **110. What is the Open Feature standard?**
**Answer:** OpenFeature is a vendor-neutral standard that provides common APIs and SDKs for managing feature flags across applications.

### **111. What is the Score specification in Platform Engineering?**
**Answer:** A developer-centric, workload-oriented specification that describes how an application runs without needing to know target environment Kubernetes or Terraform details.

### **112. What is FinOps and what are its three core phases?**
**Answer:** Cloud Financial Operations. The three phases are: **Inform** (visibility and tagging), **Optimize** (rate reduction and right-sizing), and **Operate** (continuous governance).

### **113. What is Cloud Unit Economics?**
**Answer:** Measuring cloud spend relative to direct business metrics (e.g., *Cost per Active User*, *Cost per Transaction Processed*, *Cost per GB Streamed*).

### **114. What is a Cloud Savings Plan?**
**Answer:** A flexible pricing model offering up to 72% discount on compute usage (EC2, Fargate, Lambda) in exchange for a 1- or 3-year hourly spend commitment.

### **115. What are Reserved Instances (RIs)?**
**Answer:** A discount commitment model tied to specific cloud instance families, OS, and regions in exchange for 1- or 3-year term commitments.

### **116. What are Cloud Spot Instances?**
**Answer:** Spare cloud provider compute capacity offered at up to 90% discount, with the caveat that the provider can reclaim the instance with a 2-minute notification.

### **117. What is Infracost?**
**Answer:** A FinOps tool that parses Terraform code in CI pull requests to display the exact monthly cost delta of proposed infrastructure changes before deployment.

### **118. What is Cloud Custodian?**
**Answer:** An open-source rules engine for cloud security and cost management that automatically stops untagged instances, terminates idle databases, and enforces compliance via YAML policies.

### **119. What is Kubernetes Right-Sizing?**
**Answer:** Adjusting container CPU/memory `requests` and `limits` based on historical usage telemetry to eliminate over-provisioning and minimize cloud waste.

### **120. What is Scale-to-Zero in serverless and Kubernetes?**
**Answer:** Automatically scaling application pod replicas down to 0 when there is no incoming traffic or queue backlog (via KEDA or Knative), saving 100% of compute cost during idle periods.

### **121. What is Karpenter Node Consolidation?**
**Answer:** An automated optimization feature where Karpenter identifies underutilized worker nodes, computes an optimal single replacement node, drains pods, and terminates empty nodes.

### **122. What is a Multi-Tenant Kubernetes Cluster?**
**Answer:** A single physical cluster shared across multiple development teams or external customers, isolated via Namespaces, NetworkPolicies, RBAC, and ResourceQuotas.

### **123. What is `vcluster` (Virtual Cluster)?**
**Answer:** An open-source tool that runs fully functional, isolated virtual Kubernetes control planes inside namespaces of an underlying host cluster, providing hard multi-tenancy.

### **124. What is Zero Trust Network Architecture (ZTNA)?**
**Answer:** A security model requiring strict identity verification and encrypted communication (mTLS) for every user, device, and service regardless of whether it resides inside the private VPC.

### **125. What is SPIFFE/SPIRE?**
**Answer:** Standardized cryptographic workload identity framework that issues short-lived, auto-rotating X.509 certificates to microservices based on kernel and kubelet attestation.

### **126. What is Policy as Code (PaC)?**
**Answer:** Defining, testing, and enforcing compliance and operational rules using machine-readable code files (Open Policy Agent Rego, Kyverno) across CI/CD and admission controllers.

### **127. What is Open Policy Agent (OPA)?**
**Answer:** An open-source, general-purpose policy engine that evaluates structured JSON/YAML inputs against declarative logic written in the **Rego** language.

### **128. What is Kyverno?**
**Answer:** A Kubernetes-native policy engine written 100% in YAML that validates, mutates, and generates Kubernetes resources and verifies container image signatures.

### **129. What is HashiCorp Vault?**
**Answer:** A secure secrets management system that provides centralized dynamic secrets generation, PKI certificate authority management, and data encryption as a service.

### **130. What is External Secrets Operator (ESO)?**
**Answer:** A Kubernetes operator that syncs secrets from external enterprise vaults (AWS Secrets Manager, HashiCorp Vault) into native Kubernetes `Secret` objects.

### **131. What is Keyless Signing with Sigstore Cosign?**
**Answer:** Cryptographically signing container images using short-lived OIDC certificates from Fulcio and transparency logs from Rekor, eliminating static PGP private keys.

### **132. What is an SBOM (Software Bill of Materials)?**
**Answer:** A machine-readable nested inventory of all software packages, libraries, and transitive dependencies bundled inside a software container or binary (e.g., CycloneDX).

### **133. What is the SLSA Framework (Supply-chain Levels for Software Artifacts)?**
**Answer:** A security framework establishing standards for software build integrity, hermetic build sandboxing, and non-falsifiable build provenance.

### **134. What is eBPF (Extended Berkeley Packet Filter)?**
**Answer:** A Linux kernel technology allowing sandboxed programs to execute safely inside the kernel without changing kernel source code, used for high-speed networking (Cilium), observability (Hubble), and runtime security (Falco).

### **135. What is Falco?**
**Answer:** A CNCF runtime security tool that parses Linux kernel system calls via eBPF probes to detect and alert on unauthorized container activities (spawning shells, reading `/etc/shadow`).

### **136. What is Cilium?**
**Answer:** An eBPF-based Kubernetes CNI, Service Mesh, and network security plugin providing high-performance Layer 3 to Layer 7 routing and transparent encryption.

### **137. What is the Gateway API in Kubernetes?**
**Answer:** The modern successor to Kubernetes Ingress providing role-oriented resource separation (`GatewayClass`, `Gateway`, `HTTPRoute`) and native traffic splitting.

### **138. What is KEDA (Kubernetes Event-driven Autoscaling)?**
**Answer:** An autoscaler that scales Kubernetes workloads from 0 to hundreds based on external event metrics (AWS SQS queue length, Kafka consumer group lag).

### **139. What is Istio Ambient Mesh?**
**Answer:** A sidecarless service mesh architecture that splits mesh processing into per-node `ztunnel` daemons (Layer 4 mTLS) and optional per-namespace waypoint proxies (Layer 7 routing).

### **140. What is Distributed Consensus (Raft / Paxos)?**
**Answer:** Algorithms that enable distributed clusters (etcd, Consul, CockroachDB) to agree on data values and state machine logs across independent nodes despite network partitions.

### **141. What is Write-Ahead Logging (WAL)?**
**Answer:** A database reliability technique where changes are recorded to append-only disk storage before being applied to memory, guaranteeing durability during crashes.

### **142. What is Database Connection Pooling?**
**Answer:** Reusing a fixed pool of established database connections (via PgBouncer / RDS Proxy) to prevent thousands of client requests from exhausting database memory and thread limits.

### **143. What is Sharding in databases?**
**Answer:** Horizontally partitioning database rows across multiple independent physical database instances based on a shard key (e.g., `user_id` % 10).

### **144. What is Read-Write Splitting?**
**Answer:** Routing write operations (`INSERT`, `UPDATE`) to the primary database while directing read queries (`SELECT`) to asynchronous read replicas.

### **145. What is Database Replication Lag?**
**Answer:** The delay in time between a transaction being committed on a primary database and that transaction being applied on asynchronous read replicas.

### **146. What is Dual-Write Pattern in microservices?**
**Answer:** The anti-pattern of an application attempting to write to both a database and a message queue in a single transaction, leading to data inconsistency when one write fails.

### **147. What is the Transactional Outbox Pattern?**
**Answer:** Saving events to an "Outbox" database table within the same ACID transaction as business data, and using a separate change-data-capture (Debezium) process to publish events to Kafka.

### **148. What is the Saga Pattern in distributed transactions?**
**Answer:** Managing distributed transactions across microservices via a sequence of local transactions, executing compensating transactions (reversals) if a step fails.

### **149. What is Event Sourcing?**
**Answer:** An architectural pattern where state changes are stored as an append-only sequence of immutable events rather than overwriting current state values in place.

### **150. What is CQRS (Command Query Responsibility Segregation)?**
**Answer:** Separating read and write operations into distinct data models and databases optimized specifically for high-throughput writes (Commands) or fast reads (Queries).

### **151. What is an Anycast IP Address?**
**Answer:** Routing client traffic to the topologically closest server among multiple globally distributed servers sharing the exact same IP address via BGP.

### **152. What is a Content Delivery Network (CDN)?**
**Answer:** A globally distributed network of proxy caching servers that caches web assets close to users to minimize latency and absorb traffic surges.

### **153. What is Head-of-Line (HoL) Blocking?**
**Answer:** A performance bottleneck where a single dropped or delayed packet in a FIFO queue blocks all subsequent packets from processing (resolved by HTTP/3 QUIC over UDP).

### **154. What is AWS Direct Connect / Azure ExpressRoute?**
**Answer:** Dedicated private physical fiber connections between an enterprise on-premise data center and a cloud provider, bypassing public internet routing.

### **155. What is AWS Transit Gateway?**
**Answer:** A centralized hub-and-spoke router connecting hundreds of VPCs, VPNs, and Direct Connect links through a single managed gateway.

### **156. What is AWS PrivateLink (VPC Endpoint)?**
**Answer:** Private network interfaces connecting VPC subnets to cloud services or SaaS vendors over cloud backbone networks without public internet transit.

### **157. What is Multi-Region Active-Active Architecture?**
**Answer:** Deploying fully functional infrastructure across multiple geographical cloud regions simultaneously, routing live users to the closest region with real-time data replication.

### **158. What is Disaster Recovery Failover Routing?**
**Answer:** DNS routing policies (Route 53) that automatically redirect global user traffic to a backup disaster recovery region when primary health check probes fail.

### **159. What is Pilot Light Disaster Recovery?**
**Answer:** Replicating critical databases continuously to a secondary region while keeping minimal core infrastructure running, provisioning full compute only during a disaster.

### **160. What is Warm Standby Disaster Recovery?**
**Answer:** Running a scaled-down, fully functional copy of production infrastructure in a secondary region that can be scaled up instantly upon failover.

### **161. What is Cold Start in Serverless?**
**Answer:** The latency penalty incurred when an incoming request requires the cloud provider to download the container image, provision a microVM, and initialize the language runtime.

### **162. What is AWS Lambda SnapStart?**
**Answer:** Caching an encrypted Firecracker microVM snapshot of an initialized JVM runtime during deployment, resuming subsequent cold starts in $< 200\text{ms}$.

### **163. What is an API Gateway?**
**Answer:** An application-layer reverse proxy that manages incoming API traffic, handling authentication, rate limiting, request validation, and analytics.

### **164. What is gRPC vs REST?**
**Answer:** REST uses HTTP/1.1 with JSON text payloads; gRPC uses HTTP/2 with binary Protocol Buffers (Protobuf), providing multiplexing, bi-directional streaming, and high throughput.

### **165. What is GraphQL vs REST?**
**Answer:** REST exposes fixed data endpoints; GraphQL allows clients to request the exact fields they need in a single request, eliminating over-fetching and under-fetching.

### **166. What is Webhook Payload Verification (HMAC-SHA256)?**
**Answer:** Validating that an incoming webhook originated from an authentic sender by comparing the hash of the request body with a shared secret key.

### **167. What is JWT (JSON Web Token) Structure?**
**Answer:** Encoded string with three parts separated by dots: **Header** (algorithm), **Payload** (claims: `sub`, `exp`), and **Signature** (cryptographic hash).

### **168. What is OAuth 2.0 vs OpenID Connect (OIDC)?**
**Answer:** OAuth 2.0 is an authorization framework issuing Access Tokens for API permissions; OIDC is an identity layer on top of OAuth 2.0 issuing ID Tokens for user authentication.

### **169. What is Role-Based Access Control (RBAC)?**
**Answer:** Assigning system permissions to roles rather than individual users, granting users permissions based on role memberships.

### **170. What is Attribute-Based Access Control (ABAC)?**
**Answer:** Evaluating context attributes (user department, resource tags, time of day, IP address) to determine real-time access authorization.

### **171. What is CloudTrail vs CloudWatch?**
**Answer:** CloudTrail records every API call made in an AWS account for auditing; CloudWatch monitors operational performance metrics and aggregates logs.

### **172. What is Amazon GuardDuty?**
**Answer:** Intelligent threat detection analyzing CloudTrail, VPC Flow Logs, and EKS audit logs via machine learning to detect compromised instances.

### **173. What is AWS Security Hub?**
**Answer:** A centralized dashboard aggregating compliance posture (CIS, PCI-DSS) and security findings across AWS accounts.

### **174. What is Amazon Inspector?**
**Answer:** Automated vulnerability management scanning EC2 instances, ECR container images, and Lambda functions for software vulnerabilities.

### **175. What is AWS KMS (Key Management Service)?**
**Answer:** Managed service for creating and controlling cryptographic encryption keys used across cloud storage and applications.

### **176. What is Envelope Encryption?**
**Answer:** Encrypting high-volume plaintext data with a Data Encryption Key (DEK), and encrypting the DEK with a root KMS Key.

### **177. What is AWS Secrets Manager vs Parameter Store?**
**Answer:** Secrets Manager supports automated secret rotation and cross-account access; Parameter Store is a simpler, hierarchical key-value configuration store.

### **178. What is Infrastructure Drift Detection?**
**Answer:** Automatically comparing running cloud resources against IaC state files to detect and alert on unauthorized manual modifications.

### **179. What is Terratest?**
**Answer:** A Go library for writing automated integration tests that provision real cloud infrastructure via Terraform, validate endpoints, and tear down resources.

### **180. What is Checkov?**
**Answer:** A static code analysis tool for Infrastructure as Code that scans Terraform, CloudFormation, and Kubernetes manifests for security misconfigurations.

### **181. What is OpenTofu?**
**Answer:** An open-source, community-governed fork of Terraform (MPL 2.0) maintained by the Linux Foundation.

### **182. What is Prometheus PromQL?**
**Answer:** A powerful read-only query language for filtering, aggregating, and computing mathematical functions over Prometheus time-series metrics.

### **183. What is Grafana Loki LogQL?**
**Answer:** A Prometheus-inspired query language for filtering log streams and generating real-time metrics from raw log text.

### **184. What is Grafana Tempo?**
**Answer:** A distributed tracing backend that stores raw spans directly in cheap cloud object storage without needing Elasticsearch.

### **185. What is OpenTelemetry (OTel) Collector?**
**Answer:** A proxy pipeline component that receives, processes (batches, redacts, samples), and exports telemetry to multiple backend storage engines.

### **186. What is eBPF Hubble?**
**Answer:** An observability platform running on eBPF to visualize service-to-service communication dependency graphs and network latency.

### **187. What is Chaos Mesh?**
**Answer:** A Kubernetes-native chaos engineering operator that injects faults via CRDs to test system resiliency.

### **188. What is DAST (Dynamic Application Security Testing)?**
**Answer:** Attacking running web applications from the outside to discover runtime misconfigurations, XSS, and SQL injection flaws.

### **189. What is SAST (Static Application Security Testing)?**
**Answer:** Analyzing uncompiled source code to detect security vulnerabilities, syntax errors, and coding flaws.

### **190. What is SCA (Software Composition Analysis)?**
**Answer:** Scanning open-source third-party dependencies against national vulnerability databases for known CVEs.

### **191. What is a Container Escape?**
**Answer:** An exploit where an attacker running code inside a container escapes isolation boundaries to gain control over the host operating system.

### **192. What is Rootless Docker / Podman?**
**Answer:** Running container daemons and processes inside unprivileged user namespaces, preventing host root compromise during breakouts.

### **193. What is Pod Security Admission (PSA)?**
**Answer:** Kubernetes built-in admission controller enforcing Privileged, Baseline, or Restricted security standards per namespace.

### **194. What is a Kubernetes Pod Disruption Budget (PDB)?**
**Answer:** A policy limiting how many pods of a replicated service can be down simultaneously during voluntary disruptions (node drains).

### **195. What is Kubernetes Horizontal Pod Autoscaler (HPA)?**
**Answer:** Automatically adjusting the number of pod replicas based on observed CPU, memory, or custom external metrics.

### **196. What is Kubernetes Vertical Pod Autoscaler (VPA)?**
**Answer:** Automatically right-sizing container CPU and memory resource requests/limits based on historical usage analysis.

### **197. What is NodeLocal DNSCache?**
**Answer:** A DaemonSet caching DNS queries locally on worker nodes to eliminate CoreDNS network bottlenecks and glibc `ndots:5` latency storms.

### **198. What is GitOps Reconciliation Loop?**
**Answer:** A continuous background process where a GitOps operator compares desired state in Git against live cluster state and automatically auto-heals drift.

### **199. What is Progressive Delivery?**
**Answer:** An evolution of Continuous Delivery that combines canary deployments, automated metric analysis, and feature flags to roll out features with minimal blast radius.

### **200. What is an SRE Blameless Post-Mortem Creed?**
**Answer:** The guiding philosophy that human error is the starting point of an incident investigation, not the conclusion, focusing on improving systemic safeguards.
