# SPLUNK-SSH-OUTBOUND-COMMUNICATION
Splunk SOC lab demonstrating SSH outbound network traffic analysis, destination IP investigation, and daily scheduled security reporting.


# Splunk SSH Outbound Communication Monitoring

## Project Overview
This project demonstrates how to use Splunk Enterprise to investigate outbound network communication originating from an SSH server and create a scheduled daily report for SOC monitoring.

The investigation identifies the top destination IP addresses contacted by the SSH server, summarizes outbound communication, and configures a reusable report that runs automatically every day.

## Tools & Technologies
- Splunk Enterprise
- Search Processing Language (SPL)
- Network Traffic Analysis
- SSH Server Monitoring
- Destination IP Analysis
- Scheduled Reporting
- SOC Investigation and Documentation

## Lab Environment
- Splunk Platform: Splunk Enterprise
- Index: `mydfir-lab1`
- Source IP: `178.128.237.149`
- Report Name: Daily - SSH Server - Outbound Communication
- Report Type: Scheduled Report
- Schedule: Every day at 00:00
- Report Content: Statistics Table
- Time Range Picker: Disabled

## Investigation Objective
- Identify the top destination IPs contacted by the SSH server.
- Monitor outbound network communication.
- Create a repeatable daily scheduled report.
- Provide a statistics table for SOC analyst review.
- Identify unexpected destinations requiring further investigation.

## SPL Investigation Query

### Identify Top 3 Outbound Destination IPs

```spl
index="mydfir-lab1" src_ip=178.128.237.149
| top limit=3 dest_ip
```

## Investigation Findings

The search returned 1,982 events in the displayed time range.

| Destination IP | Events | Percentage |
|---|---:|---:|
| 178.128.225.222 | 1,243 | 62.714430% |
| 43.135.172.223 | 112 | 5.650858% |
| 104.248.150.105 | 112 | 5.650858% |

**Key observation:** Destination IP `178.128.225.222` represented the largest share of the displayed top-three outbound destinations.

Frequency alone does not establish malicious activity. Destination legitimacy requires further investigation and validation against expected SSH server behavior.

## Scheduled Report Configuration

| Setting | Configuration |
|---|---|
| Report Title | Daily - SSH Server - Outbound Communication |
| Report Type | Scheduled Report |
| Schedule | Every day |
| Execution Time | 00:00 |
| Schedule Priority | Default |
| Schedule Window | No window |
| Report Content | Statistics Table |
| Time Range Picker | No |

## SOC Analyst Investigation Workflow

1. Identify the SSH server's source IP.
2. Search outbound communication using Splunk SPL.
3. Identify the top destination IP addresses.
4. Review destination frequency and historical communication.
5. Validate whether destinations are expected for the server.
6. Investigate unusual ports, protocols, and connection patterns.
7. Correlate network traffic with authentication and endpoint activity.
8. Document findings and escalate unexpected activity.

## Recommended Follow-Up

- Investigate destination IP `178.128.225.222`.
- Validate whether all three destination IPs are expected.
- Review connection ports and protocols.
- Check DNS and threat intelligence context.
- Correlate outbound traffic with SSH authentication activity.
- Identify related hosts, users, and processes.
- Document the security justification for expected traffic or escalate suspicious activity.

## Project Evidence

See `Splunk_SSH_Outbound_Communication_Scheduled_Report.pdf` for the full investigation walkthrough, SPL query, destination IP statistics, scheduled report configuration, and screenshots.

## Skills Demonstrated

Splunk Enterprise | SPL | Network Traffic Analysis | SSH Server Monitoring | Destination IP Analysis | Scheduled Reports | SOC Monitoring | Security Investigation | Technical Documentation

