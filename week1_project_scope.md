# ScholarGuide Week 1 Project Scope

**Course:** SAIA 3113 - AI Engineering  
**Submission:** Individual semester project  

## Project Name

ScholarGuide - AI Scholarship and Convertible Education Loan Information Assistant

## Domain

Higher Education / Student Funding Information / Document-Grounded Conversational AI

## Problem Statement

Malaysian students who want to receive funding for their undergraduate studies should check out the websites, guidelines and FAQs of the different providers to learn about scholarships (biasiswa) and convertible education loans (pinjaman boleh ubah). When documents refer to different intakes or policy versions, it becomes more complicated to compare the published requirements, coverage, procedures and conversion condition. 

ScholarGuide will explain and compare information from selected official documents using retrieval-augmented generation (RAG) and accurate citations and identification of which year and programme the information relates to.The use of AI is suitable since students might ask questions in various ways or require explanations that integrate multiple documents.

## Evidence of the Problem

**Evidence 1:** JPA's student guide for iPANDU says that one of the reasons behind developing the self-service portal was due to the volume of telephone and email enquiries going over the department's capacity. This reinforces the demand for information that is easily accessible, but doesn't necessarily mean that this specific prototype is required.  
**Source / citation:** Jabatan Perkhidmatan Awam, *iPANDU: Panduan Pelajar Tajaan* [1].

**Evidence 2:** Funding information is published separately: Yayasan Khazanah publishes the information on the scholarships page of its website, and MARA's FAQ about TESP explains a convertible-loan programme. They have given their separate documents as the initial evidence that there is a need to consult multiple sources for the cross provider evidence.  
**Source / citation:** Yayasan Khazanah Watan programme page [2]; MARA TESP 2024 FAQ [3]; JPA PBU Akademik announcement dated 1 January 2026 [4].

## Initial Related Work or Existing Approaches

### Study or Solution 1 JPA iPANDU Student Guide

**Approach:** Provides JPA-sponsored student guidance and links to supporting resources.  
**Source / citation:** JPA iPANDU [1].  
**Key limitation:** The reviewed content is JPA-specific; comparing it with other providers requires additional sources.

### Study or Solution 2 Yayasan Khazanah Watan Programme Page

**Approach:** Publishes structured scholarship information and requirements.  
**Source / citation:** Yayasan Khazanah [2].  
**Key limitation:** The reviewed page describes one programme rather than providing cross-provider explanations.

### Study or Solution 3 MARA TESP Information Page and FAQ

**Approach:** Provides programme information and answers to common questions.  
**Source / citation:** MARA TESP 2024 FAQ [3] and diploma/degree funding page [5].  
**Key limitation:** The dated FAQ must be interpreted within its intake, and comparisons require other documents.

## Engineering Gap or Limitation

Students must manually combine provider-specific information to answer comparison questions. The proposed gap is a single interface that retrieves and explains evidence across a small approved collection while keeping providers, programmes, intake years and policy versions separate. ScholarGuide will address this through citations, metadata-aware retrieval and explicit uncertainty when information is missing or conflicting.

## Initial Project Objectives

- **O1:** To design a document-grounded scholarship and convertible-loan information assistant with source provenance and responsible AI controls.
- **O2:** To create a RAG prototype that clarifies and contrasts published information, provides evidence, identifies document versions and provides a suitable response to unsupported questions.
- **O3:** To measure the accuracy of the answer, citation, response time and handling of information that is out of date or not supported by a search on the keyword.

## Target Users

Malaysian prospective and current undergraduate students seeking funding information for study at Malaysian institutionsor university student-support staff helping students locate official funding information.

## Data Sources

1. **Khazanah Watan Scholarship Programme - Yayasan Khazanah** [2]. Web document for undergraduate scholarship information.  
   **URL:** https://www.yayasankhazanah.com.my/scholarship-programmes/khazanah-watan-scholarship-programme.aspx
2. **Soalan Lazim TESP 2024 - MARA**, updated 15 March 2024 [3]. PDF for historical intake information and PBU explanations. Its conditions and dates must not be presented as current intake guidance.  
   **URL:** https://mara.b-cdn.net/wp-content/uploads/2024/03/SOALAN-LAZIM-TESP-MAC-2024.pdf
3. **PBU Akademik implementation announcement - JPA**, 1 January 2026 [4]. PDF for policy and version context; it is not a complete new-applicant guide.  
   **URL:** https://docs.jpa.gov.my/docs/akhbar/2026/siaran_media01012026.pdf
4. **Peringkat Diploma dan Ijazah - MARA**, TESP section [5]. Web document for the programme overview; intake-specific conditions require separate verification.  
   **URL:** https://www.mara.gov.my/bm/pendidikan/pembiayaan-pelajaran/peringkat-diploma-ijazah/
5. **iPANDU: Panduan Pelajar Tajaan - JPA** [1]. Web document for relevant guidance and official referral links.  
   **URL:** https://sites.google.com/jpa.gov.my/ipandupelajar/panduan-pelajar


## Similar to EduAdvisor

The systems both use official documents to answer questions in a specific domain of education. Both need to be retrieved, cited, controlled for hallucination, assessed and continually maintained in the documents.

## Different from EduAdvisor

EduAdvisor clarifies courses, requirements and graduation. ScholarGuide provides information on scholarships and convertible education loans that covers the published terms of the awards and variations in the options presented. ScholarGuide is a place of distinction for providers, intake years, and conversion-policy versions and it does not make funding decisions or guarantees approval or conversion.

## Responsible AI Risks

1. **Hallucination or mixed requirements:**  Answer could be an invented condition or a requirement attributed to the wrong programme. **Control:** Retrieve approved sources, label the programme and year, cite factual claims, and abstain when evidence is insufficient.
2. **Outdated information:** Historical deadlines or conversion terms could be presented as current. **Control:** Track versions, label historical material, and verify current-intake claims.
3. **Misleading certainty:** Users may assume that the explanation given means that they are certain of eligibility, approval or automatic conversion. **Control:** Explain public conditions without making binding decisions or personalised borrowing recommendations.
