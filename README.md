🧠 SIEM Threat Detection using Splunk

📋 Objective

The goal of this project was to simulate and detect suspicious activities — such as multiple failed SSH login attempts — using Splunk as a Security Information and Event Management (SIEM) tool.
The exercise demonstrates how to monitor system logs, detect anomalies, and configure alert rules for automated threat visibility.

🧩 Tools & Technologies

Splunk Enterprise (Free Version)
Linux (Kali)
System Logs (/var/log/auth.log, btmp, syslog)
SSH Service (for simulating failed login attempts)


⚙️ Steps & Configuration

1. Splunk Installation
Installed Splunk using the .deb package:
sudo dpkg -i splunk.deb
Started the Splunk service:
sudo /opt/splunk/bin/splunk start

Accessed the web interface via http://kali:8000

🖼️ Screenshot: splunk-login


2. Log Ingestion
Added local system logs as a data source under:
Settings → Add Data → Upload files → /var/log/
Selected logs such as btmp to track authentication activity.

🖼️ Screenshot: log-ingestion


4. Simulate Failed SSH Logins
Enabled SSH service and simulated repeated failed logins:
sudo systemctl start ssh
for i in {1..10}; do ssh fakeuser@localhost exit; done

Verified log entries using:
sudo grep -i "Failed password" /var/log/auth.log


4. Dashboard & Visualization
Created a new dashboard in Splunk.
Added a search query to visualize login failure attempts:
index=* "Failed password" | stats count by host

Displayed results in line and bar charts.

🖼️ Screenshot: dashboard-overview


5. Alert Configuration
Created an alert rule to trigger when failed SSH attempts exceeded a defined threshold.
Configured the alert to run every hour and send notifications when conditions were met.

🖼️ Screenshots:
alert-setup
alert-running


🧾 Expected Outcome

Splunk successfully identified and visualized failed SSH login attempts.
Alerts were generated when suspicious activity (multiple failed logins) occurred.
Demonstrated understanding of log analysis, SIEM dashboards, and alert configuration.


📸 Screenshots Summary

Screenshot	Description
splunk-login	Initial Splunk login page
log-ingestion	Adding local system logs
dashboard-overview	Visualization of failed login attempts
alert-setup	Alert rule configuration
alert-running	Active alert triggered


📂 Report / Repository

🔗 View Full Project on GitHub


🧠 Skills Demonstrated
Security Event Monitoring
SIEM Configuration
Threat Detection
Log Ingestion & Analysis
Alert Rule Creation
