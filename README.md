# ScholarGuide
An AI information assistant helping Malaysian undergraduate students understand and compare selected scholarships and convertible education loans (pinjaman boleh ubah) using official documents.

**Course:** SAIA 3113 - AI Engineering  
**Repository name:** `ai-engineering-Scholarguide`  

## Problem Statement

Malaysian students should check on individual scholarship providers' websites, guidelines and FAQ for scholarships and convertible education loans for comparison. Information may relate to various intake years and it is important to differentiate applicable requirements and conditions. ScholarGuide will provide RAG explanations and comparisons of selected official information with citations but the decisions on whether or not to fund it will be made by the providers.

## Evidence of the Problem

- JPA states that iPANDU was developed partly because telephone and email enquiries exceeded departmental capacity, supporting the need for self-service information [1].
- Khazanah Watan scholarship information and MARA TESP convertible-loan information are published in separate sources; comparing them requires combining documents [2, 3].
- The TESP FAQ concerns the 2024 intake, while JPA's January 2026 announcement concerns PBU Akademik arrangements. These sources show why document years and purposes must remain explicit [3, 4].

This is preliminary documentary evidence; no student survey or evaluation results are claimed.

## Initial Related Work or Existing Approaches

1. **JPA iPANDU student guide** [1]: Provides guidance and resource links for JPA-sponsored students. **Limitation:** The reviewed content is provider-specific.
2. **Yayasan Khazanah Watan programme page** [2]: Publishes scholarship information and requirements. **Limitation:** Cross-provider comparisons require other sources.
3. **MARA TESP page and 2024 FAQ** [3, 5]: Provide programme information and common answers. **Limitation:** Dated conditions require intake-specific interpretation.

## Engineering Gap or Limitation

The project will explore the possibility of providing information in a small official collection in one interface and maintaining provider, programme and intake boundaries. It will cite, document metadata and indicate uncertainty of evidence if missing, historical, or conflicting. For now, a simpler alternative that is readily available is a keyword search, which will be used as a baseline to gauge the utility of AI explanations and comparisons.

## Project Objectives

- **O1:** To design a document-grounded scholarship and convertible-loan information assistant with provenance and responsible AI controls.
- **O2:** To develop a RAG prototype with cited explanations, comparisons, document-version handling, and appropriate uncertainty responses.
- **O3:** To evaluate correctness, citation support, latency, and handling of outdated or unsupported information against a keyword-search baseline.

## Target Users

-	Malaysian students in their undergraduate studies (including UTM students) who are intending or currently studying in Malaysia institutions who are seeking funding to study in Malaysia institutions.
-	Support staff at the university assisting students with information about official funding.

## Data Sources

Official public sources checked on **18 October 2026**:

1. **Khazanah Watan Scholarship Programme** [2] - undergraduate scholarship information.  
   https://www.yayasankhazanah.com.my/scholarship-programmes/khazanah-watan-scholarship-programme.aspx
2. **MARA TESP 2024 FAQ** [3] - historical intake and PBU information; not current intake guidance.  
   https://mara.b-cdn.net/wp-content/uploads/2024/03/SOALAN-LAZIM-TESP-MAC-2024.pdf
3. **JPA PBU Akademik announcement, 1 January 2026** [4] - policy context; not a complete intake guide.  
   https://docs.jpa.gov.my/docs/akhbar/2026/siaran_media01012026.pdf
4. **MARA diploma and degree funding page** [5] - TESP programme overview.  
   https://www.mara.gov.my/bm/pendidikan/pembiayaan-pelajaran/peringkat-diploma-ijazah/
5. **JPA iPANDU student guide** [1] - supporting guidance and official referral links.  
   https://sites.google.com/jpa.gov.my/ipandupelajar/panduan-pelajar


## Weekly Progress

| Week | Focus | Deliverable | Status |
| --- | --- | --- | --- |
| W1 | Project scope and GitHub setup | README and scope drafted; public sources checked | Completed |
