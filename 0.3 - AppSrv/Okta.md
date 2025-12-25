tag: [[AppSrv]]

Lifecycle Management (LCM) helps connect users with apps
- Offers prescriptive Joiner, Mover, and Leaver paths
- Makes it easy to provision accounts to apps

Lifecycle Management
Joiner -> Mover -> Leaver

Okta Workflows can be thought of as an extension of LCM
- Helps add Logic, Timing and Actions to any process or application
	- For example: in addition to provisioning or creating a base account in the Box application, IT admins can also set entitlements or set folder shares which are app specific actions
- Automating granular actions with scripts or code has 2 issues:
	- Expensive
	- Difficult to maintain

A workflow typically consists of 4 steps:
1. A workflow starts with a trigger or Event.
2. The workflow may then run some Logic
3. Then the workflow performs an Action
4. Then finally we chain another Action in another Application

What are **Events**?

Events trigger flows to run. While flows can be scheduled or run manually, they typically start when an event occurs in an app. This is the starting point of every flow.

There are 5 types of events in the Workflows Console:
1. Application Event: Kicks off a flow when a specific action occurs in a particular application
2. Schedule Flow: Runs on a schedule set by the Administrator
3. Helper Flow: Runs when called from another flow and enables us to process a list or handle errors
4. API Endpoint Flow: Runs when invoked via an HTTP call using specified inputs
5. Delegated Flow: Flow that an Okta Admin can view and run directly from the Okta Admin Console
	- Useful when we want an Admin to run a workflow but don't want to give them full access to Okta Workflows

What are App **Actions**?

App Actions are steps in the flow that control other applications or web services. They trigger actions like sending a message, adding a new record, or updating an existing one. Each card or connector has its own set of actions, so it is important to be familiar with both the system and its structure.

UI: Add App Action to choose the application we want to work with. After choosing the application we need to select the Action Card for that application.

How do **Functions** work?

Functions allow us to interact with, change, or control the data in our flow. A function card is usually placed between App Action cards. This may include a continuation to execute the flow based on a value or conditionally performing an alternative logical flow. Okta Workflows categorizes the function cards to keep similar operations grouped. There are four types of functions you can choose from:

1. **Logic** functions enable you to manage the structure of your flows. These include branching and error handling functions.  They direct the order and sequence of execution of various parts of your flow
   ![[Pasted image 20251208162851.png]]
2. **Manipulation** functions allow you to parse and manipulate data within the flow such as times and dates.  They also allow you to create and iterate over lists of items or values, and even perform mathematical operations.
   ![[Pasted image 20251208163035.png]]
3. Elements functions allow you to export flows and folders as JSON files and configure elements of any tables within a flow.
   ![[Pasted image 20251225090304.png]]
4. Advanced functions allow you to create more complex interactions involving API connectors, JSON, XML, and most types of encryption.
   ![[Pasted image 20251225090407.png]]

Note cards are documentation only.

Applications are integrated into the Flow using connectors which are pre-built frameworks that leverage APIs to allow the Flow to access specific cloud based applications.