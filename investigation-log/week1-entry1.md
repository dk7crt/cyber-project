# Investigation Log Entry 1
**Date:** [Date, 29 April 2026]
**Names:** Adeena Fayyaz, Howard Wai
**Role:** System Hardening Lead 

## Task 2.1 – Initial Hypothesis
- **Working hypothesis:** The attack was a deliberate, targeted cyber incident aimed at stealing intellectual property (the secret pastry recipe) and damaging the reputation of Bee Pies & Pasties. The most likely actor is a competitor with economic motivation, possibly aided by insider knowledge.
- **Threat actor identified:** BarmBuzz Ltd (competitor) – working hypothesis
- **Reasoning:** Timing is highly suspicious: the attack occurred just days after BarmBuzz opened a store 300 metres away. Motivation is clear: economic advantage – stealing the recipe and defacing the website harms Bee Pies' unique selling point. The method (PUT request using curl) shows deliberate tampering, not random scanning. The private IP address (192.168.1.105) suggests the attacker was on the internal network, which could indicate an insider or a compromised insider device, possibly linked to BarmBuzz.
- **CIA properties breached:** Confidentiality – secret recipe, supplier lists, customer data stolen. Integrity – website defaced (index.html overwritten). Availability – website disrupted for legitimate orders.
- **STRIDE categories evidenced:** Tampering (PUT request), Information Disclosure (data stolen), Elevation of Privilege (gained write access), Repudiation (possible).

## Task 2.2 – Confidence and Gaps
- **Confidence rating:** 3/5 (moderate – plausible but needs more evidence)
- **Question 1:** Was the IP address 192.168.1.105 internal or external? (If internal → insider; if external → remote attack)
- **Question 2:** What other logs exist (authentication, database, system) that could show how the attacker gained write access?
- **Question 3:** Has BarmBuzz been linked to similar incidents elsewhere? Or have any employees recently left Bee Pies with grievances?

## Task 2.3 – Initial Risk Register Entry
- **Risk ID:** R-001
- **Risk  description:** Sensitive data (customer records and secret recipe) stolen and website defaced due to unauthorised write access to web server.
- **Threat actor:** BarmBuzz Ltd (competitor) – working hypothesis
- **Asset affected:** Customer database, recipe files, supplier lists, website (index.html)
- **CIA property:** Confidentiality and Integrity
- **Likelihood (1-5):** 4
- **Impact (1-5):** 5 
- **Risk rating (Likelihood x Impact):** 20 (Critical)
- **Recommended treatment:** 1. Block IP 192.168.1.105 immediately. 2. Disable HTTP PUT method. 3. Review and tighten file permissions. 4. Rotate all credentials. 5. Implement logging and alerting. 6. Conduct forensic investigation to find entry point.