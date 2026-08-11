# Datasets

This directory contains the input datasets used in the experimental study of collaborative cyber threat analysis based on a **Semantic Digital Twin (SDT)**.

The experimental environment combines two complementary data sources:

1. an **OSINT information dataset**, providing the external cybersecurity context used for semantic analysis and RAG-based knowledge extraction;
2. a **network infrastructure model**, providing the structural representation of the corporate network in which the investigated cyberattack scenario is analyzed.

Together, these datasets provide the informational and infrastructural foundations for constructing the Semantic Digital Twin.

---

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
```

The retrieved document collection represents the external information context associated with the experimental attack scenario: social engineering through email, credential compromise, privilege escalation, and subsequent lateral movement within a corporate network.

The OSINT dataset is used by the RAG and agent-based analytical components to identify relevant entities, vulnerabilities, attack techniques, tools, relationships, evidence, and possible attack developments. These elements are subsequently integrated into the Semantic Digital Twin.

---

## Network Infrastructure Dataset

The structural representation of the experimental corporate network is provided in:

[`cicids2017_compact_network.xml`](./cicids2017_compact_network.xml)

The XML file contains a compact machine-readable description of the network infrastructure used as the technical environment of the experiment.

Unlike the OSINT dataset, which represents the dynamically retrieved external information context, the XML dataset defines the **initial structural state of the analyzed network**. It provides the infrastructure layer onto which cybersecurity entities, attack events, vulnerabilities, compromised assets, semantic relationships, and candidate attack paths identified during the analysis can be mapped.

The network description is used as an input for constructing the infrastructure component of the Semantic Digital Twin. During collaborative analysis, this initial representation is semantically enriched with information extracted from the OSINT dataset and with hypotheses and relationships generated or verified by specialized AI agents.

Thus, the experimental Semantic Digital Twin is not constructed solely from textual cybersecurity information. It integrates:

* the **physical/logical network structure** represented by [`cicids2017_compact_network.xml`](./cicids2017_compact_network.xml);
* the **dynamic cybersecurity information context** retrieved from InfoStream;
* the **semantic entities and relationships** extracted through RAG-based analysis;
* the **analytical hypotheses, evidence, contradictions, and attack scenarios** produced and evaluated during multi-agent collaboration.

This combination allows the resulting Semantic Digital Twin to represent both the structure of the protected environment and the evolving knowledge about cyber threats affecting that environment.

---

## Role in the Experiment

The two datasets serve different but complementary functions.

The XML network model defines **where the cyberattack can develop**, while the OSINT collection provides evidence about **how such an attack can develop, which techniques and vulnerabilities may be involved, and which alternative scenarios should be considered**.

Their integration provides the initial context for bidirectional semantic expansion and subsequent construction of the Semantic Digital Twin used by the collaborative multi-agent analysis.
