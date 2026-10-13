Version: NAFATH-V2
Track: Software

## Overview
A reliable 5G service for emergency responders requires several IT fields to work together, especially during network congestion, outages, and cyberattacks. Software engineering helps applications handle failed requests and retries without causing unintended duplicate actions. Artificial intelligence can predict network congestion, allowing operators to prepare before performance becomes worse. Mobile applications should support offline work and synchronize important information when connectivity returns. Networking provides dedicated 5G network slices to help prioritize emergency communications. Cybersecurity teams prepare for, detect, respond to, and recover from attacks that could disrupt the service. Data management supports daily reports on service usage across different regions, helping managers understand performance and plan improvements. Together, these six fields support a more resilient, secure, and dependable emergency communication service.

## Software
HTTP safe methods (GET, HEAD, OPTIONS, and TRACE) are intended for reading without changing server state. Idempotent methods include these safe methods plus PUT and DELETE, meaning repeated identical requests have the same intended effect as one request. During 5G outages, an emergency application can retry an idempotent request after losing a response. Retrying a non-idempotent POST without safeguards could create duplicate emergency reports.

Resource: RFC 9110 - HTTP Semantics, Section 9.2 - https://www.rfc-editor.org/rfc/rfc9110.html#section-9.2

## AI
Overfitting occurs when an AI model learns training data too closely and performs poorly on unseen data. For predicting 5G network congestion, cross-validation evaluates the model across different training and validation splits to estimate its performance on new observations. Since network traffic changes over time, TimeSeriesSplit is useful because it trains on earlier data and validates on later periods, helping assess whether predictions are reliable for emergency services.

Resource: scikit-learn User Guide - Cross-validation: evaluating estimator performance - https://scikit-learn.org/stable/modules/cross_validation.html

## Mobile
An emergency mobile application should remain usable when 5G connectivity is lost by displaying locally stored information. Important updates can be saved on the device and queued for synchronization when the network returns. The application should show whether changes are pending or confirmed and handle conflicts between local and server data. Time-critical actions requiring immediate server confirmation must not be presented as successful while offline.

Resource: Android Developers - Build an offline-first app - https://developer.android.com/topic/architecture/data-layer/offline-first

## Networking
5G network slicing allows operators to customize connectivity for different services. For emergency responders, a dedicated network slice could be configured to provide suitable quality of service during network congestion. This can help support important communications when many people are using the network simultaneously. However, network slicing does not eliminate all risks, because shared infrastructure failures may still disrupt connectivity. Operators must also plan for backup communication options.

Resource: GSMA - What is Network Slicing? - https://www.gsma.com/solutions-and-impact/technologies/networks/5g-network-technologies-and-solutions/5g-standalone-networks/network-slicing/

## Cybersecurity
NIST describes four incident response phases: preparation, detection and analysis, containment with eradication and recovery, and post-incident activity. For a 5G emergency service, preparation includes response plans and backup communications. Security teams then investigate suspicious alerts and logs. If an attack is confirmed, they contain the threat, remove malicious components, and restore affected systems. Finally, they document the incident and review lessons learned to improve future responses.

Resource: NIST - Computer Security Incident Handling Guide, Section 3 - https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-61r2.pdf

## Data
A star schema connects a central fact table directly to dimension tables, making filtering and reporting simpler. A snowflake schema normalizes dimensions into multiple related tables, reducing repeated information but adding relationship complexity. For daily 5G usage reports by region, I would choose a star schema with usage measurements in a fact table and separate date and region dimensions. This structure supports clear summaries and easier analysis, although the best design depends on data requirements.

Resource: Microsoft Learn - Understand star schema and the importance for Power BI - https://learn.microsoft.com/en-us/power-bi/guidance/star-schema
## Misconception in My Track

## Open Question
