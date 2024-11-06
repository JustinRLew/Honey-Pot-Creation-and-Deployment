## Cowrie SSH Honeypot Project

https://www.youtube.com/watch?v=SsDzZr9zwlI

## Overview
This project involves setting up a medium-interaction SSH honeypot using Cowrie to detect and analyze unauthorized login attempts, particularly brute-force attacks. The honeypot logs attacker behavior and provides insights into attack methods, which are valuable for understanding threat landscapes and enhancing cybersecurity defenses.

## Project Goals
Monitor and log unauthorized SSH access attempts.
Analyze attacker behavior and extract meaningful insights.
Showcase practical cybersecurity skills, including deployment, monitoring, and data analysis.
Demonstrate continuous learning by planning future enhancements.

## Key Features
Medium-Interaction Honeypot: Simulates an SSH service without giving full access to the system.
Detailed Logging: Captures login attempts, commands entered, and connection details.
Email Alerts: Sends real-time alerts for specific attack patterns.
Data Visualization: Visualizes attack data with Python scripts and integration options with tools like Kibana.
Scalability: Plans to expand to multi-region honeypots and integrate with SIEM tools.

## Project Setup
Prerequisites
Google Cloud Platform (GCP) account for VPS setup.
Ubuntu 22.04 LTS as the operating system.
Basic knowledge of SSH and Linux commands.

Step 1: Create a Free VPS on Google Cloud Platform
Sign in to Google Cloud Platform.
Activate the $300 free trial for 90 days.
Create a new project called honeypot-project.
Navigate to Compute Engine > VM Instances and create an e2-micro instance with Ubuntu 22.04 LTS.
Connect to the VPS using SSH.

Step 2: Install Cowrie
Update system packages:
bash

sudo apt-get update && sudo apt-get upgrade -y
Install dependencies:
bash

sudo apt-get install python3 python3-venv git -y
Clone Cowrie repository:
bash

git clone https://github.com/cowrie/cowrie.git
cd cowrie
Set up a virtual environment:
bash

python3 -m venv cowrie-env
source cowrie-env/bin/activate
pip install -U pip setuptools
pip install -r requirements.txt
Step 3: Configure Cowrie
Copy the sample configuration file:
bash

cp etc/cowrie.cfg.dist etc/cowrie.cfg
Edit etc/cowrie.cfg to adjust logging levels and listening port settings:
ini

[ssh]
listen_port = 2222
Step 4: Start Cowrie
Run Cowrie:
bash

bin/cowrie start
Verify it’s running:
bash

tail -f var/log/cowrie/cowrie.log
Logging and Monitoring
Log Location: /path/to/cowrie/var/log/cowrie/
Automated Log Rotation:
bash

sudo apt-get install logrotate -y

## Alerts and Automation
Email Alerts: Set up real-time alerts using sendmail and a custom script to monitor log entries.
Automated Reports: Use Python and cron jobs to generate weekly summaries of attacker activity.
Data Analysis and Visualization
Python Scripts: Visualize attack trends with matplotlib and pandas.
Integration with Kibana: Forward logs to Kibana for interactive dashboards and deeper analysis.

## Future Enhancements
Deploy multi-region honeypots to compare geographic attack patterns.
Add protocol support for Telnet and HTTP services.
Integrate with SIEM tools like Splunk for comprehensive threat intelligence.
Automate response mechanisms with tools like Fail2Ban.

## License
This project is licensed under the MIT License. See LICENSE for details.

## Contact
For questions or collaboration, contact justinlew1000@gmail.com
