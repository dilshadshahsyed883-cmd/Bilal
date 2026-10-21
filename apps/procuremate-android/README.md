# ProcureMate Pakistan (Android) — Bilal

**Current build:** v0.1.1-beta · **Owner / maker:** Bilal · **Package:** `pk.procuremate.app`

This is the independent Android source of the Pakistan Procurement & Sourcing Assistant. The app is built and published through the **Bilal** GitHub repository; do not build this project in Haseeb or VPS_1.

## Tested implementation
- Android Java app with Google ML Kit Latin text recognition for images and scanned PDF.
- Geometry-aware table/BOQ row reconstruction, separated item, quantity, unit, original page/row source, manual review warnings.
- Local item/supplier records; browser supplier searches and optional Serper-sourced leads in Lahore/Faisalabad/Gujranwala (unverified leads; no invented contacts).
- Editable product/quantity/unit/specification; sample tender items, CSV export, English/Urdu RFQ drafting.
- Visible app credit **Made by Bilal**, About > Owner / Developer: Bilal.
- Pure-Java table parser regression tests plus GitHub Actions Android APK build and package verification.

## Install
Get the **APK directly** from [the v0.1.1-beta GitHub Release](https://github.com/dilshadshahsyed883-cmd/Bilal/releases/tag/v0.1.1-beta), or download a GitHub Actions artifact if a release is unavailable. APK is **debug-signed for testing**. A different Android signing key may require uninstalling a previous beta; export existing local records before uninstalling.

## Scope and limitations
This is a testable beta, **not** completion of the full [MVP v1.1 specification](../../docs/MVP_SPEC_V1_1.md). Image/PDF OCR still requires user review. XLSX/Urdu OCR, full multipage/lot-aware tender segmentation, verified supplier identities, quotation comparisons, cloud workspace, and tests against the full nine-image reference corpus are pending. No automated messaging or bid submission. Never add private tenders, supplier contacts, API keys, or signing keys to this public repository.

## Local build
Requires JDK 17, Android SDK platform/build-tools 35, Gradle 8.10.2+:
```sh
cd apps/procuremate-android
gradle :app:assembleDebug
```
Release CI recompiles app and verifies `pk.procuremate.app` and `0.1.1-beta`, runs parser regression tests, then publishes the APK as a versioned GitHub Release asset. 
