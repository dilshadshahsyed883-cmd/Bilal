# Bilal — Night Session Work Register (20–21 October 2026)

**Project:** Pakistan Government Procurement & Sourcing AI (Android)  
**Owner/maker:** Bilal  
**Master Doc:** https://docs.google.com/document/d/1Q5geNcCefCE4QBScqt6g11bCuwAB_wGPjP84gny1VR8/edit  
**Specification:** [MVP v1.1](./MVP_SPEC_V1_1.md)

## What was completed and recorded
- Collected and refined the Android product requirements into an MVP v1.1 specification. Owner accepted v1.1 as the provisional testing baseline, with future changes driven by hands-on testing.
- Defined bilingual English/Urdu procurement case intake, tender/BOQ screenshot/photo/PDF/CSV/XLSX import, editable line-item normalization, category filtering, source-based supplier discovery, quotations, RFQ drafts, comparisons and exports.
- Defined preferred sourcing cities: Lahore, Faisalabad, Gujranwala initially; search across Pakistan when warranted. Classify manufacturer, wholesaler, distributor, importer and retailer with source evidence and uncertainty.
- Defined seven launch category filters, Home Bedding and Hospital Textiles subgroups, dynamic categories, and mixed-category procurement support.
- Reviewed nine user-supplied screenshot variants as acceptance-test references, including overlapping crops and multi-page tables; raw screenshots are not in this repository.
- Documented three visible fixture groups: (A) District & Sessions Judge Multan FY 2026–27 stationery and general stores, two budget sections; (B) civil-judge/court mixed-lot goods; (C) maintenance/gardening/hardware/IT BOQ excerpt through 61 lines, with a document-specific 18% GST note.
- Defined screenshot deduplication, independent lot tracking, multiline/page-break reconstruction, quantity and packaging normalization (packs/dozens/bottles/liters/kg/feet), brand/equivalent wording, source/page traceability, ambiguous OCR review (e.g. "Electric Cattle", "-do-", "Cat 06"), and tender-specific tax handling.
- Owner reported screenshot uploads produced poorly structured data for understanding and supplier search; BIL-001 is the priority parsing/format defect.
- Owner requested visible maker/owner text "Bilal"; BIL-002 remains unverified in code/app metadata.
- Owner requested a rebuild and said they were ready to test; BIL-003 remains awaiting APK and installation evidence.

## Verified repository state before this sync
- On 2026-10-21 existing repository dilshadshahsyed883-cmd/Bilal had only README.md and .gitignore on main. Historical commit: 8ffc9a84c05270b3d705fcb57ee220ad0af67091 ("Initial commit").
- No Android source project, APK build workflow, verified build artifact, releases, or Android installation/smoke-test evidence was found in GitHub.
- This documentation update is not proof an Android APK was built or delivered.
- This repository is currently PUBLIC. Do not commit raw private tender screenshots, credentials, identifiable data, or confidential supplier files.

## Issue and release register
| ID | Status at documentation sync | Evidence to close |
|---|---|---|
| BIL-001 | OPEN | Screenshot import outputs deduplicated, lot-aware, properly formatted, searchable BOQ rows |
| BIL-002 | OPEN / NOT VERIFIED | Maker name "Bilal" visible in the app and relevant APK metadata |
| BIL-003 | APK DELIVERY NOT VERIFIED | Android source, reproducible CI APK, and install/smoke-test proof |
| BIL-004 | OPEN | Live supplier evidence search returns real source URLs/contacts, not made-up data |
| BIL-005 | OPEN | Nine reference screenshot variants run as regression fixtures |

## Work chronology
- 20–21 Oct 2026 — procurement requirements consolidated into v1.1; nine screenshot variants reviewed; OCR and supplier-search formatting issue recorded; "Bilal" branding requested; rebuild and hands-on test intent confirmed.
- 21 Oct 2026 — Master Doc created; retrospective GitHub and Master Doc history sync.

The complete detailed product and acceptance requirements are retained in MVP_SPEC_V1_1.md. No CI or deployment success is implied by this retrospective record.
