# Detection Searches — Case 01 SSH Brute Force

## 1) Raw failed SSH events
``spl
index=main sourcetype=Ubuntu-Victima "Failed password"``

### Purpose
Used to identify raw authentication failure events.

## 2) Failed attempts by source IP

`` index=main sourcetype=Ubuntu-Victima "Failed password"
| rex "from (?<src_ip>\d+\.\d+\.\d+\.\d+)"
| stats count by src_ip
| sort - count``

### Purpose
Highlights the source IPs generating the most failed SSH login attempts.

## 3) Failed attempts by username

``index=main sourcetype=Ubuntu-Victima "Failed password"
| rex "for (invalid user )?(?<user>\w+)"
| stats count by user
| sort - count``

### Purpose
Shows which usernames are being targeted.

## 4) Brute force trend over time

``index=main sourcetype=Ubuntu-Victima "Failed password"
| timechart span=5m count``

### Purpose
Visualizes spikes in failed authentication activity over time.
