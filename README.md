SIEM Threat Detection Using Splunk

🎯 Project Overview

This project demonstrates the use of Splunk as a Security Information and Event Management (SIEM) tool to detect suspicious activities on a simulated network. The goal was to configure Splunk to monitor system logs, detect failed SSH login attempts, and create alert mechanisms for real-time threat visibility.

⚙️ Setup Process

Installed Splunk Enterprise (Free) on Kali Linux using the Debian package.

Started Splunk and accessed the web interface at http://localhost:8000.

Configured Splunk to ingest system logs from /var/log/ including btmp.log and other authentication-related logs.

Simulated failed SSH login attempts on the host machine using terminal commands.

Verified log ingestion in Splunk through search queries and created an alert for brute-force detection.

🔍 Detection Logic

Used the following Splunk search query to identify multiple failed SSH login attempts:

index=* "Failed password" | stats count by src_ip | where count > 3


This query counts how many times a failed password attempt occurred per source IP address and highlights IPs exceeding the defined threshold — indicating potential brute-force attempts.

🔔 Alert Configuration

Created an alert to automatically detect and notify of repeated failed login attempts:

Search Query: index=* "Failed password" | stats count by src_ip | where count > 3

Trigger Condition: When number of results > 0

Schedule: Cron expression */1 * * * * (simulating every-minute detection)

Action: Display detection and alert logs in Splunk UI

🖼️ Screenshots Included

splunk-login – Splunk web interface on startup

log-ingestion – Verification of log data successfully ingested

alert-setup – Alert configuration window in Splunk

alert-running – Active alert detecting failed SSH logins

dashboard-overview – Overall interface showing query results and monitoring activity

🧠 Key Skills Demonstrated

SIEM configuration and monitoring

Log ingestion and parsing

Incident detection and alerting

Linux command-line log generation

Security event correlation and analysis

🏁 Outcome

Successfully simulated and detected SSH brute-force attempts using Splunk’s SIEM capabilities.
This project demonstrates practical experience in threat detection, incident response, and log analysis — critical skills for a Security Analyst or SOC role.
