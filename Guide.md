Challenge Lab Project 2: Build and Orchestrate Multi-Agent Custom Automation Engine using Foundry IQ
Scenario: Modernize Enterprise Operations – Multi-Agent Custom Automation Engine Solution Accelerator
Overall Estimated Duration: 120 minutes
Version: January 23, 2026

Contoso Ltd. is a global enterprise with multiple departments such as Human Resources, IT Operations, Finance, Legal, and Marketing. As the company grows, many of its internal business processes require coordination across teams, systems, and approvals. These workflows are currently manual, time-consuming, and prone to delays due to frequent handoffs and limited visibility.

To modernize its operations, Contoso decides to implement a Multi-Agent Custom Automation Engine powered by AI. Instead of relying on a single automation script or chatbot, Contoso uses a team of specialized AI agents that can collaboratively plan, execute, and validate complex business tasks from a single user request.

In this lab, you will step into the role of a Contoso automation engineer and deploy the multi-agent automation platform. You will explore how AI agents work together to interpret business requests, break them into actionable steps, coordinate across domains, and deliver end-to-end outcomes for real-world enterprise scenarios.

Objective
By completing this lab, learners will be able to:

Understand the architecture of a multi-agent automation system and how multiple AI agents collaborate to solve complex enterprise workflows at Contoso
Deploy the Multi-Agent Custom Automation Engine in Azure using the provided solution accelerator and infrastructure templates
Observe agent orchestration in action, including task planning, delegation, execution, and validation across multiple agents
Execute real-world Contoso business workflows by submitting high-level natural-language requests to the automation engine
Analyze agent behavior and execution flow using logs, traces, and execution summaries
Customize or extend agent capabilities to support additional Contoso business scenarios
Prerequisites
Prerequisites are pre-configured in the CloudLabs environment. If you're using your personal computer or laptop, ensure all essential prerequisites are installed to complete this challenge.

Required Tools:
Azure Portal - https://portal.azure.com/

Development Environment: Visual Studio Code

Azure Developer CLI (azd) - Install or update to the latest version: https://aka.ms/install-azd

Python 3.11+ - Required to run AI agent scripts and manage dependencies: https://www.python.org/downloads/

Git - Used to clone lab repositories: https://git-scm.com/downloads

Docker Desktop - Enables containerization and local testing: https://www.docker.com/products/docker-desktop/

PowerShell Core - Needed for automation scripts: https://learn.microsoft.com/powershell/scripting/install/installing-powershell-on-windows

Important: Lack of permissions is the #1 cause of deployment failures.

Component Definitions
User Interface (UI): Web-based front-end where users submit natural language business requests and monitor multi-agent execution progress.

Agent Framework (Microsoft Agent Framework): Manages the orchestration of multiple LLM-based agents with specialized roles in enterprise automation workflows.

Planning Agent: An LLM-based agent that interprets business requests, breaks them into actionable tasks, and creates execution plans.

Coordination Agent: Oversees workflow between all specialized agents, ensures task delegation, and maintains execution quality across the multi-agent system.

Domain-Specific Agents: Specialized agents for different business functions:

HR Agent: Handles employee onboarding, paperwork, and compliance training workflows
Marketing Agent: Manages product release planning, campaign coordination, and content creation
Customer Success Agent: Analyzes customer satisfaction data and recommends remediation steps
Finance Agent: Reviews RFPs, performs risk assessments, and handles contract compliance
IT Operations Agent: Manages system provisioning, access controls, and technical workflows
Azure OpenAI Endpoint: The foundation LLM (e.g., GPT-4) hosted on Azure that powers each agent's intelligence.

Prompt Engineering Layer: Custom system and user prompts designed to guide agents in enterprise automation tasks.

Microsoft Foundry Toolkit: Provides templates, deployment tools, and configuration for agentic automation workloads on Azure.

Workflow Engine: Manages task execution, dependencies, and handoffs between agents while maintaining state and context.

Output Formatter: Converts agent responses into actionable deliverables, reports, and workflow summaries.

Logging & Telemetry: Tracks agent performance, workflow success rates, and automation metrics for continuous improvement.

Deployment Runtime (Azure): Managed environment using Azure Container Apps that hosts the multi-agent automation application.

Accessing the Azure Portal
To access the Azure portal, open a private/incognito window in your browser and navigate to the Azure Portal: https://portal.azure.com/

On the Sign in to Microsoft Azure tab, you will see a login screen. Enter the following email/username and then click on Next.

Email/Username: [Provided in Environment tab]

Now enter the following password and click on Sign in.

Password: [Provided in Environment tab]

If you see the pop-up Stay Signed in?, click No.

If you see a pop-up You have free Azure Advisor recommendations! Close the window to continue with the challenge.

If you see the pop-up Action Required, click Ask Later.

If a Welcome to Microsoft Azure pop-up window appears, click Cancel to skip the tour.

Challenge Task 1: Provision Azure Resources and Deploy Multi-Agent Framework
Objective: This task involves provisioning necessary Azure cloud resources for the multi-agent automation engine (compute, storage, networking, AI services) and deploying the required language models. It enables seamless integration of AI services with scalable infrastructure for real-time workflow automation and agent coordination.

Instructions
Create a resource group using a clear naming convention(example: agentic-RG)
Deploy only in supported Azure regions(example: East US 2)
Important: Deploy only in supported regions: East US, East US 2, France Central, Southeast Asia, Canada East, Sweden Centra. Deploying outside these regions will cause failures.

VALIDATION CHECK
20/20 Points
Challenge Task 1: Provision Azure Resources and Deploy Multi-Agent Framework
Status: Success
Congratulations on completing the task! Now, it's time to validate it. Here are the steps:

Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task.
If not, carefully read the error message and retry the step, following the instructions in the lab guide.
If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com. We are available 24/7 to help.
Success Criteria
A Resource Group has been created in a supported region
The resource group is ready to host multi-agent automation resources
You have verified the resource group appears in your Azure subscription
Challenge Task 2: Clone and Configure Multi-Agent Application
Objective: This task involves cloning the Multi-Agent Custom Automation Engine project repository from GitHub and configuring the environment settings required for the multi-agent application to run. It includes setting environment variables, dependencies, and deployment parameters to match your Azure infrastructure.

Instructions
Clone the GitHub repository using the following command:

git clone https://github.com/technofocus-pte/Multi-Agent-Custom-Automation-Engine-Solution-Accelerator.git
Open the cloned repo in the VS code.

Open Docker Desktop and keep it running (do not close it). <Note: There is no need to sign-in in the docker.

VALIDATION CHECK
30/30 Points
Challenge Task 2: Clone and Configure Multi-Agent Application
Status: Success
Congratulations on completing the task! Now, it's time to validate it. Here are the steps:

Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task.
If not, carefully read the error message and retry the step, following the instructions in the lab guide.
If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com. We are available 24/7 to help.
Success Criteria
The Multi-Agent-Custom-Automation-Engine-Solution-Accelerator repository has been successfully cloned to the local environment
VS Code is configured with the project folder opened and ready for deployment
Docker Desktop is running and accessible for containerization support
Challenge Task 3: Deploy the Multi-Agent Automation Engine
Objective: In this task, you will use the Azure Developer CLI (azd) to authenticate, configure the environment, provision resources, and deploy your AI-enabled multi-agent automation platform. You will also verify the deployed resources and endpoints.

Instructions
Login to Azure subscription using the following command in the terminal:

az login
Sign in when the browser window opens:

Select Work or school account
Enter your Username (from Environment tab)
Enter the TAP (Temporary Access Pass) token (from the Environment tab)
Click Sign in and then Yes when prompted
Return to the terminal and select your subscription by entering 1.

Set up new environment using:

azd env new agentic-env
Deploy all resources using:

azd up
During deployment, you will be prompted to:

Enter y to login when prompted
Select your current account
Select the given subscription
Select UK South/West US region for azureAiServiceLocation
Select Central US region as location for infrastructure parameters
Select the existing resource group: agentic-RG
Wait for deployment completion (20-30 minutes).

Upload Team Configurations to the web app using:

infra\scripts\Selecting-Team-Config-And-Data.ps1
Deploy all use cases by entering 6 when prompted.

VALIDATION CHECK
50/50 Points
Challenge Task 3: Deploy the Multi-Agent Automation Engine
Status: Success
Congratulations on completing the task! Now, it's time to validate it. Here are the steps:

Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task.
If not, carefully read the error message and retry the step, following the instructions in the lab guide.
If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com. We are available 24/7 to help.
Success Criteria
You have executed azd up to provision and deploy all required resources for multi-agent automation
You have successfully uploaded team configurations using the post-deployment script
The resource group agentic-RG contains all necessary Azure services, including Container Apps, Azure OpenAI, and supporting infrastructure
All five use case scenarios have been deployed and configured
The frontend container app is running and accessible
Challenge Task 4: End-User Testing - Multi-Agent Workflows
Objective: End-user testing involves interacting with the deployed multi-agent automation application from a user's perspective to validate functionality, usability, and performance. This ensures the multi-agent workflow orchestration behaves as expected under real-world enterprise scenarios.

Instructions
Go to the Azure Portal and open the resource group created for this challenge (example: agentic-RG)

From the application resources, locate the frontend application service.

Open the application URL to launch the multi-agent automation interface

From the application’s navigation panel, review the list of available teams. Confirm that five preconfigured teams are visible, each representing a Contoso business scenario.

Use Case 1: Retail Customer Success Team
Scenario: Work with the Retail Customer Success Team to improve customer satisfaction and retention through multi-agent collaboration.

Agents in This Team:

CustomerDataAgent – Accesses internal customer profiles and interaction history

OrderDataAgent – Accesses order, inventory, and fulfilment information

AnalysisRecommendationAgent – Analyzes data and generates recommendations

ProxyAgent – Requests clarification when instructions are incomplete

Testing Steps:

Ensure Retail Customer Success Team is selected.

From Quick Tasks, select "Satisfaction Plan" and submit it.

Wait approximately 15-20 seconds while the system generates a proposed task plan.

Review the output - you will see an analysis of Emily Thompson's satisfaction with Contoso, along with a proposed plan containing four or more steps.

Click the Details button to review the agents involved and their responsibilities.

Click "Approve Task Plan" button.

Observe the execution process (1-2 minutes) including:

Thinking Process

Processing your plan

Coordinating with AI agents

Review the final output generated by the agents.

Use Case 2: Contract Compliance Review Team
Scenario: Explore contract document analysis for compliance and risk assessment through specialized agents.

Agents in This Team:

Contract Summary Agent – Analyzes contract structure and key terms

Contract Risk Agent – Identifies potential risks and compliance issues

Contract Compliance Agent – Validates regulatory compliance requirements

Testing Steps:

Click on the Contoso icon to select a new team.

From the "Current Team" dropdown, choose "Contract Compliance Review Team" and click Continue.

From Quick Tasks, select "NDA Contract Review" and submit it.

Wait approximately 15-20 seconds while the system generates a proposed task plan.

Monitor multi-agent collaboration as different agents contribute their specialized analysis.

Review comprehensive compliance assessment generated through agent coordination.

Click the Details button to review the agents involved and their responsibilities.

Click "Approve Task Plan" button.

Observe the execution process (1-2 minutes) including:

Thinking Process

Processing your plan

Coordinating with AI agents

Review the final output generated by the agents

Use Case 3: RFP Team
Scenario: Explore RFP and contract document analysis for summarization, risk evaluation, and compliance validation through specialized agents.

Agents in This Team:

RFP Summary Agent – Summarizes RFP and contract documents into structured, easy-to-understand overviews

RFP Risk Agent – Identifies delivery, financial, operational, and compliance-related risks

RFP Compliance Agent – Detects compliance gaps against regulations, policies, and standard contracting practices

Testing Steps:

Click on the Contoso icon to select a new team.

From the Current Team dropdown, choose RFP Team and click Continue.

From Quick Tasks, select “RFP Document Summary” and submit the request.

Review the initial output as the system triggers Generating Plan Action and presents a Proposed Plan with three or more steps.

Click the Approve Task Plan button to proceed with execution.

Monitor multi-agent collaboration as the RFP Summary, Risk, and Compliance agents contribute their specialized analysis.

Review the final consolidated RFP assessment generated through coordinated agent execution.

Use Case 4: Product Marketing Team
Scenario: Explore product-related marketing workflows, including product information retrieval and campaign content generation, through coordinated multi-agent collaboration.

Agents in This Team:

Product Agent – Provides product details, supports product management activities, analyzes sales data, and coordinates with marketing and support teams

Marketing Agent – Focuses on marketing strategy, campaign creation, and market data analysis

Proxy Agent – Acts as a clarification agent when user instructions are unclear or additional details are required

Testing Steps:

Click on the Contoso icon to select a new team.

From the Current Team dropdown, choose Product Marketing Team and click Continue.

From Quick Tasks, select “Draft a press release” and submit the request.

Review the initial output as the system triggers Generating Plan Action and displays a Proposed Plan with three or more steps.

Click the Approve Task Plan button to proceed with execution.

Monitor multi-agent collaboration as the Product, Marketing, and Proxy agents contribute their specialized inputs.

Review the final marketing content generated through coordinated agent execution.

Use Case 5: HR Onboarding Team
Scenario: Explore employee onboarding workflows, including HR coordination, IT setup, and policy-related activities, through coordinated multi-agent collaboration. This use case demonstrates how multiple specialized agents work together to streamline the onboarding experience for new employees.

Agents in This Team

HRHelperAgent – Assists with employee onboarding, benefits, HR policies, and general HR-related inquiries

TechnicalSupportAgent – Handles IT-related onboarding tasks such as laptop provisioning, email setup, and technical support

ProxyAgent – Acts as a clarification agent when user instructions are unclear or additional details are required

Testing Steps:

Click the Contoso icon and select HR Onboarding Team from the Current Team dropdown, then click Continue.

From Quick Tasks, select Onboard New Employee and submit the request.

Review the Generating Plan Action and examine the Proposed Plan containing three or more onboarding steps.

Click Approve Task Plan to allow the multi-agent workflow to proceed.

When prompted for clarification, provide the following onboarding details in a single response to avoid repeated questions:

 Department: HR, Role: Manager, Start Date: 11/23/2025, Orientation Date: 11/25/2025, Location: Onsite, Email: js@contoso.com, Mentor: Jim Shorts, Benefits Package: Standard, ID Card: Yes, Salary: 70000, Laptop: Dell 14 Plus.
Observe the coordinated execution as HRHelperAgent and TechnicalSupportAgent collaborate to complete HR and IT onboarding tasks.

Review the final onboarding outputs generated by the multi-agent system.

Success Criteria
You have successfully accessed the multi-agent automation application interface

You have tested the Retail Customer Success Team workflow and observed multi-agent collaboration

You have experienced task planning, agent coordination, and execution phases

You have reviewed agent-generated outputs including analysis, recommendations, and action plans

You have tested the Contract Compliance Review Team and observed specialized agent contributions

You understand how different agents collaborate to deliver comprehensive business solutions

Learning Objectives
Upon completion of this challenge lab, participants will have gained practical experience with:

Multi-Agent Architecture: Understanding how specialized AI agents collaborate to solve complex enterprise workflows

Azure AI Services: Implementing Azure OpenAI Service and Microsoft Agent Framework for business automation

Enterprise Workflow Automation: Developing and deploying AI solutions for real-world business process modernization

Agentic AI Systems: Experiencing how multiple agents coordinate, delegate tasks, and maintain execution quality

Business Process Intelligence: Learning to interpret and validate AI-generated workflow automation results

Resources & Documentation
Microsoft Foundry Documentation
Azure OpenAI Documentation
Microsoft Agent Framework
Multi-Agent Systems Best Practices
Azure Developer CLI Documentation