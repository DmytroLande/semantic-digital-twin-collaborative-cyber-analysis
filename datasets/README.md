# Datasets

This directory contains the input datasets used in the experimental study of collaborative cyber threat analysis based on a **Semantic Digital Twin (SDT)**.

The experimental environment combines two complementary data sources:

1. **OSINT information context** — [`RAG-TW-2.docx`](./RAG-TW-2.docx);
2. **network infrastructure model** — [`cicids2017_compact_network.xml`](./cicids2017_compact_network.xml).

Together, these datasets provide the informational and infrastructural foundations for constructing the Semantic Digital Twin.

---

## OSINT Dataset

The OSINT dataset used in the experiment is provided in:

[`RAG-TW-2.docx`](./RAG-TW-2.docx)

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

The resulting document collection was saved as `RAG-TW-2.docx` and represents the external information context associated with the experimental attack scenario: social engineering through email, credential compromise, privilege escalation, and subsequent lateral movement within a corporate network.

The dataset serves as the source collection for **RAG-based retrieval and semantic analysis**. Relevant entities, vulnerabilities, attack techniques, tools, relationships, evidence, and possible attack developments extracted from this collection are used to enrich the Semantic Digital Twin.

---

## Network Infrastructure Dataset

The structural representation of the experimental corporate network is provided in:

[`cicids2017_compact_network.xml`](./cicids2017_compact_network.xml)

The XML file contains a compact machine-readable description of the network infrastructure used as the technical environment of the experiment.

Unlike `RAG-TW-2.docx`, which represents the external cybersecurity information context, `cicids2017_compact_network.xml` defines the **initial structural state of the analyzed network**.

The network model provides the infrastructure layer onto which cybersecurity entities, attack events, vulnerabilities, compromised assets, semantic relationships, and candidate attack paths identified during the analysis can be mapped.

During collaborative analysis, this initial representation is semantically enriched with information retrieved from `RAG-TW-2.docx` and with hypotheses, relationships, evidence, and contradictions generated or verified by specialized AI agents.

---

## Integration into the Semantic Digital Twin

The experimental Semantic Digital Twin is constructed by integrating two complementary representations:

```text
RAG-TW-2.docx
      │
      │  RAG / semantic extraction
      ▼
Cybersecurity information context
      │
      ├──────────────┐
      │              │
      ▼              ▼
Entities         Relations / Evidence
      │              │
      └──────┬───────┘
             │
             ▼
    Semantic Digital Twin
             ▲
             │
     Network infrastructure
             ▲
             │
cicids2017_compact_network.xml
```

Thus, the Semantic Digital Twin combines:

* the **physical/logical network structure** represented by [`cicids2017_compact_network.xml`](./cicids2017_compact_network.xml);
* the **dynamic cybersecurity information context** contained in [`RAG-TW-2.docx`](./RAG-TW-2.docx);
* the **semantic entities and relationships** extracted through RAG-based analysis;
* the **evidence, analytical hypotheses, contradictions, and alternative attack scenarios** generated and evaluated during collaborative multi-agent analysis.

---

## Role in the Experiment

The two datasets serve different but complementary functions.

The network model defines **where the cyberattack can develop**, while the OSINT dataset provides the information necessary to determine **how the attack can develop, which vulnerabilities and techniques may be involved, and which alternative scenarios should be considered**.

Accordingly, the experiment starts from two explicit input files:

| Input                     | File                                                                 | Purpose                                                             |
| ------------------------- | -------------------------------------------------------------------- | ------------------------------------------------------------------- |
| OSINT information context | [`RAG-TW-2.docx`](./RAG-TW-2.docx)                                   | RAG retrieval, semantic extraction, evidence and threat context     |
| Network infrastructure    | [`cicids2017_compact_network.xml`](./cicids2017_compact_network.xml) | Initial structural representation of the analyzed corporate network |

Their integration provides the initial context for **bidirectional semantic expansion**, collaborative multi-agent analysis, and construction of the resulting Semantic Digital Twin.
