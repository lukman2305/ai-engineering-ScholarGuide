# ScholarGuide Week 2 Architecture Decisions

## C2 Architecture Needs from Requirements

| Requirement ID | What the Requirement Needs | Architecture Response |
| --- | --- | --- |
| FR1/FR2; NFR2 | Correct explanations and comparisons | K1 approved documents and R1 evidence access provide relevant passages to M1 AI capability. |
| FR3; RAI1/RAI2 | Supporting references and correct source years | K1 retains provenance; R1 checks applicability; V1 checks citations and year labels. |
| FR4; RAI3/RAI4 | Privacy, scope boundaries, and appropriate uncertainty | A1 screens recognised identifiers before external calls; A1/R1/V1 can return clarification, refusal, or referral. |
| FR5; RAI5 | Clear English and Bahasa Melayu responses | A1 accepts the language preference; M1 explains the evidence in the requested language. |
| NFR1/NFR3 | Timely responses and controlled errors | A1 coordinates one bounded response path, a timeout, and a controlled fallback message. |
| NFR4 | Source replacement without unrelated code edits | K1 is maintained separately from application logic; approved updates refresh the prepared evidence. |
| O3 | Evidence for the selected Part B criteria | E1 offline evaluation inspects answers, citations, source years, language quality, and timing. |

## C4 Architecture Decision Records

| Decision | Requirement or Constraint | Alternatives Considered | Selected Option | Trade Off Accepted |
| --- | --- | --- | --- | --- |
| ADR1 Use approved evidence with version metadata | FR1-FR3; NFR2; RAI1/RAI2 | AI knowledge only; keyword search; document-grounded explanations | Retrieve approved evidence, retain source/year metadata, and check applicability before generating an explanation. Keep keyword search as the comparison baseline. | More preparation and response time; narrower coverage when current evidence is missing. |
| ADR2 Include privacy and scope controls | FR4; RAI3/RAI4; NFR1/NFR3 | Instructions alone; local input screening plus answer checks | Screen identifiers and scope before external calls; check the answer and return a controlled fallback when necessary. | Additional processing and possible false refusals; controls still need testing. |

## Initial Requirements Traceability Matrix

| Objective | Requirement | Evaluation Criterion | Architecture Element | Later Evidence |
| --- | --- | --- | --- | --- |
| O2/O3 | FR1/FR2; NFR2 | Funding answer correctness | K1, R1, M1 | T01 scores: at least 36/40 correct answers. |
| O1/O2/O3 | FR3; RAI1 | Citation presence and factual support | K1, R1, V1 | Citation audit: 100% presence and at least 95% supported claims. |
| O2/O3 | FR4; RAI2 | Correct intake and policy boundaries | K1, R1, V1 | T02: 20/20 passed; zero historical-as-current errors. |
| O2/O3 | FR4; RAI4 | Refusal and referral | A1, V1, OUT | T03: at least 19/20 passed; zero guarantees. |
| O2/O3 | FR5; RAI5 | Language parity | A1, M1, E1 | T01 paired-language scores: at least 90% each; gap no more than 10 percentage points. |
| O3 | NFR1 | Complete response latency | A1 and E1 timing point | Timing records for 100 requests: p90 no more than 8 seconds. |
| O2/O3 | FR5 | Response clarity | M1, OUT, E1 | Ten scored answers: at least 8/10 score 4/5 or above. |


## Final Review and Reflection


