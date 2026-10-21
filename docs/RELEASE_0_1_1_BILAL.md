# ProcureMate v0.1.1-beta — Bilal GitHub release

Date: 2026-10-21

- Product: Pakistan Procurement & Sourcing Android app, developer credit **Bilal**.
- App package: pk.procuremate.app; versionCode 2; versionName 0.1.1-beta.
- Ported and isolated previously compiled Android source into this Bilal repository.
- Implementation: layout-aware Latin OCR for images/scanned PDFs; row, source page and uncertainty handling; edits for quantity/unit and supplier search; independent supplier leads not verified.
- GitHub Actions builds Android APK from the checked-in source and publishes `ProcureMate-Pakistan-v0.1.1-Bilal.apk` into release v0.1.1-beta.
- Verification: parser regression tests + Gradle assembleDebug + APK manifest version check run in CI. On-device installation/real tender acceptance tests remain pending.
- Existing incomplete features: advanced multi-lot/multi-page deduplication, 9 real-image regression corpus, XLSX and Urdu OCR, team synchronization, source-backed verified contacts.
- Source history: prior prototype on Haseeb feature branch. **Current canonical source is now Bilal**; unrelated Haseeb applications untouched.
