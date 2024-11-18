Chapter 28 on monitoring from the *UNIX and Linux System Administration Handbook, Fifth Edition*, along with example codes and best practices:

### 28.1 AN OVERVIEW OF MONITORING
Monitoring aims to ensure IT infrastructure operates as expected and provides actionable data for management and planning. The basic structure of monitoring involves:
1. **Data Collection**: Gathering raw data from systems and devices.
2. **Evaluation**: Applying rules to determine the appropriate response.
3. **Action and Display**: Triggering alerts and summarizing data through dashboards.

**Example Script**:
A simple Perl script for load monitoring:
```perl
use strict;
use warnings;

my $load = `uptime | awk '{print $(NF-2)}'`;
chomp $load;
if ($load > 5.0) {
    `mail -s "High Load Alert" admin@example.com`;
}
```

### 28.2 THE MONITORING CULTURE
A strong monitoring culture emphasizes:
- **Comprehensive Monitoring**: Monitor everything of value, including high-availability systems.
- **Team Involvement**: Everyone, not just ops, should respond to alerts.
- **Reducing Alert Fatigue**: Tune alerts to minimize false positives.

### 28.3 THE MONITORING PLATFORMS
Monitoring platforms collect, display, and act on data. Key features to evaluate:
- **Data Collection Flexibility**: Support for various data sources.
- **User Interface**: A clear and customizable UI.
- **Cost**: Options range from free (e.g., Zabbix, Icinga) to commercial solutions (e.g., Datadog).
- **Open-Source Real-Time Platforms**: Nagios and Icinga for threshold-based notifications.
- **Time-Series Platforms**: InfluxDB and Graphite, often paired with Grafana for visualizations.

### 28.4 DATA COLLECTION
Tools like **StatsD** collect arbitrary statistics. Example configuration with **Graphite** for data retention:
```conf
[storage-schemas]
pattern = .*
retentions = 10s:12h, 1m:7d, 10m:1y
```

### 28.5 NETWORK MONITORING
**Ping** and tools like **SmokePing** help monitor network reliability. For deeper inspection, **SNMP** is used to extract network device data.

### 28.6 SYSTEMS MONITORING
**Commands**:
- `sar` for comprehensive system activity reports.
- **collectd**: Gathers system metrics for real-time or time-series databases.

**Example `collectd` Configuration**:
```conf
LoadPlugin cpu
LoadPlugin memory
LoadPlugin network
<Plugin network>
  Server "monitoring.example.com" "25826"
</Plugin>
```

### 28.7 APPLICATION MONITORING
Monitors application-specific metrics and performance using tools like **sysdig** and **dtrace**, which can trace system and containerized environments.

### 28.8 SECURITY MONITORING
Incorporates **Intrusion Detection Systems (IDS)** like **OSSEC** and **Fail2Ban** to detect unauthorized activities and protect against brute-force attacks.

### 28.9 SNMP: THE SIMPLE NETWORK MANAGEMENT PROTOCOL
**SNMP** gathers data using hierarchical OIDs defined in MIBs. It's useful for specialized device monitoring.

### 28.10 TIPS AND TRICKS FOR MONITORING
Best practices include:
- **Avoiding Alert Fatigue**: Ensure actionable notifications only.
- **Documenting Procedures**: Maintain runbooks for handling alerts.
- **Monitoring Your Monitors**: Ensure the reliability of your monitoring systems themselves.

### 28.11 RECOMMENDED READING
- *The Art of Monitoring* by James Turnbull.
- Resources like *Monitoring with Graphite* for setting up metrics and visualization.