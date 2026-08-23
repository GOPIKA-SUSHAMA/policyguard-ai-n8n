PolicyGuard AI — n8n Governance Gate V1



A simple rules-first AI governance workflow built with n8n to review employee AI-use requests.



 V1 Logic



```text

Webhook

&#x20;  ↓

Check Credentials / Secrets

&#x20;  ├── TRUE → BLOCKED

&#x20;  └── FALSE

&#x20;         ↓

Check Personal Data + External AI

&#x20;  ├── TRUE → HUMAN\_REVIEW

&#x20;  └── FALSE

&#x20;         ↓

Check Approved AI Tool

&#x20;  ├── TRUE → APPROVED

&#x20;  └── FALSE → HUMAN\_REVIEW

```



 Decisions



\* \*\*BLOCKED\*\* — credentials or secrets detected

\* \*\*HUMAN\_REVIEW\*\* — personal data sent to external AI or unapproved AI tool

\* \*\*APPROVED\*\* — approved tool with no higher-risk condition triggered



\## Concepts Used



\* n8n Webhooks

\* JSON input

\* IF conditions

\* Deterministic policy rules

\* Conditional routing

\* Structured decision outputs



\## Example Input



```json

{

&#x20; "request\_id": "AI-103",

&#x20; "ai\_tool": "ChatGPT",

&#x20; "contains\_credentials": false,

&#x20; "contains\_personal\_data": false,

&#x20; "external\_ai": true,

&#x20; "approved\_tool": true

}

```



Expected result:



```text

APPROVED

```



\## Next Version



V2 will add \*\*audit logging and decision tracking\*\* before introducing AI-assisted review for ambiguous policy cases.



