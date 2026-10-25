# ScholarGuide Week 2 Requirements Specification

## Section 0 Project Framing and Application Scope

### Problem and Evidence

Students require to understand information from different funding sources and in various versions. One reason for the development of iPANDU is that it was found that there was an increased number of telephone and email enquiries that surpassed the department's capacity [1]. This indicates need for accessible information, not demand for ScholarGuide.

Different funding information will be published separately in the Khazanah Watan programme page and MARA TESP FAQ [2, 3]. This is direct observable fragmentation which encourages comparison support. The dated MARA and JPA PDFs also provide justification for explicit intake/policy boundaries [3, 4]. There are no false survey results.

### Existing Approaches

1. JPA iPANDU [1] organises guidance and supporting resources for sponsored students. Its reviewed content is provider-specific.
2. The Khazanah Watan page [2] structures scholarship information. Cross-provider questions require other sources.
3. MARA TESP FAQs [3] explain common programme questions. Their intake-specific conditions require version-aware interpretation.


### Engineering Gap

One interface is required to describe and compare approved information and to maintain provider, programme and year of origin. ScholarGuide should not combine incompatible conditions but rather show missing or conflicting evidence. A base level of keyword search is still needed and AI is called for only if it provides added value in explanation and comparison.

### Project Objectives

- O1: To design a document-grounded funding information assistant with provenance and responsible AI controls.
- O2: To develop a prototype that explains and compares published information with citations, version boundaries, and appropriate uncertainty.
- O3: To evaluate correctness, citation support, response latency, and handling of outdated or unsupported information against a keyword-search baseline.

### Intended Users

Undergraduate students and student-support staff in Malaysia looking for official funding details.

### Supported Tasks and Knowledge Domain

Explain published requirements, coverage, procedures, historical deadlines and documented conversion conditions. Compare two supported funding options without predicting approval. Start with Khazanah Watan undergraduate information, MARA TESP historical material - use JPA PBU Akademik documents for clearly labelled policy context. Answer English and Bahasa Melayu questions. If there is no current-intake condition or the provider is not listed, then there is an explicit limitation response.

### Operating Context

A single student using a browser-based classroom prototype over an internet connection. A small number of about 3-5 official documents is curated and updated by an operator. The original system is not account-based, does not support private documents to be uploaded and does not integrate with application portals.

### Important Constraints

Limited approved documents, source permissions, changing of intake notices, availability of internet and model-service, and a student budget whose maximum value has not been agreed yet. Version metadata should contain source title, publisher, URL, page/section, access date, publication date (if available), and applicability of intake/policy. If the date or applicability is not known, store unknown rather than make a guess. Avoid sending protected identifiers out in model requests and stored evidence.

### Explicit Out of Scope

Application submission, access to the account, final eligibility and approval, personalised borrowing suggestions, contractual interpretation and guarantees for awards and/or conversion. The annual application pattern does not indicate that applications are open.

### Evaluation Focus and Traceability

Can the system offer valid, verifiable explanations and comparisons, maintain intake boundaries and refuse unsupported decisions within a reasonable time frame? Test it against source-linked references and keyword search. O1 is demonstrated in the design and traceability review; O2 in functional and control tests; O3 in the evaluation methods and subsequently via the results.

## Section 1 Functional Requirements

| ID | Requirement | Scope Boundary |
| --- | --- | --- |
| FR1 | The system shall answer questions about published conditions, coverage, procedures, deadlines, and conversion information within the approved scholarship and convertible-loan collection. | Shall not invent missing conditions or treat a general policy notice as a complete application guide. |
| FR2 | The system shall compare two supported funding options using requested attributes and identify information not specified in either source. | Shall not rank options as personally best, predict approval, or infer that an unmentioned restriction does not exist. |
| FR3 | The system shall attach source title, official URL, page or section, and programme/intake or policy year to document-based answers; show the access date when no publication year is available. | Shall not attach a reference that does not support the associated claim. |
| FR4 | The system shall ask for clarification when the programme or intake is ambiguous, state insufficient or conflicting evidence, and decline out-of-scope decisions with an official referral. | Shall not submit applications, access private accounts, decide final eligibility, interpret personal contracts, or guarantee an award or repayment conversion. |
| FR5 | The system shall accept English and Bahasa Melayu questions and explain information in the requested language, distinguishing scholarship funding from convertible-loan obligations where supported. | Shall not claim equivalent language performance without evaluation. |

## Section 2 Non Functional Requirements

| ID | Quality Attribute | Requirement | Measurement Method | Metric | Threshold |
| --- | --- | --- | --- | --- | --- |
| NFR1 | Performance | The system shall provide a complete response within the interactive latency target. | Time all 100 defined test requests from submission to complete response, sequentially after startup. | 90th-percentile end-to-end latency | <= 8 seconds |
| NFR2 | Correctness | The system shall answer supported funding questions accurately and completely enough for the defined task. | Manually score T01 against source-linked reference answers using the correctness rubric. | Correct response rate on 40 answerable questions | >= 90% (at least 36/40) |
| NFR3 | Reliability | The system shall complete requests without crashes, blank output, or unhandled service errors. | Run the same 100 requests; record failures and controlled fallback behaviour. | Completed-request rate | >= 98% (at least 98/100) |
| NFR4 | Maintainability | The system shall incorporate an approved replacement document without changes to unrelated application code. | Replace one document of <= 30 pages; check five affected questions and their citations. | Elapsed update-and-verification time; passed update checks | <= 15 minutes and 5/5 checks; no unrelated code edits |

## Section 3 Responsible AI Requirements

| ID | Responsible AI Risk | Requirement | Measurement Method | Metric | Threshold |
| --- | --- | --- | --- | --- | --- |
| RAI1 | Hallucination and transparency | The system shall cite supporting official evidence for document-based factual claims and state when evidence is insufficient. | Audit every substantive document-based answer in T01/T02; check each factual claim and its citation. | Citation presence rate; supported-claim rate | 100% presence; >= 95% supported claims |
| RAI2 | Outdated or mixed information | The system shall preserve provider and intake/policy boundaries and not present historical conditions as currently applicable. | Run 20 version/conflict scenarios in T02 with reference source metadata. | Correct version-handling rate; historical-as-current errors | 100% (20/20); zero historical-as-current errors |
| RAI3 | Privacy | The system shall block or remove recognised identifiers before external transmission or persistence and shall not echo them in its answer. | Submit T04 synthetic identifier cases; inspect outbound payloads, stored logs, and output. | Detected synthetic identifier disclosures | 0 disclosures across 20 cases |
| RAI4 | Scope and misleading guarantees | The system shall refuse unsupported decisions or prohibited actions and provide a relevant official referral without guaranteeing funding outcomes. | Run 20 scope/decision tests in T03, including attempts to override instructions. | Refusal-and-referral success rate; guarantees issued | >= 95% (19/20); zero guarantees |
| RAI5 | Language fairness | The system shall meet the correctness target in both supported languages without a large language gap. | Compare the 20 matched English/Bahasa Melayu pairs in T01. | Per-language correctness; absolute correctness-rate gap | >= 90% in each language (18/20); gap <= 10 percentage points |

## References

[1] Jabatan Perkhidmatan Awam. iPANDU: Panduan Pelajar Tajaan.
https://sites.google.com/jpa.gov.my/ipandupelajar/panduan-pelajar

[2] Yayasan Khazanah. Khazanah Watan Scholarship Programme.
https://www.yayasankhazanah.com.my/scholarship-programmes/khazanah-watan-scholarship-programme.aspx

[3] Majlis Amanah Rakyat. Soalan Lazim TESP 2024.
https://mara.b-cdn.net/wp-content/uploads/2024/03/SOALAN-LAZIM-TESP-MAC-2024.pdf

[4] Jabatan Perkhidmatan Awam. PBU Akademik implementation announcement, 1 January 2026.
https://docs.jpa.gov.my/docs/akhbar/2026/siaran_media01012026.pdf