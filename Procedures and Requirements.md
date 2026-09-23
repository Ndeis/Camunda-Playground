## 1. Purpose

This document defines simple and clear upgreade request flows for a demo AI agent.

This procedure applies to all aircraft upgrade requests.


---

## 2. The Upgrade Matrix

2.1 "Approved": Upgrade requests for single and multiple aircraft are approved on the spot. 
2.2 "Upgrade Approved": Single aircraft upgrade requests may be approved on the spot. For multiple aircraft requests - the smallest mission-capable aircraft can be guaranteed on the spot. Requests for any larger aircraft must be submitted via the Scheduling Request Form.  
2.3 "Submit for Approval": An upgrade request form must be submitted to scheduling.
2.4 "Director Approval Required": Denied. Human flow.

---

## 3. Operational Context
A customer, referred to as an owner, has made an aircraft upgrade request. This means their gauranteed aircraft does not match the requested aircraft on their reservation. The upgrade matrix provides availability options of upgrades. 

---

## 4. Decision Outcomes

| Code | Outcome | Condition |
| :---- | :---- | :---- |
| APPROVED | Application approved | The requested aircraft is approved for use as an upgrade. |
| PENDING_INFORMATION | Awaiting further information from human-in-the-loop | Missing or invalid information |
| ESCALATED | Human review required | Tool/data unavailable, ambiguous result, or risk flag |
| DENIED | Request denied | No available capacity or human-in-the-loop has chosen to deny the request |

---

## 5. Agent Behavior Rules (Simplified)

5.1 Agent must select one path only based on upgrade request. 
5.2 Agent may make request recommentations a maximum of two times before ESCALATED.  
5.3 Every outcome must log the rule numbers used.  
5.4 Agent must never default to request approval.

---

## 6. Example Upgrade Alternatives Response
Account: 51156 | Request: req-1345 | Flight Date: 2026-09-24 | Requested Aircraft: GL5000/GL5500

The GL5000/GL5500 on September 24th is flagged as "Director Approval Only" in the availability matrix, meaning it cannot be approved on the spot and requires a human escalation flow (Rule 2.4). Per the operational process, alternative upgrade options are being presented.

September 24th Matrix Status for alternatives:

EMB-545: ✅ Upgrade Approved (best available status)
GL7500/GL8000: 📋 Submit for Approval (larger Global family aircraft)
GL6000: 📋 Submit for Approval (comparable large-cabin aircraft)
Rules applied: 2.4, 5.1, 5.2, 5.3
