# Dataset

This directory contains the information dataset used in the experimental study of collaborative cyber threat analysis based on a Semantic Digital Twin.

## OSINT Dataset

The experimental information context was formed using the **InfoStream information and analytical system**, which provides access to continuously updated collections of open-source information.

The dataset was retrieved specifically for the cybersecurity problem investigated in the experiment rather than collected as a general-purpose cybersecurity corpus.

The thematic search query was:

```text
("phishing" | "spear phishing" | "malicious email" |
 "email attachment" | "fake IT support")
&
("credential theft" | "credential access" |
 "credential dumping" | "stolen credentials" |
 "account compromise")
AND
("lateral movement" | "domain controller" |
 "Active Directory" | "internal network" |
 "privilege escalation")
&
(Windows | workstation | Rendpoint)
