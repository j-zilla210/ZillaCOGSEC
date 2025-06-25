### June 23 2025 

Due to recent events in the middle east, I was asked to be part of a 4 team *Cybersecurity Incident Response Team* (CIRT).
Our primary goal would be to provide 24/7 monitoring of the company network for suspucious activity.
Our team consists of 3 Analysts and 1 Lead
All analysts are trained in Cybersecurity but this is our first actual tasks as a Security Analyst.

## Initial understanding
Our main goals:
 - Monitor
 - Investigate
 - Report
 - Escalate as needed

Responsibilities:
 - In charge of Log generation for 8 monitored systems (Atlassian, Acumatica, Workday, Azure, Microsoft 365, Microsoft Authenticator, Windows Sign in) 
 - Verifying incident/anomalies threat levels
 - Starting the chain of Custody and contacting the proper entity, if an incident progresses

> I will be noting my progress and my personal "Lessons Learned" 

## Day 1: graveyard (6/23 - 6/24)
> Currently I do not have access to any Cybersecurity systems, waiting for approval and finalization of job details.

### The current tasks: 
 - Monitor CIRT email inbox for any high level alerts and notify Team lead
 - Go over and learn Incident Response Plan

### What I learned:
 - The 6 phases of the incident Life Cycle
 - What the Levels of Escalation are (0-3)
 - How to document incidents
 - Communication Protocol
 - Created a cheat sheet for Escalation & response

## 🔐 Summary Cheatsheet: Incident Escalation & Response

| **Phase**            | **What You Do**                                                  | **Key Contacts**                |
|----------------------|------------------------------------------------------------------|----------------------------------|
| **Detection**        | Notice anomalies (e.g., unusual logins, malware alerts)         | ISO, Help Desk                   |
| **Analysis**         | Review logs, confirm event details, assess threat level         | CIRT Technical Lead              |
| **Escalation**       | Classify the incident using escalation levels (0–3)             | ISO determines the level         |
| **Response**         | Contain incident, collect forensic data, preserve evidence      | IR Lead, Sys Admins              |
| **Documentation**    | Log actions, maintain chain of custody, update status reports  | IR Lead, CIO, Legal if needed    |
| **Recovery**         | Eradicate threat, restore systems, validate security controls   | IT Support, Systems Team         |
| **Post-Incident**    | Contribute to Lessons Learned & After Action Reports           | ISO, IR Lead                     |

### 🛠️ Escalation Levels

- **Level 0**: Routine event or false positive. No threat confirmed.
- **Level 1**: Possible threat. Begin investigation and notify ISO.
- **Level 2**: Confirmed threat. Mobilize CIRT and start containment.
- **Level 3**: Widespread/high severity incident. Full response with external coordination if needed.

📌 **Tip**: Always use uncompromised systems to report incidents and avoid using affected networks for communication.


> **Day ended with no incident**

## Day 2: graveyard (6/24 - 6/25)
> Still no access to system, but was provided access to logs in order to familiarize myself with the content and structure

### Current Tasks:
 - Monitor CIRT inbox for any high level alerts and notify Team Lead
 - Look through Logs to see what recent events look like

### What I found:
On the *Firewall blocked network traffic* excel log. It breaks down the traffic into countries using a table form on one workbook and all the raw individual blocked traffic on another.

#### Looking at the blocked traffic by Country:
 - you can see the number of blocked attempts per country.
 - You can organize the list as well as expand the graph to see more countries

#### Looking at the individual blocked traffic events:
 - You are provided a detailed breakdown of each event, where the attempted connection originated from, what malicious event it was, (these are tyically botnets, especially when attempts are bunched together)
 - The IP addresses the attempt was from, what IP it was hitting, the latitude and longitude of the malicious attempt, the threat level, threat confidence and other information
 - All other logs monitor for failed login attempts. There were not very many suspicious login attempts, most looked to be user error.

> **Day ended with no incident**
