Cynthia Wade - cynthia.wade@okta.com

**Heropa - what is that?** - Cloud based IT Labs Platform

Day 1: On the final day we will get certificate of attendance to claim credits.

We will do polls to review content and ask questions.

We can follow along the demo but Cynthia will gives us time to do it after watching it. Notify Cynthia if the screens are not synchronized or if there are delays.

We will get the presentation, lab guide, **access code and link to get into lab environment.**

Okta Identity Cloud and features. Professional Certificate exam is a pre-requisite before the Administrator exam. This course will help prepare for both. On Day 3 we will review that.

Introductions:

- Kirsten - Regional Manager of Customer Success in Ohio - Okta
- Tim Morris - IT Support Technician, IMI Materials Inc. - Indianapolis, Indiana
- Hina Adnan - Security Engineer - Mars? - New Jersey
- Rob Gorges - Sr. System Administrator, Linux (Bowling Green State University?) - Works with Arlen
- Marcos Martinez - IT Technician, Builders Vision? Chicago
- Andrei Burdujan - Sr. Administration - Calleo? - Montreal
- John Porter - Eventive? Technologies, Texas
- Arien del Castillo - Linux - Works with Rob Gorges - Bowling Green State University
- Annie Varghese - S&P Global - Detroit
- Allen George - S&P Global - Detroit
- Jamie West - And Allen, Siddharth and Annie work together - S&P Global - Detroit
- Siddhart Sappal - Working from Mexico virtually - S&P Global - Mexico

---

Active Directory
Networking
SAML & OAuth 2.0

Discussed the challenges faced which Okta solves:
**LDAP** - Lightweight Directory Access Protocol

How to manage users and update them?
What is Universal Directory?
Add attributes to Users

---

Integrating Existing Directories - Day 1
Integrating Applications - Day 2
	Okta Integration Network
Managing User Profiles in Universal Directory - Day 2
Strengthening Security - Day 3
	Customizing: End User Dashboard and Communication that comes from Okta

---

Practical:
	Sandboxes for Training
	Sandboxes for Practice

Guides:
	For class Lab Guide will give step by step instructions
	Practice Lab Guide won't have step by step instructions

---

Best practices for setting up Administrators - **Applies to our current environment** - Alim

---

Integrating Existing Directories
	Setting up an Okta AD sync agent
	Importing users into Okta and JIT provisioning
	delegating authentication
	Setup multiple threads to improve the Okta AD Sync training agent

#### OIC - Workforce Identity (employees) and Customer Identity (people purchasing services from Company)

SSO:
Using SAML for authentication v/s WF-FED (Microsoft 365) or OIDC
	Okta found Secure Web Authentication

Universal Directory:
Describe any attribute, bring into Okta and then share the User profile with other applications
	Allows us to add attributes to Users that are not there
	Allows data transformation before sharing the User Profile

Advanced Server Access:
Have the ability to provision Users and their Access Policies (covered in Okta Advanced Server Access)

Adaptive MFA:
We have the capacity to setup 2 factors
	We can challenge the Users to provide additional information

User Lifecycle Management (Application Provisioning):
Will make it possible to CRUD User Profiles in Applications
	We can remove access User access to applications with 1 click

Access Gateway:
Solution Developed to setup SSO for on-premises application (like PeopleSoft)

API Access Management:
To control access to any APIs based on various factors (like device, user role, group membership, location, etc.)

Authentication, Authorization, and User Management

*What is AD FS Management?*

### Module 1 - Course Introduction

*arranged the above notes here*
#### Lab: 1-1 - Access the lab environment

*Note: Essentials Org Practical and SF Practical (do yourself)*

1. Okta Credentials
2. Setup MFA
   ![[Pasted image 20260127091221.png]]

*Setup Okta Verify (is that how you set it up on desktop?)*
*Got the prompt to setup MFA when I was trying to log in to the End User dashboard -  noticed it was different for Cynthia who was only prompted when going to the Admin panel - is that standard?*

3. Setup Okta Verify on Mobile Device
4. End User Dashboard

**Navigating to Admin Dashboard:**

### Module 2 - Define Users in Okta

3 types of people we can create in Okta:
1. Okta-sourced
2. Directory-sourced (delegated authentication)
3. Application-sourced (usually an HR App but can be any application)

31 default Base Attributes + custom attributes (while importing mark attributes as optional so that it doesn't fail)
	By default first and last name is required but this can be marked optional
	Required Attributes
		*First Name* - can be marked optional
		*Last Name* - can be marked optional
		*Username (must be in an email format - doesn't need to be a real email)*
		*Primary Email* - *has to be a real email*
		*Secondary Email (optional) - has to be a real email*
			*both receive activation email*

Okta Statuses (review how it is different in all types of sourced profiles):
	Initial States (On-boarding):
		Staged State
		Pending User Action State
	Active State
	Deactivated (Termination State)
		*Removes all applications previously assigned to user (deprovisioned at once)*
		*Removes password for the user so they cannot sign into Okta*
		*Can be reactivated*
	Blocked States:
		Password Reset State
		Password Expired State
		Locked Out State
		Suspended State (*does not remove applications or password - but password may expired depending on policy*)

For Directory Sourced (Blocked States will relate to all 3 types of Users):
	Change the status in AD and the AD Agent will pull the state from AD and push it into Okta
	Manage Password for Users in AD (unless we turn off Delegated Authentication and have policies to do so in Okta)

What about users that come in from Federated Managed IdPs?
	There is an Identity Providers section
		Directory > Profile Editor > Identity Providers

We can create Users individually or through a Bulk Import template CSV file
	Custom attributes must be added to Okta User Profile before importing
	*To download this template*: Directory > People > More Actions > Import Users from CSV > *this template*

#### Lab 2-1: Create Okta-sourced users (Module 2)

- Create the Okta Admin Account
- Create a Personal Account
- Activate the Personal Account

*Note: Have a Primary Admin Account and a Backup Admin Account*

1. ![[Pasted image 20260127101925.png]]
2. ![[Pasted image 20260127102153.png]]
3. ![[Pasted image 20260127102008.png]]
4. ![[Pasted image 20260127102302.png]]

Bulk import CSV for contractors (we can use the CSV to update - use the original CSV)
	ensure login is in username format (email format)
	even if one user has issues the others will be created

#### Administrator

Standard
	Super Admin
		Only account that can assign admin privileges
	Organization Admin
		Cannot Perform Application Management tasks
	Application Admin
		Cannot manage Organization settings
	Help Desk Admin
		Standard Help Desk Tasks
	Read Only Admin
		Can view things but cannot modify Organizational settings
	Group Admin
		Can perform certain user related tasks in a specific group

Custom - for more granular control (least privileged access)

**Admin Dashboard**

Tasks *(3 types of tasks)*
- To-do
- Info
- Error

**Reports** (*System Logs can be accessed from here with pre-defined filers applied*)

Note: By default the reports and system logs are retained for 90 days - if they are needed for longer then download as CSV and store locally

Pre-configured reports

#### Lab 2-2: Assign administrative roles

Note: In the Admin Consloe in general - changes may need to cycle overnight to reflect (the dashboard for example)

Security > Administrators

#### Lab 2-3: Monitor user account activities

Reports > Reports and System Log

### Module 3 - **Integrate Existing Directories**

Best Practice - Setup 2 AD agents

We cannot user JIT Provisioning (Profile is created when User Signs in) without Delegated Authentication (Authentication is outside of Okta w/ the Directory)
	Delegated Authentication is enabled by default when we install the Okta AD agent

![[Pasted image 20260127133250.png]]

The agent is an Okta Account and it will run as a **service**.






---

what are the situations when users don't need to add security methods?
	- Authenticators

pw for shaun.sebastian: Tra!nme1234
pw for ss-test: Boop123@
	Check our Okta Authenticators for the issue 

---

Day 2 - SF Sandbox
