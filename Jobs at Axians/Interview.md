Automating tasks with basic scripting or programming involves writing code to perform repetitive or tedious tasks efficiently. This can be achieved using various scripting and programming languages, depending on the task's complexity and the tools available. Here's an overview:

1. **Tell me about a time when you had to automate a task using scripting or programming:**

In my role as a security researcher / programmer at VUT, I was tasked with creating tools for enhancing our penetration testing capabilities. One specific challenge was the need to automate the process of vulnerability scanning, identification and reporting. To address this, I decided to develop a custom penetration testing tool using Python.

The tool aimed to automate the initial stages of penetration testing, including network reconnaissance, vulnerability scanning, and data analysis. I started by researching common penetration testing methodologies (in IPv6) and identifying key tasks that could be automated to improve efficiency. The key tasks are:
- Automatically scanning the local network. Every time when a new device enters the network, the tool can detect and get the information.
- Combining several tools performing in various penetration testing frameworks.
- Converting retrieved information to json and csv format.
- Cleaning up the network after finishing work.

Using Python and relevant libraries, I created a tool that automated the discovery of hosts, scanned for vulnerabilities, and generated detailed reports with actionable insights for our security team.

During development, I focused on ensuring the tool was user-friendly and configurable for different testing scenarios. I implemented features for customizing scan parameters, managing scan results, and generating comprehensive reports that could be easily interpreted by both technical and non-technical stakeholders.

After implementing the tool, I conducted thorough testing in simulated environments to validate its effectiveness and accuracy. The tool successfully reduced the time required for routine penetration testing tasks, allowing our team to allocate more time to in-depth analysis and remediation efforts.

This automation not only improved the efficiency of our penetration testing processes but also contributed to the overall security posture of our clients. It showcased my ability to bridge programming skills with a deep understanding of cybersecurity principles to develop practical solutions for complex challenges.

2. **Automated testing, unit test, integration test:**

Unit testing involves testing individual units or components of a software independently to ensure they function as expected. In this example,  class `TestPacketParser` contains two unit tests: one for valid packet data (MAC, IP, Payload, Fragmentation field) and another for invalid data. The `parse_packet` function is part of the security tool, and the unit tests ensure that it behaves correctly in different scenarios

Integration testing involves testing the interaction between different components or modules to ensure they work together as intended. Assuming your security tool has a module that interfaces with external APIs to fetch threat intelligence data, you can create integration tests to verify the integration between your tool and the API.

3. **Can you give an example of a reporting dashboard you have created for software engineering metrics:**

Metrics Included:
- Sprint Progress:
    - Burndown chart displaying the remaining work in the current sprint.
    - Velocity chart showing the team's historical performance over sprints.
- Code Quality:
    - Code coverage trends over time.
    - Number of code smells and technical debt evolution.
- Bug Tracking:
    - Number of open, closed, and reopened bugs.
    - Average time to resolve bugs.
- Release Management:
    - Deployment frequency chart.
    - Success rate of deployments.

Visualization:
- Burndown chart: Line chart displaying the work completed versus the work remaining in the current sprint.
- Cycle time report.
- Flow Diagram.
- Pie Chart Report.

4. **How would you approach extracting development lifecycle data from Jira and automating the process:**

To automate the extraction of development lifecycle data from Jira, you can use Jira's REST API along with a scripting or programming language. Here is a step-by-step approach using Python as an example:

### Prerequisites:

1. **Jira Account:** Ensure you have access to a Jira account with the necessary permissions to read the data you're interested in.
    
2. **API Token (for Jira Cloud):** If you're using Jira Cloud, generate an API token from your Atlassian account settings.
    
3. **Python and Requests Library:** Install Python on your machine and the `requests` library, which will help you interact with Jira's REST API.

4. **Understand Jira REST API:** Familiarize yourself with Jira's REST API documentation to understand the available endpoints and how to structure requests. The Jira REST API documentation can be found on the Atlassian website.
    
5. **Authentication:** Use your Jira credentials or API token to authenticate your requests. Include the credentials or token in the headers of your HTTP requests.
    
6. **Identify Data Endpoints:** Determine which Jira REST API endpoints contain the data you need. For development lifecycle data, you might be interested in endpoints related to projects, issues, sprints, or boards.
    
7. **Retrieve Data Using API Endpoints:** Use the appropriate API endpoints to retrieve the desired development lifecycle data. Examples include: Retrieving issues: `/rest/api/3/search?jql=project=YOUR_PROJECT_KEY`

8. **Transform and Store Data:** Once you retrieve the data, you may need to transform it into a suitable format for your needs (e.g., CSV, JSON). You can then store the data in a local file or a database.
 

