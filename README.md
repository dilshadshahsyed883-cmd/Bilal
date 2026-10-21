# Bilal — Procurement & Sourcing AI (Android)

**Owner / maker: Bilal.** GitHub-first project source and releases: [ProcureMate Pakistan v0.1.1-beta](https://github.com/dilshadshahsyed883-cmd/Bilal/releases/tag/v0.1.1-beta).

## App
- [Android source code](apps/procuremate-android/)
- [Download current test APK from Releases](https://github.com/dilshadshahsyed883-cmd/Bilal/releases/tag/v0.1.1-beta)
- [Android build and release automation](.github/workflows/procuremate-android-release.yml)

The app includes OCR-driven image/scanned-PDF item extraction with table geometry, editable BOQ records, source page/row, low-confidence review, Pakistan supplier web-lead search (not verified businesses), RFQ drafts, CSV export and **Made by Bilal** branding. CI runs parser tests, builds and verifies the APK, and publishes the downloadable test package to GitHub Releases.

**Important:** v0.1.1-beta is an early working app and does not implement the entire MVP v1.1 scope. On-device testing and the nine-screenshot regression corpus remain open. The APK is debug-signed, not a Play Store release.

## Reference
- [MVP specification v1.1](docs/MVP_SPEC_V1_1.md)
- [Night session and issue history](docs/NIGHT_SESSION_2026-10-20_21.md)
- [Bilal Master Google Doc](https://docs.google.com/document/d/1Q5geNcCefCE4QBScqt6g11bCuwAB_wGPjP84gny1VR8/edit)

Do not commit private tender screenshots, supplier personal data, API keys, or signing credentials. Keep Bilal application work separate from VPS_1 and Haseeb.
