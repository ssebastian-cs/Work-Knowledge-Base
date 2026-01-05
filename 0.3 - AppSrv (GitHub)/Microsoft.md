
Tags: [[AppSrv]]

# Azure



---

## References



---

# Active Directory Domain Services



---

## References



---

# Microsoft Entra

## Microsoft Entra Overview

[Microsoft Entra](https://learn.microsoft.com/en-us/entra/fundamentals/what-is-entra#establish-zero-trust-access-controls) is a family of identity and network access products. It enables organizations to implement a [Zero Trust](https://learn.microsoft.com/en-us/security/zero-trust/zero-trust-overview) security strategy and create a [trust fabric](https://www.microsoft.com/security/blog/2024/05/08/how-implementing-a-trust-fabric-strengthens-identity-and-network/) that verifies identities, validates access conditions, checks permissions, encrypts connection channels, and monitors for compromise.

The Microsoft Entra product family covers four maturity stages of secure end-to-end access for any trustworthy identity. These stages include establishing Zero Trust access controls, and securing access for employees, customers, partners, and any cloud environment

![Entra](entra-product-family.png)

### Zero Trust Access Controls:

Zero Trust is a security model that assumes no user or device is inherently trustworthy, requiring strict identity verification for every access attempt. Microsoft Entra provides tools to implement Zero Trust by securing identities, access, and permissions across various environments.

---

### Core Identity and Access Management

#### **Microsoft Entra ID**
- **What it is**: The foundation of Microsoft Entra, providing **identity management**, **authentication**, and **access policies** to secure employees, devices, apps, and resources.
- **Why it matters**: Ensures only authorized users and devices access enterprise resources.
- **Key terms**: Identity, authentication, policy, protection.

#### **Microsoft Entra Domain Services**
- **What it is**: A managed service offering **domain services** like **group policy**, **LDAP** (Lightweight Directory Access Protocol), and **Kerberos/NTLM authentication**.
- **Why it matters**: Supports legacy applications in the cloud that rely on traditional authentication methods (e.g., Kerberos) without organizations managing the infrastructure.
- **Example**: A company can deploy a legacy app requiring Kerberos in a Microsoft-managed domain, simplifying maintenance.
- **Key terms**: Managed domain, LDAP, Kerberos, NTLM.

---

### Secure Employee Access

#### **Microsoft Entra Private Access**
- **What it is**: Secures access to **private apps** and **corporate resources** (e.g., internal networks, multicloud environments) without needing a **VPN**.
- **Why it matters**: Enables secure remote access from any device or network.
- **Example**: An employee can print to a corporate printer from a cafe without a VPN.
- **Key terms**: Private apps, corporate network, multicloud, VPN.

#### **Microsoft Entra Internet Access**
- **What it is**: Secures access to **internet resources**, including **SaaS apps** and **Microsoft 365**, with real-time monitoring and access adjustments.
- **Why it matters**: Protects against risky access and ensures compliance with organizational policies.
- **Example**: Web content filtering to block specific websites based on categories or domains.
- **Key terms**: SaaS, Microsoft 365, web content filtering, real-time monitoring.

#### **Microsoft Entra ID Governance**
- **What it is**: Simplifies **identity and permissions management** by automating **access requests**, **assignments**, and **reviews**.
- **Why it matters**: Streamlines onboarding/offboarding and protects critical assets through **identity lifecycle management**.
- **Example**: Automatically assign Microsoft 365 licenses to new hires and remove them when employees leave.
- **Key terms**: Identity lifecycle management, access requests, automation.

#### **Microsoft Entra ID Protection**
- **What it is**: Detects and mitigates **identity-based risks** using tools like **Conditional Access**.
- **Why it matters**: Proactively identifies and responds to suspicious activities.
- **Example**: Require **multifactor authentication (MFA)** for sign-ins flagged as medium or high risk.
- **Key terms**: Identity-based risks, Conditional Access, multifactor authentication.

#### **Microsoft Entra Verified ID**
- **What it is**: A **credential verification service** using **decentralized identities (DIDs)** based on open standards.
- **Why it matters**: Allows users to store and present **verifiable credentials** (e.g., digital signatures proving information validity) securely.
- **Example**: A graduate receives a digital diploma from their university, stored in their DID, and presents it to an employer for verification.
- **Key terms**: Decentralized identities (DIDs), verifiable credentials, digital signature.

---

### Secure Access for Customers and Partners

#### **Microsoft Entra External ID**
- **What it is**: Manages **external identities** for secure collaboration with **business partners**, **guests**, and **customers** in consumer-facing apps.
- **Why it matters**: Simplifies secure access for non-employees while supporting **customer identity and access management (CIAM)**.
- **Example**: Customers can sign into a web app using a one-time passcode or social accounts (e.g., Google, Facebook).
- **Key terms**: External identities, CIAM, self-service registration.

---

### Secure Access Across Clouds

#### **Microsoft Entra Permissions Management**
- **What it is**: Provides visibility and control over **permissions** across **Microsoft Azure**, **AWS**, and **Google Cloud Platform (GCP)**.
- **Why it matters**: Detects and removes unused or excessive permissions to reduce security risks.
- **Example**: Automatically revoke high-risk permissions for users who don’t use them.
- **Key terms**: Permissions management, multicloud, right-sizing permissions.

#### **Microsoft Entra Workload ID**
- **What it is**: Manages **workload identities** (e.g., apps, services, containers) with **authentication** and **authorization policies**.
- **Why it matters**: Secures non-human identities accessing resources.
- **Example**: A GitHub Action uses a workload identity to access Azure subscriptions for automated workflows.
- **Key terms**: Workload identities, authentication, authorization, adaptive policies.

---

## Microsoft Entra Architecture

[Identity Management Fundamentals](https://learn.microsoft.com/en-us/entra/fundamentals/identity-management-overview).

---

### Microsoft Entra Architecture: How It Works
Microsoft Entra is built to be **reliable**, **fast**, and **scalable** by using a **geographically distributed system** (servers spread across the world). This ensures the service is always available, performs well, and can handle failures without disrupting users.

#### Key Concepts
1. **Distributed Design**:
   - The system is split into independent pieces called **partitions** (like separate filing cabinets for data).
   - Each partition handles a portion of the data, making the system easier to manage and scale.

2. **Primary and Secondary Replicas**:
   - **Primary Replica**: The main server for a partition that handles all **write operations** (e.g., updating a user’s password). Writes are copied to a secondary replica in another location for safety before confirming success.
   - **Secondary Replicas**: Multiple backup servers in different locations handle **read operations** (e.g., checking a user’s login). This spreads the workload and ensures fast access.
   - **Why it matters**: Reads (like logins) are more common than writes, so secondary replicas make the system faster and more reliable by serving users from nearby locations.

3. **Scalability**:
   - **Write Scalability**: Partitions split data to handle more write requests efficiently.
   - **Read Scalability**: Secondary replicas spread across the globe serve read requests from the closest location, speeding up performance.
   - **Example**: If you log in from Europe, your request goes to a nearby server, not one in the U.S., for faster response times.

4. **Continuous Availability**:
   - Microsoft Entra ensures the system is always running by using multiple **datacenters** (server locations worldwide).
   - If one datacenter fails, traffic automatically shifts to another, so users don’t notice interruptions.
   - **No downtime for maintenance**: The system is designed to stay online even during updates.
   - **Example**: It’s like having backup power generators that kick in instantly if the main power fails.

5. **Fault Tolerance**:
   - The system can handle hardware, network, or software failures.
   - If the primary replica fails, another replica takes over as the new primary in 1–2 minutes, keeping writes available. Reads are unaffected because they use secondary replicas.
   - **Example**: If a server crashes, the system switches to a backup server without you noticing.

6. **Data Durability**:
   - Every write (e.g., changing a user’s permissions) is saved in at least two datacenters to prevent data loss.
   - **Zero Recovery Time Objective (RTO)**: No data is lost during failovers for reads or token issuance (e.g., login tokens). Writes may have a brief 5-minute delay.
   - **Example**: It’s like saving a document on two different computers so it’s never lost, even if one crashes.

7. **Datacenters**:
   - Microsoft Entra runs in **datacenters worldwide** (see [Azure global infrastructure](https://azure.microsoft.com/en-us/global-infrastructure/)).
   - A **Gateway service** balances traffic, checks server health, and reroutes requests to healthy datacenters if one fails.
   - **Active-active configuration**: Multiple datacenters handle reads simultaneously, and writes can failover to a new primary if needed.

8. **Data Consistency**:
   - The system uses **eventual consistency**, meaning secondary replicas might not have the latest data immediately after a write.
   - To ensure accuracy, apps targeting a secondary replica send writes to the primary replica, which syncs back to the secondary for consistent reads.
   - **Example**: If you update your password, the system ensures the change is applied everywhere, but it may take a moment to sync.

9. **Backups and Recovery**:
   - **Daily backups** protect data in case of major issues.
   - **Soft deletes**: Deleted items (e.g., user accounts) can be restored within 30 days, preventing accidental data loss.
   - **Example**: If you accidentally delete a user account, you can recover it like retrieving a file from the recycle bin.

10. **Monitoring and Metrics**:
    - Microsoft Entra constantly tracks **service health** to detect and fix issues quickly.
    - **Goals**: Detect problems in under 5 minutes (**Time to Detect**, TTD) and resolve them in under 30 minutes (**Time to Mitigate**, TTM).
    - **Example**: It’s like a smoke detector that alerts firefighters instantly and ensures they put out the fire fast.

11. **Secure Operations**:
    - Uses **multifactor authentication (MFA)** and **auditing** for all operations.
    - **Just-in-time access**: Temporary permissions are granted only when needed for specific tasks.
    - **Example**: It’s like giving a worker a temporary key to a room only for the time they need to do their job.

---

#### Why This Matters
Microsoft Entra’s architecture ensures that:
- Your apps and data are **always available**, even during failures.
- The system is **fast** by serving users from nearby datacenters.
- Data is **secure and durable**, with no loss even if a datacenter goes down.
- Access is tightly controlled with robust **identity management**.

Think of it as a global network of super-smart, super-secure librarians who manage access to a massive library, ensuring you can always find and use the right books (resources) quickly and safely, no matter where you are or what goes wrong.

---

### References & Further Reading

https://learn.microsoft.com/en-us/entra/architecture/architecture

---

## Microsoft Entra Deployment Plans

### Simplified Explanation of Microsoft Entra Deployment Plans

**Microsoft Entra Deployment Plans Overview**  
Microsoft Entra (formerly Azure Active Directory) is a cloud-based system that helps organizations securely connect employees, customers, and partners to apps, devices, and data. This article, published on February 7, 2024, provides guidance on creating a deployment plan for Microsoft Entra ID to ensure secure and efficient access management. It covers key areas like stakeholder roles, authentication, applications, hybrid setups, user identities, and governance. Below, each section is explained in simple terms while retaining important terminology and including the provided hyperlinks.

---

### Key Steps for Building a Deployment Plan
A deployment plan ensures Microsoft Entra ID is set up correctly for your organization. The process involves identifying **stakeholders** (key decision-makers and affected groups), planning **authentication methods**, integrating **apps and devices**, handling **hybrid scenarios** (mix of on-premises and cloud systems), managing **user identities**, and setting up **governance and reporting**. Think of it as creating a roadmap to roll out a secure access system for your company.

---

### Stakeholders and Roles
To deploy Microsoft Entra ID successfully, involve the right people with clear responsibilities. Stakeholders are individuals or teams who influence or are affected by the deployment. Their roles and duties vary, but the areas of ownership are similar across organizations.

#### Common Roles and Responsibilities
- **Sponsor**: A senior leader who approves budgets and resources, acting as a bridge between managers and executives.
- **End Users**: The people who will use the system (e.g., employees accessing apps). They may test the system in a pilot program.
- **IT Support Manager**: Provides feedback on whether the proposed changes are practical for IT support teams.
- **Identity Architect**: Ensures the changes align with the organization’s **identity management** (how users are identified and authorized).
- **Application Business Owner**: Manages specific apps, including who can access them and the user experience.
- **Security Owner**: Verifies that the plan meets **security requirements**.
- **Compliance Manager**: Ensures the plan complies with corporate, industry, or government regulations.

#### RACI Model
The **RACI model** (Responsible, Accountable, Consulted, Informed) clarifies who does what in the deployment:
- **Responsible**: The people who do the work to complete a task (e.g., IT team setting up authentication).
- **Accountable**: The one person ultimately responsible for ensuring the task is done correctly (e.g., a project manager who approves the work).
- **Consulted**: Experts who provide advice (e.g., a security specialist giving input).
- **Informed**: People kept updated on progress, usually after tasks are completed (e.g., end users notified of changes).

**Why it matters**: Clear roles prevent confusion and ensure everyone knows their part in the deployment.

---

### Authentication Deployment
Authentication is how users prove their identity to access resources. Microsoft Entra ID offers several methods to make this secure and user-friendly.

#### **Microsoft Entra Multifactor Authentication (MFA)**
- **What it is**: Requires users to verify their identity with two or more methods (e.g., password + phone code).
- **Why it matters**: Adds extra security while keeping sign-ins simple.
- **Resources**:
  - Watch: [How to configure and enforce multifactor authentication in your tenant](https://learn.microsoft.com/en-us/entra/identity/authentication/how-to-mfa-getting-started)
  - Read: [Plan a multifactor authentication deployment](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-mfa-deployment-plan)

#### **Conditional Access**
- **What it is**: Automatically controls access based on conditions (e.g., location, device, or risk level). For example, require MFA only for logins from unfamiliar devices.
- **Why it matters**: Balances security and convenience by applying rules when needed.
- **Resources**:
  - Read: [What is Conditional Access?](https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview)
  - Read: [Plan a Conditional Access deployment](https://learn.microsoft.com/en-us/entra/identity/conditional-access/plan-conditional-access)

#### **Microsoft Entra Self-Service Password Reset (SSPR)**
- **What it is**: Lets users reset their passwords without IT help.
- **Why it matters**: Saves time for users and IT staff.
- **Resources**:
  - Read: [Passwordless authentication options for Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-authentication-passwordless)
  - Read: [Plan a Microsoft Entra self-service password-reset deployment](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-sspr-policy)

#### **Passwordless Authentication**
- **What it is**: Allows sign-ins without passwords using tools like the **Microsoft Authenticator app** or **FIDO2 security keys**.
- **Why it matters**: Makes logins faster and more secure by eliminating passwords.
- **Resources**:
  - Read: [Enable passwordless sign-in with Microsoft Authenticator](https://learn.microsoft.com/en-us/entra/identity/authentication/howto-authentication-passwordless-phone)
  - Read: [Plan a passwordless authentication deployment in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-passwordless-deployment)

**Example**: Instead of calling IT to reset a password, an employee uses their phone to verify their identity and set a new password.

---

### Applications and Devices
This section covers how to integrate apps and devices with Microsoft Entra ID to improve productivity and security.

#### **Single Sign-On (SSO)**
- **What it is**: Lets users sign in once to access multiple apps without re-entering credentials.
- **Why it matters**: Simplifies access and reduces password fatigue.
- **Resources**:
  - Read: [What is SSO in Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)
  - Read: [Plan a SSO deployment](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/plan-sso-deployment)

#### **My Apps Portal**
- **What it is**: A web portal where users can find and access their apps, request access to new ones, or manage resources.
- **Why it matters**: Boosts productivity by giving users self-service tools.
- **Resource**: [My Apps portal overview](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/my-apps-portal-end-user-access)

#### **Devices**
- **What it is**: Integrates devices (e.g., laptops, phones) with Microsoft Entra ID for secure access.
- **Why it matters**: Ensures only trusted devices can access company resources.
- **Resource**: [Plan your Microsoft Entra device deployment](https://learn.microsoft.com/en-us/entra/identity/devices/plan-device-deployment)

**Example**: An employee logs into the My Apps portal once and accesses all their work apps, like email and project management tools, without signing in again.

---

### Hybrid Scenarios
Hybrid scenarios involve connecting on-premises systems (like servers in your office) with Microsoft Entra ID in the cloud.

#### **Active Directory Federation Services (AD FS)**
- **What it is**: Moves user authentication from on-premises systems to the cloud using methods like **pass-through authentication** or **password hash sync**.
- **Why it matters**: Simplifies management by leveraging cloud authentication.
- **Resources**:
  - Read: [What is federation with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/whatis-federation)
  - Read: [Migrate from federation to cloud authentication](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/migrate-from-federation-to-cloud-authentication)

#### **Microsoft Entra Application Proxy**
- **What it is**: Allows secure access to on-premises apps without needing a **VPN** or **DMZ** (demilitarized zone).
- **Why it matters**: Enables remote work by securely connecting to internal apps.
- **Resources**:
  - Read: [Remote access to on-premises applications through Microsoft Entra application proxy](https://learn.microsoft.com/en-us/entra/identity/app-proxy/application-proxy)
  - Read: [Plan a Microsoft Entra application proxy deployment](https://learn.microsoft.com/en-us/entra/identity/app-proxy/application-proxy-deployment-plan)

#### **Seamless Single Sign-On (Seamless SSO)**
- **What it is**: Automatically signs users into Microsoft Entra ID on corporate devices connected to the company network, often without needing usernames or passwords.
- **Why it matters**: Makes logins effortless for employees in the office.
- **Resources**:
  - Read: [Microsoft Entra SSO: Quickstart](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/how-to-connect-sso-quickstart)
  - Read: [Microsoft Entra seamless SSO: Technical deep dive](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/how-to-connect-sso)

**Example**: An employee working from home uses Application Proxy to access an internal HR app securely without a VPN.

---

### Users
This section focuses on managing **user identities** (e.g., employee or external user accounts).

#### **User Identities**
- **What it is**: Automates creating, updating, or removing user accounts in cloud apps like Dropbox, Salesforce, or ServiceNow.
- **Why it matters**: Saves time and ensures accuracy in managing user access.
- **Resource**: [Plan an automatic user provisioning deployment in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/plan-auto-user-provisioning)

#### **Microsoft Entra ID Governance**
- **What it is**: Manages the **identity lifecycle** (e.g., onboarding, transfers, terminations) using rules linked to HR systems like Workday or SuccessFactors. It automates IT actions like creating or disabling accounts.
- **Why it matters**: Ensures the right people have access at the right time.
- **Resources**:
  - Read: [Plan cloud HR application to Microsoft Entra user provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/plan-cloud-hr-provision)
  - Read: [Secure access for a connected world—meet Microsoft Entra](https://learn.microsoft.com/en-us/entra/fundamentals/whatis)

#### **Microsoft Entra B2B Collaboration**
- **What it is**: Allows secure collaboration with external users (e.g., partners or vendors) by giving them access to your apps.
- **Why it matters**: Simplifies working with people outside your organization.
- **Resources**:
  - Read: [B2B collaboration overview](https://learn.microsoft.com/en-us/entra/external-id/b2b-overview)
  - Read: [Plan a Microsoft Entra B2B collaboration deployment](https://learn.microsoft.com/en-us/entra/external-id/b2b-collaboration-deployment-plan)

**Example**: When a new employee starts, their account is automatically created in all necessary apps based on HR data.

---

### Identity Governance and Reporting
Governance ensures proper access management, while reporting tracks system activity to meet security and compliance needs.

#### **Microsoft Entra ID Governance**
- **What it is**: Automates access management, delegates tasks to business teams, and provides visibility into who has access to what.
- **Why it matters**: Improves productivity, strengthens security, and ensures compliance.
- **Resources**:
  - Read: [Govern access for applications in your environment](https://learn.microsoft.com/en-us/entra/id-governance/identity-governance-applications)

#### **Privileged Identity Management (PIM)**
- **What it is**: Manages high-level access (e.g., admin roles) with **just-in-time (JIT) access**, approval workflows, and access reviews to prevent misuse.
- **Why it matters**: Reduces the risk of unauthorized access to critical systems.
- **Resources**:
  - Read: [Start using Privileged Identity Management](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management-start-using)
  - Read: [Plan a Privileged Identity Management deployment](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management-deployment-plan)

#### **Reporting and Monitoring**
- **What it is**: Tracks system activity to ensure security, compliance, and performance, with dependencies on legal, security, and operational factors.
- **Why it matters**: Helps identify and fix issues quickly.
- **Resource**: [Microsoft Entra reporting and monitoring deployment dependencies](https://learn.microsoft.com/en-us/entra/monitoring-health/concept-deployment-dependencies)

#### **Access Reviews**
- **What it is**: Regularly checks who has access to resources to ensure it’s still appropriate.
- **Why it matters**: Prevents outdated or unnecessary access that could pose risks.
- **Resources**:
  - Read: [What are access reviews?](https://learn.microsoft.com/en-us/entra/id-governance/access-reviews-overview)
  - Read: [Plan a Microsoft Entra access reviews deployment](https://learn.microsoft.com/en-us/entra/id-governance/access-reviews-deployment-plan)

**Example**: PIM ensures only approved admins get temporary access to sensitive systems, and access reviews confirm they still need it.

---

### Best Practices for a Pilot
A **pilot** is a small-scale test to ensure the system works before rolling it out to everyone. It helps identify issues early.

#### **Pilot: Phase 1**
- **What to do**: Test with a small group, including IT, usability testers, and other users who can provide feedback.
- **Why it matters**: Feedback helps fix problems and improve communication for the full rollout.
- **Example**: IT tests MFA with a few employees to ensure it’s easy to use.

#### **Pilot: Phase 2**
- **What to do**: Expand the pilot to larger groups using **dynamic membership** (automatic group assignments based on rules) or manual additions.
- **Why it matters**: Tests the system with more users to confirm scalability.
- **Resource**: [Dynamic membership rules for groups in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/users/groups-dynamic-membership)

**Example**: After a successful small pilot, add a whole department to test SSO across more apps.

---
### Why This Matters
This deployment plan helps you:
- **Involve the right people** using the RACI model to avoid confusion.
- **Secure access** with MFA, Conditional Access, and passwordless options.
- **Simplify app access** with SSO and the My Apps portal.
- **Support hybrid setups** to connect on-premises and cloud systems.
- **Automate user management** to save time and reduce errors.
- **Ensure governance and compliance** with tools like PIM and access reviews.

Think of it as building a secure, user-friendly bridge that connects your team to the tools they need, whether they’re in the office, at home, or working with external partners. The provided resources guide you through each step to make the deployment smooth and effective.

### References & Further Reading

https://learn.microsoft.com/en-us/entra/architecture/deployment-plans
https://www.youtube.com/watch?v=qNndxl7gqVM

---

## Microsoft Entra identity and access management operations reference guide

https://learn.microsoft.com/en-us/entra/architecture/ops-guide-iam
## Microsoft Entra authentication management operations reference guide

https://learn.microsoft.com/en-us/entra/architecture/ops-guide-auth

## Microsoft Entra ID Governance operations reference guide

https://learn.microsoft.com/en-us/entra/architecture/ops-guide-govern
## Microsoft Entra general operations guide reference

https://learn.microsoft.com/en-us/entra/architecture/ops-guide-ops

## # Microsoft Entra security operations guide

https://learn.microsoft.com/en-us/entra/architecture/security-operations-introduction
## Microsoft Entra ID (Formerly Azure Active Directory)



---

## References

https://learn.microsoft.com/en-us/entra/fundamentals/whatis
https://learn.microsoft.com/en-us/entra/fundamentals/create-new-tenant