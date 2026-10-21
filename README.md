# Bilal — Procurement & Sourcing AI (Android)

Bilal's independent Pakistan Government Procurement & Sourcing AI project. Target: a bilingual Android app to turn tender/BOQ documents into structured, editable, supplier-search-ready records; discover legitimate Pakistan B2B suppliers; and compose owner-reviewed RFQs and quote comparisons.

**Owner/maker:** Bilal (display requirement; not yet verified in a running APK).  
**Testing baseline:** MVP v1.1 (provisional).  
**Status on 21 Oct 2026:** Specification and test scenarios documented; Android source and verified built APK are not yet present here.

## Project records
- [Detailed product requirements: MVP v1.1](docs/MVP_SPEC_V1_1.md)
- [20–21 Oct night work, decisions and outstanding issues](docs/NIGHT_SESSION_2026-10-20_21.md)
- [Bilal Master Google Doc](https://docs.google.com/document/d/1Q5geNcCefCE4QBScqt6g11bCuwAB_wGPjP84gny1VR8/edit)

## Requirements at a glance
- Tender PDF, screenshot, photo, CSV and Excel input; duplicate screenshot detection; independent lots; multi-page table reconstruction; editable BOQ lines and units.
- Preserve source page, quantities and units, brands/equivalents, uncertainty and document-specific GST/other conditions.
- Search real suppliers starting with Lahore, Faisalabad and Gujranwala; widen to Pakistan when needed; no fictitious business contacts or quotations.
- Bilingual human-approved RFQ drafts, actual landed-cost comparison and exports.
- Seven priority categories plus home and hospital textile specializations and dynamic mixed-category items.
- Private team workspace target (2–5 users); no unauthorized auto-messaging or government bid submission.

## Build proof still needed
Android source, CI analysis/tests, reproducible APK build and installation/smoke-test evidence are required before claiming the APK is delivered. VPS_1 and Haseeb projects remain separate. Because this GitHub repo is public, keep private tenders, contacts, API credentials and signing keys out of commits.
