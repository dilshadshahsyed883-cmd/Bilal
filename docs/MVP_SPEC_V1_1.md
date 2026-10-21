# Pakistan B2B Procurement & Sourcing AI — Android MVP Specification

**Version:** 1.1 | **Date:** 2026-10-21 | **Status:** Approved scope candidate / specification, not an implemented APK

## 1. Product mission

A bilingual English/Urdu Android APK for a Pakistani supplier responding to government and private procurement inquiries. The app ingests tenders/BOQs (primary), PDF documents, spreadsheets, screenshots and photos, extracts precise product requirements, finds potential B2B suppliers in Pakistan, preserves verifiable evidence for every claimed contact and company type, prepares user-approved WhatsApp/email RFQ drafts, and compares actual supplier quotations for purchasing decisions. No auto-messaging or PPRA bid submission in MVP.

## 2. Confirmed business settings

- Registration and procurement enrollment are owner-managed; specific credentials or business records are not stored in this public repository.
- Customers: federal and provincial agencies, private firms and institutions.
- Typical purchase units: wholesale 20–500, but tender value/quantities vary.
- Delivery coverage: all Pakistan.
- Supplier types: manufacturers, wholesalers, distributors, importers and online stores (clearly classified, with evidence and uncertainty).
- Supplier-search priority: Lahore, Faisalabad, Gujranwala; widen to rest of Pakistan when quality/compliance/price warrant.
- Ranking: balanced; specification compliance is a hard gate, then compare landed cost, supplier reliability, delivery capability, MOQ and payment terms.
- Languages: English and Urdu; optionally Roman Urdu in text interface.
- Team: 2–5 users sharing a private workspace.
- Research cost preference: minimal. Free OCR/local catalog where feasible; paid search/AI backend configurable and usage-capped. An API connection may be required for reliable unattended supplier research.
- Messaging: generate/edit RFQ drafts only; user chooses whether to send.

## 3. Category catalog

### Launch filters (selected in most recent requirements)
1. Household & Kitchen
2. Cleaning & Janitorial
3. Stationery & Paper
4. Electrical & Lighting
5. Textiles & Uniforms
6. Bedding & Mattresses
7. Packaging & Plastic

### Dedicated textile subdivisions (prior requirement retained)
8. Home Bedding & Home Textiles: sheets, blankets, pillowcases, mattress protectors, curtains, towels, quilts, duvets.
9. Hospital Bedding & Hospital Textiles: hospital sheets, blankets, gowns, linen, drapes, waterproof covers and institutional textiles.

### Available but initially inactive filters
Office Furniture, Hardware & Tools, Plumbing & Sanitary, Computers & IT, Printing & Toners, Food & Refreshments, Sports & Recreation, Lab & Medical Supplies, Industrial Machinery; more categories can be added by an authorized team member.

Users can select **multiple** categories in a single case. Classification is editable and every custom category is reusable.

## 4. Primary workflow

1. Create a procurement inquiry/case; optionally set buyer, tender reference, delivery address, closing date and desired margin.
2. Upload tender PDF, BOQ (.xlsx, .csv), screenshot/photo or typed item list; support multi-file, multi-item input and Android Share intent where viable.
3. Extract each line item with name, quantity, unit, measurements, fabric composition, GSM/thread count, dimensions, grade, branding/equivalence language, documentation, samples, warranty, packing, delivery terms. Show source page/row and confidence; require correction for uncertain fields. Distinguish tender requirements from general notes.
4. Normalize item names and search phrases in English, Urdu and local market synonyms. Never silently substitute a non-compliant product.
5. Discover suppliers from public authorized sources and supplier websites. Search three priority cities first; expand if not enough compliant candidates exist.
6. Create individual evidence records: original URL, website/business name, classification basis, public phone/email/WhatsApp, address, extraction date, confidence and verification state.
7. Present supplier shortlist. Status labels: Discovered / Source-cross-checked / Contact confirmed / Quotation received / Unverified. Absence of evidence must not be represented as verification.
8. Prepare editable bilingual RFQ draft including item specs, quantity, quotation validity, tax, lead time, freight to buyer site, payment, warranty and requested supporting documents. Provide Copy, WhatsApp Share, Email Draft actions only; never silently send.
9. User captures received offers, quote PDF/screenshots and structured unit pricing. Compare **actual quoted landed costs** on a common tax/delivery basis; separately show estimated and historical prices if available.
10. Export supplier comparison and item schedule as CSV/Excel/PDF; archive case status and supplier history.

## 5. Main screens

- Dashboard: open cases, pending responses, nearest deadlines, recent items.
- New Inquiry: import files and define tender context.
- Parsed BOQ: editable item-by-item table with source and uncertain fields.
- Categories: multi-select chips, home/hospital textile specialty specs, custom categories.
- Supplier Discovery: city filters, supplier type, evidence links, contact confidence and duplicates.
- RFQ Drafts: bilingual messages, edit/share/copy, draft history.
- Quotations: taxes, freight, packing, risk, margin, delivery comparison.
- Supplier Directory: reviewed profiles and source history.
- Team/Settings: owner and staff login, budget caps, optional AI/search provider connection.

## 6. Price and decision logic

- Never rank a non-compliant item above a compliant alternative simply because it is cheaper.
- Landed cost: quoted quantity × unit price + applicable taxes + freight + packing + other clearly identified transaction costs; normalize tax-included vs tax-exclusive bids.
- Suggested selling quote and estimated gross margin are calculated from transparent, user-editable assumptions; do not present unconfirmed taxes as settled facts.
- Default balanced ranking weights among specification-compliant suppliers: 35% normalized landed price, 25% source/fulfillment reliability, 20% delivery speed/capability, 10% MOQ/payment fit, 10% location/logistics flexibility. Weights configurable, missing data marked unknown; no fabricated scores.
- Label *best verified quoted deal* only when enough comparable supplier quotations exist. Otherwise *promising sourcing candidate*.

## 7. Research and verification constraints

- Public supplier directories and official trade/chamber sources are evidence pointers, not automatic manufacturer proofs.
- Collect only publicly available business contacts from sources that permit access; no invented emails, phones, prices or WhatsApp accounts.
- Source URL and last-seen date are mandatory for automatically discovered contacts.
- Categorize source confidence and contact verification separately.
- Avoid prohibited scraping and CAPTCHA bypass; prefer authorized search APIs and user-supplied reference URLs.
- Any paid API usage must be configurable with rate/budget caps and safe key storage on server, never hard-coded in APK.
- Federal PPRA 2026 rules and Punjab PPRA requirements differ; display original document references and ask user to confirm tender-specific conditions. No claim that automatic checks replace professional review.

## 8. Proposed implementation architecture

- **Android UI:** Flutter/Dart. Bilingual form and data-rich tables; Android Share and file picker.
- **On-device extraction:** ML Kit Latin OCR for eligible photos/screenshots; local PDF text and spreadsheet parsers where possible. Urdu scripts and complex scans may require a cloud OCR service or human correction.
- **AI extraction:** structured output model behind a small, authenticated HTTP API, with strict schema validation and source line/page references; configurable provider and cost cap.
- **Search and research:** backend supplier search service supporting authorized search providers and user-fed links; query variants; deduplication; evidence extraction and source traceability.
- **Team cloud data:** managed Postgres/Auth/Storage (Supabase free tier as prototype option, with inactivity/quota/backup limitations), private per-organization access policies. Never expose service-role secrets in the client.
- **Local cache:** device storage for offline draft viewing; synchronize via authenticated backend when online.
- **Release:** private, independent GitHub repository; GitHub Actions with Flutter test/analyze/build APK, artifact download; signed release key stored in CI secrets. No changes to existing VPS_1 or unrelated desktop application repos.

## 9. Scope split

### First working vertical slice / MVP v0.1
- Android login for private team workspace.
- Upload one tender PDF or image/BOQ, split into multiple editable line items.
- Multi-select category tags and dedicated home/hospital bedding spec fields.
- Run source-backed supplier search in Lahore, Faisalabad, Gujranwala with widening as needed.
- Show original links, found business contact evidence, type/verification states.
- Produce editable bilingual WhatsApp/email RFQ and CSV export.
- Save inquiries and supplier profiles for reuse.

### Subsequent iterations
- Automated PPRA tender discovery/watch, tender alerts, archival award-price intelligence.
- Comprehensive quotation profitability and procurement bid pack.
- Supplier reply/offer inbox integration (only with explicit authorization), quote attachment parsing.
- Offline processing enhancements; optional additional category templates; advanced market insights and negotiated deals.

### Not in MVP
- Automated WhatsApp messaging or bulk cold outreach.
- Automatic government bid submission or CAPTCHA bypass.
- Claims of official business/manufacturer verification without evidence.
- Unlimited free automated commercial search, guaranteed lowest real-world price or full Urdu handwriting OCR.

## 10. Data objects

Organization, UserRole, Category, TenderCase, TenderSourceFile, BOQLineItem, ProductSpec, Supplier, SupplierSourceEvidence, SupplierItemMatch, RFQDraft, SupplierQuote, QuotationLine, ExportDocument, CaseActivityLog, ResearchUsageBudget.

## 11. Acceptance tests and release gates

1. Import a real ten-line tender/BOQ with source page/row references; each identified line remains editable and original attachment is preserved.
2. Create one inquiry containing at least three categories including either Home Bedding or Hospital Textiles.
3. Supplier results never show a phone/email without its source; results correctly label unverifiable cases and duplicates.
4. No synthetic actual prices, manufacturer claims or fake verification statuses.
5. Generate English and Urdu editable RFQ for the same item; user action required to send/share.
6. Tax/freight/quantity normalized in comparison; missing quotations do not appear as cheapest offers.
7. Two staff accounts access only their organization's authorized cases; owner can manage team access.
8. GitHub CI passes static analysis, unit tests and a reproducible Android APK build; APK is installed and basic upload → research → draft journey is smoke-tested on Android before being called delivered.
9. App remains clear and honest during network/API failures and partial supplier search results.
10. API usage can be capped and logged; supplier search can fall back to user-provided evidence rather than fabricating results.

## 12. First practical development sequence

1. Provision a separate private GitHub repository and Android CI build (do not reuse VPS_1 production code).
2. Implement Android case intake, categories, BOQ item-table editor, local data model and team identity.
3. Implement actual text extraction from common PDFs/Excel files and OCR fallback for screenshots; attach source references.
4. Connect one legitimate live supplier search provider with evidence extraction and three-city preferences, handle zero-results honestly.
5. Add RFQ draft composer, comparison table, export, persistence and regression tests.
6. Build/smoke-test the first signed or development APK with real redacted procurement examples, then release a downloadable APK artifact.

**Needed practical input for tuning:** one or two genuine tender/BOQ examples (commercially sensitive details can be redacted) and several previously difficult product inquiries. No user request to perform account provisioning or change any existing production repositories is implied by this specification.

## 13. Real procurement reference images received — 2026-10-21 (acceptance test corpus)

Nine images/screenshot variants supplied by the owner, including overlapping cropped and browser-frame copies of the same pages. **Do not count duplicate screenshots as separate tenders or duplicate BOQ lines.** These are **partial screenshots**, not complete original tender files. Original document ID, full page sequence, procurement deadlines and bid conditions must remain unknown unless supplied or verified.

### Distinct visible reference groups (do not merge across documents)

**A. District & Sessions Judge Multan — FY 2026–27 office stationery and general stores:** visible section heading `A03901-Office Stationary` (estimated budget PKR 4,000,000), another section `A03970-001-Others` (estimated budget PKR 1,000,000). Some examples: white paper ream, legal size 70 gsm, 500 sheets, 3,000 reams; shorthand notebook, 200 leaf, 200 Nos; blue and black ballpoint pens, 500 packets each; large tissue box, 500 boxes, minimum 200 sheets; dustbin large, 05 dozen; Dettol/equivalent 500 ml, 05 dozen; phenyl 60 bottles; insecticide spray; brooms/wipers; wall clock, 2 dozen; wireless remote bells, 3 dozen. This proves that a *single tender* can mix multiple procurement categories while maintaining separate budgets/sections and packaging units.

**B. Civil-judge/court general-stores list:** pictured excerpts show ballpoint red, scales, several envelope sizes specified by 50 envelopes per packet, tape, glue, highlighter, pens, and a separate Lot #2 including back-care supports, electric kettle (source text appears `Electric Cattle` and must be flagged rather than silently corrected), tissues, air freshener, insecticide spray, handwash, liquid toilet cleaner, crockery sets, network hubs and Cat6 cables. `Brand / Equivalent` wording appears repeatedly. Some product descriptions wrap across a page break, so the parser must join them without accidentally moving a quantity into the wrong row. The actual tender/court reference and year are not established by these cropped images.

**C. Maintenance, consumables, gardening, hardware and IT BOQ:** visible rows 18–61 include air freshener, rose water (1,000 liters), electric spray machine (10 Nos), protective footwear (25 pairs), acid-based floor cleaner (700 liters), garden pipe 1-inch (3,000 feet), locks (1,500 each), industrial pipe wrenches, PPR heater 1,500 watts (2 Nos), lime (9,500 kg), large brushes (500 each), concrete flower pots (100 each), 16-foot telescopic aluminium ladders (5 each), Canon Pixma G1010 colour printer (5 each) and HP LaserJet 108A monochrome printer (6 each). The visible table ends with an instruction to add `18% G.S.T.`; store this as a **document-specific input** requiring confirmation, never as a universal tax rule. Source identity and adjacent missing rows remain unknown.

### Extraction/output behavior required by these samples

1. **Page and screenshot deduplication:** combine overlapping screenshots of same tender/page, preserving source references, and avoid inflated quantities.
2. **Separate procurement lots and budgets:** retain original lot name, item serial, tender identifier (if found), estimated budget and buyer, and keep conflicting/noisy source references reviewable.
3. **Line wrapping and page breaks:** correctly attach continuation text to the appropriate item, with a pending-review flag for ambiguous rows.
4. **Packaging and unit conversion:** preserve raw quantity `05 Dozen`, `60 Bottle`, `500 Packet`, `1000 Packet (50 per pkt)`, `3000 P-ft`, `9500 P-Kg`, `05 Box`, etc.; calculate normalized counts **only when pack size and meaning are confirmed**. Example: `05 dozen` = 60 individual units, but one `packet` need not be a single pen.
5. **Brand-equivalent logic:** `Mortein/Equivalent`, `Uni Ball/Equivalent`, `Dettol/Equivalent`, etc., must remain searchable with both branded and genuine spec-compliant substitutes. The user confirms acceptability; do not silently downgrade brands or technical specifications.
6. **Ambiguities to flag rather than fabricate:** OCR `Electric Cattle` likely means kettle but needs review; `-do-` in quantity column refers to preceding row but must be confirmed when the source is unclear; `Cat 06 Cables` likely Cat6; broken/missing units and item names must remain uncertain.
7. **Government quotation math:** recognize blank rate/amount columns as fields awaiting supplier quotations, not zero pricing. Apply document-specific taxes separately and preserve the raw quoted rate, estimated quantity and extension totals.
8. **Category breadth:** even if primary filters are the user's seven preferred groups, surfaced tenders include hardware, gardening, crockery, computer accessories/printers, sanitary supplies and pest-control items. **Dynamic categories** must be available; the parser must not drop items outside configured launch filters.
9. **Solicitation-specific caveats:** retain `quantity may be increased/decreased`, buyer location, brand-or-equivalent conditions, sample/warranty requirements (if visible), and bid deadlines when original PDF contains them.
10. **Testable handoff:** Owner can inspect and edit an extracted BOQ preview, select any line, find potential suppliers by city, draft vendor RFQ, save price/lead-time/MOQ quotations and export a properly grouped response.

### Mandatory realistic test scenarios

- **Mixed-lot tender:** Given the Multan screenshots, report two visible budget groups rather than merging, parse sample rows, correctly distinguish number of boxes/packets/dozens and show budget as metadata rather than inferred available purchase money per item.
- **Noisy scanned pages:** Given the civil-judge screenshots, preserve uncertain OCR spans, page-break continuations, pack specifications and brand/equivalent references; require corrections before launching a supplier search with uncertain critical specs.
- **Unit-heavy maintenance BOQ:** Given the 61-line excerpt, preserve litre/foot/kilogram/pair/each, surface its 18% GST instruction as document-specific, and allow reviewing extensions where quantity and unit price are entered.
- **Supplier evidence:** Live suppliers and contact numbers are **not present** in these screenshots. Supplier contacts and prices must be collected by subsequent authorized, source-attributed live search or actual quotation; never generated from these images.