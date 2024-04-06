# 	 		Assignment_2
#	 Automating Anomaly Detection and Alerting in Cloud Security

## Team Members:

* Ahmad Sultan
* Akin Kuyga
* Chowdhurysal Ferdowsy
* Cameron Barber
* Jaehoandrew Han

## Steps are taken:

## Part 1: Understanding Anomaly Detection

### Anomaly detection refers to the process of identifying unusual patterns that deviate from the norm in a dataset. These anomalies can indicate potential problems, such as security breaches, fraud, or system failures. The technique is widely used in various fields, including cloud security, finance, and healthcare, to proactively identify and respond to unexpected events before they can cause significant impact.

### Anomaly detection in cloud security can be understood as a way to spot unusual activity that might indicate a security threat. Just like a security camera that alerts you to unexpected movement, anomaly detection systems in cloud computing constantly watch over data and activities, ready to flag anything that doesn't look right.

### For instance, if someone repeatedly tries to guess a password and fails, or if there's a sudden spike in data traffic that's out of the ordinary, these could be signs of a security breach. Researchers like An et al. (2015) and Chandola et al. (2009) have developed methods that teach computers to recognize these potential threats automatically. These methods learn from past data to identify what normal activity looks like so they can pick up on anything abnormal.

### To explore anomaly detection further, especially within cloud security, you could consider the various methodologies and frameworks that have been studied and applied. For example, an et al. (2015) developed an anomaly detection model based on machine learning that can efficiently process and identify unusual patterns in large-scale data. Additionally, Chandola et al. (2009) provides a comprehensive survey of anomaly detection techniques across different domains, highlighting the specific challenges in the area of network security. These resources can provide detailed insights and methodologies for detecting irregularities in security logs and system behaviors.

### An, J., Cho, S., & Han, I. (2015). The use of a neural network in the detection of abnormal access to the 	cloud system. Expert Systems with Applications, 42(3), 1451-1458.
### Chandola, V., Banerjee, A., & Kumar, V. (2009). Anomaly detection: A survey. ACM computing surveys 	(CSUR), 41(3), 15.
.

## Part 2: Preparing for Automation Azure Automation Account Setup:

### Create an Azure Automation account if one does not already exist.
 
### Familiarize yourself with runbooks and their use in automation.

### Azure Logic Apps Setup:

Create an Azure Logic App.
Understand how to set up triggers and actions within a Logic App workflow.

Connect to Azure Log Analytics:

## In the first attempt we failed because of region-mappings issu with Azure automation account and Azure Log analytics work space. After few hours research, we started from beginnig (creeateing RG) to creating and setting Logic app part (all in the screenshots), and after 2 times fail login attempts notify via email. 

* https://learn.microsoft.com/en-us/azure/automation/how-to/region-mappings 

## First attempt:

- Create RG, Azure automation account and Azure Log analytics workspace, VM Linux server, create runbooks and connect all syslogs with log analytics workspace and auutomatin account:

![A screenshot of a computer Description automatically
generated](./Screenshots/2a0.png)

![A screenshot of a computer Description automatically
generated](./Screenshots/2a.png)

![A screenshot of a computer Description automatically
generated](./Screenshots/2b.png)

![A screenshot of a computer Description automatically
generated](./Screenshots/2c.png)

![A screenshot of a computer Description automatically
generated](./Screenshots/2d.png)

![A screenshot of a computer Description automatically
generated](./Screenshots/2e.png)

![A screenshot of a computer Description automatically
generated](./Screenshots/2f.png)

![A screenshot of a computer Description automatically
generated](./Screenshots/2g.png)

![A screenshot of a computer Description automatically
generated](./Screenshots/2h1.png)

![A screenshot of a computer Description automatically
generated](./Screenshots/2h2.png)

- unfortunately could not proceed because we cannot connect wokspace and automation account shown below picture.

![A screenshot of a computer Description automatically
generated](./Screenshots/2k.png)

![A screenshot of a computer Description automatically
generated](./Screenshots/2k1.png)

## Secont try with selecting Canada Central for all resources:

![A screenshot of a computer Description automatically
generated](./Screenshots/2.1.1.png)

 - connect VM to Log Analytics and enable to insights for VM to Azure WorkAnalytics Workspace

![A screenshot of a computer Description automatically
generated](./Screenshots/2.5.a.png)

![A screenshot of a computer Description automatically
generated](./Screenshots/2.5.b.png)

![A screenshot of a computer Description automatically
generated](./Screenshots/222.png)


![A screenshot of a computer Description automatically
generated](./Screenshots/2.5.c.png)

- connect automation account and log analytics (SUCCESS !!!)

![A screenshot of a computer Description automatically
generated](./Screenshots/2.7.a.png)

![A screenshot of a computer Description automatically
generated](./Screenshots/2.7.b.png)

![A screenshot of a computer Description automatically
generated](./Screenshots/2.7.c.png)

## Part 3: Implementing Anomaly Detection

- Azure automation runbook is created (TEST) and it is success, tested and it is working:

![A screenshot of a computer Description automatically
generated](./Screenshots/2.9.a.png)

![A screenshot of a computer Description automatically
generated](./Screenshots/2.9.b.png)

![A screenshot of a computer Description automatically
generated](./Screenshots/2.9.c.png)

![A screenshot of a computer Description automatically
generated](./Screenshots/2.9.c1.png)

![A screenshot of a computer Description automatically
generated](./Screenshots/2.9.c2.png)

![A screenshot of a computer Description automatically
generated](./Screenshots/2.9.c3.png)

![A screenshot of a computer Description automatically
generated](./Screenshots/2.9.c4.png)

![A screenshot of a computer Description automatically
generated](./Screenshots/2.9.c5.png)

![A screenshot of a computer Description automatically
generated](./Screenshots/2.9.c6.png)


- Azure automation runbook is created to triger for 2 times (treshold) login failure, and create alert via Logic App, send an email for notify.
* (we used Logic app for only to send email for notification purpose)
 
![A screenshot of a computer Description automatically
generated](./Screenshots/2.3.1.png)

![A screenshot of a computer Description automatically
generated](./Screenshots/2.3.2.png)

![A screenshot of a computer Description automatically
generated](./Screenshots/2.3.3.png)

![A screenshot of a computer Description automatically
generated](./Screenshots/2.3.4.png)

![A screenshot of a computer Description automatically
generated](./Screenshots/2.3.5.png)

![A screenshot of a computer Description automatically
generated](./Screenshots/2.3.6.png)

![A screenshot of a computer Description automatically
generated](./Screenshots/2.3.7.png)

-Check login failure from Log Analyticd Workspace:

![A screenshot of a computer Description automatically
generated](./Screenshots/9.d.1.png)

![A screenshot of a computer Description automatically
generated](./Screenshots/9.d.2.png)

![A screenshot of a computer Description automatically
generated](./Screenshots/9.d.3.png)

![A screenshot of a computer Description automatically
generated](./Screenshots/9.d.4.png)

![A screenshot of a computer Description automatically
generated](./Screenshots/9.d.5.png)

![A screenshot of a computer Description automatically
generated](./Screenshots/9.d.6.png)

-After more than 2 times logon failure:

![A screenshot of a computer Description automatically
generated](./Screenshots/email.png)

## Part 4: Integrating Cloud Security Best Practices :


### Alert Escalation:

Defining Severity Levels: We should create different severity levels for alerts, such as Informational, Warning, and Critical. This could be based on the number of failed login attempts, the nature of the accessed resource, or unusual patterns that might indicate a threat.

### Establishing an Escalation Path: For each severity level, we need to establish a clear escalation path:

Informational: We log the event for auditing; no immediate action is taken.
Warning: We notify the IT security team via email or a ticketing system for further investigation.
Critical: We escalate immediately to senior IT staff, potentially invoke an automated response, and alert external cybersecurity services if necessary.
Incident Response Instructions: We must document specific instructions for responding to incidents at each severity level, detailing:

Initial response actions such as alert verification and impact assessment.
Investigation procedures, including log reviews and system checks.
Containment strategies, such as disabling affected accounts or isolating systems.
Eradication and recovery processes, like changing credentials and applying patches.
Follow-up actions to fortify defenses and prevent recurrence.
Regular Updates:
Updating Detection Rules: We should establish a routine for periodically reviewing and updating our detection rules, which includes:

Keeping abreast of emerging threat intelligence.
Analyzing patterns from past incidents to refine our detection mechanisms.
Adjusting alert thresholds based on the balance between sensitivity and false positives.
Automating Rule Updates: We aim to automate the updates to detection rules where feasible, using threat intelligence feeds and cybersecurity services that can dynamically adjust rules according to the latest threat landscape.

### Least Privilege Access:
Permission Reviews: We'll regularly audit the permissions of our Azure Automation account and Logic Apps to ensure compliance with the least privilege principle:

Confirming the Automation account's permissions are strictly necessary for its functions.
Assigning only essential roles to Managed Identities in Logic Apps for executing their actions.
Access Monitoring: We'll implement monitoring to alert on any permission changes or use of high-privileged operations, indicative of potential security issues.

Auditing and Logging: We will enable comprehensive auditing and logging to track operations, by whom they're performed, and when. Utilizing Azure Monitor and Azure Log Analytics will help maintain logs and create alerts for any unauthorized access attempts.

### Incident Response plan:


* 1. Preparation:

Maintain an up-to-date list of contacts for incident response team members.
Ensure all team members are trained and familiar with the response procedures.
Regularly update and test our security tools and processes.
Create and maintain documentation for systems, networks, and logging capabilities.
* 2. Identification:

Determine the nature and scope of the incident. Is it a false positive, or a real threat?
Gather evidence, logs, and related information.
Document everything from the start. Use a predefined incident form to capture data.
* 3. Containment:

Short-term: Isolate affected systems to prevent further damage. This might involve disconnecting them from the network.
Long-term: Implement strategy to prevent the spread and further exploitation of the issue while maintaining business continuity.
* 4. Eradication:

Remove the cause of the incident and any associated malware or vulnerabilities.
Update security measures and apply patches.
Reset passwords and credentials if necessary.
* 5. Recovery:

Bring affected systems back online carefully, ensuring they are no longer compromised.
Monitor systems for signs of abnormalities to ensure the threat is neutralized.
Gradually restore services to normal operations.
* 6. Post-Incident Activity:

Conduct a post-mortem meeting to review and analyze the incident. What was the cause? What was the impact? How was it resolved? What can be done better next time?
Update the incident response plan and related documentation with any new findings or procedures.
Provide training or additional resources to team members if gaps in response were identified.
Preserve evidence and logs for potential legal actions or to assist in future incidents.
Documentation:

Keep detailed records of the incident’s timeline and actions taken.
Retain logs and forensic evidence in a secure location for future reference or legal compliance.
Communication:

Inform stakeholders and affected parties about the incident and how it's being addressed, respecting privacy and compliance requirements.
If customer data was breached, follow relevant regulations for notifying affected individuals.
Review and Improve:

Regularly schedule reviews of our incident response plan.
Perform drills and tabletop exercises to keep our response team sharp and ready.
By following these steps, we can ensure a coordinated and effective response to security incidents, minimizing the impact and improving our resilience against future threats.


### Explanation for our script:

Authentication: The script starts by authenticating to Azure using the managed identity of the Azure Automation account. This requires that the managed identity has been granted access to the Azure Log Analytics workspace.
Workspace ID and Query: The script sets the workspace ID and the KQL query based on your requirements. The query looks for instances where there are more than 2 failed login attempts, which could indicate a brute-force attack.

Executing the Query: It then executes the query against your Azure Log Analytics workspace using Invoke-AzOperationalInsightsQuery.

Output: The script checks if there are any results from the query. If results are found, it outputs the time, source IP address, and the count of failed login attempts. Otherwise, it outputs that no anomalies were detected.


## Lastly: 

In this lab, we've gained valuable hands-on experience with Azure's cloud security and automation services. By setting up Azure Automation runbooks and Logic Apps, we've learned how to automate the process of monitoring and responding to security events. Specifically, we discovered how to create and execute scripts that detect anomalies, such as repeated failed login attempts, and we've practiced how to trigger actions in response, like sending alerts via email. This exercise has reinforced the importance of continuous monitoring and the efficiency of automated responses in maintaining a secure cloud environment.

Additionally, we've deepened our understanding of cloud security best practices. We've applied the principle of least privilege to limit access rights for accounts to the bare minimum required to perform their work, which minimizes potential attack vectors. The lab also provided insights into the significance of having a solid incident response plan, ready to be enacted in the event of a security breach. Through this practical application, we've learned that proactive security measures combined with an effective response strategy are essential in protecting cloud-based resources and data.



##  						THANK YOU!


























































