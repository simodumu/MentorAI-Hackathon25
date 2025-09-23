# AI Agent for Mentoring team members

**MentorAI** is your AI peer—designed to guide, support, and empower you throughout your journey in the team. Whether you're onboarding, skilling up, navigating internal processes, or seeking help with team-specific tasks, MentorAI is always there to assist.

Built for remote and hybrid work environments, MentorAI delivers personalized, role-based learning journeys and real-time guidance. It integrates seamlessly with internal resources and uses Azure AI technologies to provide contextual support tailored to your role, team, and goals.

Think of it as a mentor you can reach out to anytime—whether you're part of a mission-critical team or working in SFMC. It won’t overwhelm you with tons of information. Instead, it offers just what you need, when you need it, helping you stay engaged, confident, and successful.

</div>

## Solution Overview

This solution deploys a web-based chat application with an AI agent running in Azure Container App.

The agent leverages the Azure AI Agent service and utilizes Azure AI Search for knowledge retrieval from uploaded files, enabling it to generate responses with citations. The solution also includes built-in monitoring capabilities with tracing to ensure easier troubleshooting and optimized performance.

This solution creates an Azure AI Foundry project and Azure AI services. More details about the resources can be found in the [resources](#resources) documentation. There are options to enable logging, tracing, and monitoring.

Instructions are provided for deployment through GitHub Codespaces, VS Code Dev Containers, and your local development environment.

</div>

### Solution Architecture

![Architecture diagram showing that user input is provided to the Azure Container App, which contains the app code. With user identity and resource access through managed identity, the input is used to form a response. The input and the Azure monitor are able to use the Azure resources deployed in the solution: Application Insights, Azure AI Foundry Project, Azure AI Services, Storage account, Azure Container App, and Log Analytics Workspace.](docs/images/architecture.png)

The app code runs in Azure Container App to process the user input and generate a response to the user. It leverages Azure AI projects and Azure AI services, including the model and agent.

</div>

### Key Features

MentorAI offers a rich set of features designed to make learning and onboarding seamless, personalized, and effective:
- **Personalization:** MentorAI adapts its responses and learning paths based on the user's role, team, and goals. Whether you're in a mission-critical team or SFMC, the agent delivers relevant, focused support without overwhelming you.
- **Real-Time Guidance:** Provides contextual help for navigating internal tools, understanding processes, and progressing through certification pathways. It acts like a knowledgeable peer who’s always available.
- **Integration with Internal Resources:** Seamlessly connects to internal systems like SharePoint, Teams, and organizational APIs to surface the most relevant content and automate answers.
- **Performance Nudges:** Offers proactive suggestions and reminders to help users stay on track with learning goals, certifications, and team expectations.
- **Scalable Architecture:** Designed to be modular and extensible, MentorAI can easily be adapted to support new roles, departments, and organizational needs.
- **Knowledge Democratization:** Makes expert insights accessible to everyone, reducing dependency on tribal knowledge and enabling faster ramp-up times for new employees.
- **Conversational Interface:** Intuitive chat experience for seamless interaction

</div>

Here is a screenshot showing the chatting web application with requests and responses between the system and the user:

![Screenshot of chatting web application showing requests and responses between agent and the user.](docs/images/webapp_screenshot.jpg)

</div>

## Resource Clean-up

To prevent incurring unnecessary charges, it's important to clean up your Azure resources after completing your work with the application.

- **When to Clean Up:**
  - After you have finished testing or demonstrating the application.
  - If the application is no longer needed or you have transitioned to a different project or environment.
  - When you have completed development and are ready to decommission the application.

- **Deleting Resources:**
  To delete all associated resources and shut down the application, execute the following command:
  
    ```bash
    azd down
    ```

    Please note that this process may take up to 20 minutes to complete.

⚠️ Alternatively, you can delete the resource group directly from the Azure Portal to clean up resources.

</div>

### Resources

Following azure resources are used

| Resource | Description |
|----------|-------------|
| [Azure AI Foundry](https://learn.microsoft.com/en-us/azure/ai-foundry/what-is-azure-ai-foundry) | A unified platform for building intelligent agents that can reason, act, and collaborate. It manages orchestration, tool calls, content safety, and observability—ideal for production-grade AI mentors. |
| [Azure AI Agent Service](https://learn.microsoft.com/en-us/azure/ai-foundry/agents/overview#how-do-agents-in-ai-foundry-work) | Azure AI Foundry Agent Service provides a production-ready foundation for deploying intelligent agents in enterprise environments. Default models deployed are gpt-4o-mini, but any Azure AI models can be specified. |
| [Azure Container Apps](https://learn.microsoft.com/azure/container-apps/) | Hosts and scales the web application with serverless containers |
| [Azure Container Registry](https://learn.microsoft.com/azure/container-registry/) | Stores and manages container images for secure deployment |
| [Storage Account](https://learn.microsoft.com/azure/storage/blobs/) | Provides blob storage for application data and file uploads |
| [AI Search Service](https://learn.microsoft.com/azure/search/) | *Optional* - Enables hybrid search capabilities combining semantic and vector search |
| [Application Insights](https://learn.microsoft.com/azure/azure-monitor/app/app-insights-overview) | *Optional* - Provides application performance monitoring, logging, and telemetry for debugging and optimization |
| [Log Analytics Workspace](https://learn.microsoft.com/azure/azure-monitor/logs/log-analytics-workspace-overview) | *Optional* - Collects and analyzes telemetry data for monitoring and troubleshooting |

### Sample prompt to intract with MentorAI Agent
- **Onboarding Support:**
   - How can you assist me as new Cloud Solution Architects?
   - Can you walk me through the SfMC onboarding checklist?
- **Skill Development:**
   - What are the top 3 skills that senior CSAs in SfMC typically master?
   - Can you recommend learning paths for improving my AI/ML expertise in SfMC?
- **Certification Guidance:**
   - Which certifications are recommended for CSAs in SfMC?
   - How do I prepare for the Azure AI Engineer Associate (AI-102) exam?
- **Internal Process Navigation:**
   - How do you guide users in navigating internal processes specific to the SfMC team?
   - Can you guide me through the escalation process for customer issues?
- **Resource Access:**
   - where do I find necessary documentation or resources?
   - Walk me through the process of using the SfMC-Hub for compliance documentation?
- **Mentorship and Growth prompt:**
   - Can you help me set quarterly goals for my sr CSA role?
   - What are examples of successful career transitions from CSA to Principal roles?

### Extending MentorAI’s Usability Across other Teams
To scale MentorAI beyond SfMC, here’s how you can adapt it for example; ARR, Engineering, or Black Belt team:

1. **Customize Role-Based Guidance**
   - Define purpose and scope for each team (e.g., ARR onboarding, Engineering repo setup).
   - Update welcome behavior to reflect team-specific language.
     
2. **Feed Team Knowledge Base**
   - Ingest team-specific documentation, playbooks, and process guides.
   - Use connectors to pull from SharePoint, OneDrive, or internal wikis.
   - Example: “Let me check the ARR-Hub for the latest escalation steps.”
     
3. **Integrate with Internal Systems**
   - Connect to Entra ID, internal ticketing systems, certification trackers.
   - Enable access to team-specific dashboards or compliance portals.
     
4. **Train with Real Scenarios**
   - Use transcripts, emails, and chat logs to train MentorAI on how each team communicates.
   - Include examples of successful onboarding, escalations, and career growth paths.
     
5. **Enable Feedback Loop**
   - Allow users to rate responses or flag gaps.
   - Use feedback to continuously improve domain-specific knowledge.

### Q&A
1. **What is MentorAI?**
   - MentorAI is a role-based AI assistant designed to guide Cloud Solution Architects (CSAs) in the Support for Mission Critical (SfMC) team. It helps with onboarding, skill development, certification planning, and navigating internal processes—just like a real-world mentor.
2. **How is MentorAI different from Copilot Studio?**
   - MentorAI is purpose-built to support specific teams—such as SfMC, ARR, or GDB—and acts like a professional mentor from within that team. It delivers end-to-end guidance using a focused knowledge base tailored exclusively to that team’s workflows, tools, and best practices.
   - Copilot Studio, on the other hand, is a general-purpose AI assistant designed to serve broader organizational needs. It draws from the entire company’s knowledge base, which can sometimes lead to information overload or less targeted guidance.
3. **What kind of questions can I ask MentorAI?** 
   - You can ask about:
        - SfMC onboarding steps
        - Recommended certifications (e.g., AI-102, SC-100)
        - Internal processes like repo compliance or escalation
        - Career growth paths like CHAPS level
        -Learning resources and skill development plans
            -Example: “How do I prepare for the AI-102 certification?”    
3. **What if MentorAI doesn’t know the answer?**
   - MentorAI responds with:
       - “I don’t have those details right now, but I’ll keep learning.”
       It’s designed to improve over time as more team knowledge is fed into it.
4. **Can MentorAI be used by other teams like ARR or Engineering?**
   -  Yes! MentorAI can be extended to other domains by:
       -Updating its purpose and scope for the new team
       -Feeding team-specific knowledge bases (e.g., ARR-Hub, Engineering playbooks)
       -Training it with real scenarios and internal documents
       -Customizing its welcome behavior and tone  
5. **How does Mentor AI ensure its answers are accurate?**
   - It uses Retrieval-Augmented Generation (RAG) with Azure Cognitive Search to pull relevant content from its knowledge base like; SharePoint, Wikis, and other sources.
6. **What tools and systems does Mentor AI integrate with?**
   - Microsoft Teams, Azure OpenAI, Semantic Kernel, Microsoft Graph, Viva Learning, Microsoft Learn, ServiceNow, Power Automate, and optionally Azure Monitor for KQL queries.
7. **Can Mentor AI automate tasks?**
   - Yes. It can initiate workflows like access requests, approvals, and ticket creation using Power Automate and ServiceNow integrations. Agent needs to be enhanced with these capabilities. 
8. **How does Mentor AI improve the employee experience?**
   - It reduces friction in onboarding, centralizes learning guidance, automates routine tasks, and connects users to the right people and resources—all within the flow of work.
9. **How does Mentor AI handle sensitive data?**
   - It uses Azure AI Content Safety and respects user permissions via Entra ID (Azure AD). It only retrieves content the user is authorized to access and filters out harmful or inappropriate responses.


