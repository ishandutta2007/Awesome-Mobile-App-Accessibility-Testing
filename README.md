# Awesome-Mobile-App-Accessibility-Testing

# Awesome Mobile App Accessibility Testing

> A curated list of top Mobile App Accessibility Testing platforms — both SaaS/Hosted commercial solutions and open-source alternatives for detecting WCAG violations, screen reader issues, and inclusive design gaps in native iOS and Android applications.
> 🌟 Star this repo if you find it useful! 🌟

---

## 📋 Table of Contents

- [SaaS / Hosted Platforms](#-saas--hosted-platforms)
  - [BrowserStack App Accessibility Testing](#browserstack-app-accessibility-testing)
  - [Evinced Mobile](#evinced-mobile)
  - [Deque axe DevTools Mobile](#deque-axe-devtools-mobile)
  - [Level Access Mobile](#level-access-mobile)
  - [Siteimprove Mobile Accessibility Testing](#siteimprove-mobile-accessibility-testing)
  - [AudioEye Mobile Audit](#audioeye-mobile-audit)
- [Open-Source Software](#-open-source-software)
  - [AccessDroid](#accessdroid)
  - [GTXiLib](#gtxilib)
  - [A11yArgus](#a11yargus)
  - [Android Accessibility Scanner](#android-accessibility-scanner)

---

## 🟦 SaaS / Hosted Platforms

Commercial, cloud-hosted Mobile App Accessibility Testing platforms. These are not open-source but are included as reference points for feature comparison.

### BrowserStack App Accessibility Testing
**Type:** Real-device accessibility scanning with screen reader support
BrowserStack provides app accessibility testing on real iOS and Android devices, with a proprietary rule engine covering **WCAG 2.1 and 2.2** across all conformance levels [citation:2]. Key capabilities include an **App Workflow Scanner** for navigating apps and scanning selected screens, one-click access to **TalkBack (Android) and VoiceOver (iOS)** with screenshot and recording capture, and support for native, hybrid, and cross-platform apps including React Native and Flutter [citation:2]. It offers zero setup—just upload your app—and supports local testing for apps behind firewalls, geolocation testing, and accessibility settings adjustments like text size and dark mode [citation:2]. AI-powered agents under the Ultimate plan add contextual issue detection and remediation suggestions [citation:14]. **Best for:** Teams wanting real-device accessibility scanning with integrated screen reader testing and WCAG 2.2 coverage without local setup.

### Evinced Mobile
**Type:** No-SDK mobile accessibility flow analysis
Evinced's Mobile Flow Analyzer requires **no SDK installation and no code-level access** to the tested app—if you can run it, you can test it [citation:3]. It works across Swift, Android, React, and other frameworks with a single set of reports and terminology across platforms, includes **webview support** (which traditional solutions often miss), and delivers annotated screenshots with fix guidance and links to relevant WCAG criteria [citation:3]. Mobile-specific checks include platform-specific fix recommendations for SwiftUI, Android (XML, Kotlin, Java), and React Native, with exportable HTML and JSON results [citation:3]. SDKs are also available for Appium, Espresso/UIAutomator, XCUI, and WebdriverIO [citation:15]. **Best for:** QA teams wanting accessibility testing without code access or SDK integration, particularly for cross-platform apps with webviews.

### Deque axe DevTools Mobile
**Type:** Automated accessibility scanning within Appium workflows
Deque's axe DevTools for Mobile integrates directly into existing Appium test workflows for Android and iOS, with dedicated drivers (AxeUiAutomator2, AxeXCUITest) that run accessibility scans as part of automation [citation:8]. It can be integrated into cloud platforms like Sauce Labs and Perfecto, or run on Deque's own device cloud [citation:4]. Results flow to the axe Developer Hub or Mobile Dashboard, with support for both instant scans and consolidated reports across test suites [citation:15]. **Best for:** Teams already running Appium automation wanting to add accessibility scanning without changing their test workflow.

### Level Access Mobile
**Type:** Access Engine rules with native-first mobile engine
Level Access provides mobile accessibility testing through **Live App Testing and Mobile SDKs** (using Access Engine rules) or **On-device testing via Level Access Desktop** (using Mobile Engine rules) [citation:5]. The Mobile Engine is a native-first testing engine with a comprehensive recommendation library supporting **Android, Jetpack Compose, iOS, SwiftUI, Flutter, React Native, .NET MAUI, and Xamarin** [citation:5]. Checks cover missing labels and content descriptions, touch target sizing (24×24 and 44×44 points), contrast, dynamic type support, traversal order, orientation restrictions, and more [citation:5]. **Best for:** Enterprises needing deep native-framework coverage with framework-specific fix recommendations.

### Siteimprove Mobile Accessibility Testing
**Type:** On-device Android testing app with accessibility overlay
Siteimprove provides a **lightweight Android app** that uses Android's Accessibility Services to inspect UI elements and detect issues in real time, without requiring source code or emulator access [citation:7]. Users install the app, log in, grant accessibility permissions, and capture screens during user flows to generate actionable reports [citation:7]. It requires **Android 8 (Oreo) and above**, runs checks only when initiated by the user, and does not record or transmit screen content automatically [citation:7]. **Best for:** Android teams wanting in-context accessibility testing on real devices without build configuration or emulator setup.

### AudioEye Mobile Audit
**Type:** Expert-led mobile accessibility auditing service
AudioEye's Mobile Audit combines **automated scans with human testing** by certified accessibility experts and members of AudioEye's A11iance team (assistive technology users) [citation:10]. The process follows three steps: pre-audit questionnaire, comprehensive testing against accessibility standards and business goals, and a detailed report with recommended fixes for developers [citation:10]. **Best for:** Organizations wanting human-validated audit reports rather than automated-only scanning, particularly for complex or high-stakes apps.

---

## 🟩 Open-Source Software

Self-hosted, community-driven Mobile App Accessibility Testing tools. The open-source ecosystem spans **Android semantics tree analyzers**, **iOS XCTest accessibility frameworks**, **hybrid UI tree + OCR analysis tools**, and **Google's official Android scanner**.

### AccessDroid
**Stack:** Python / Android / Semantics Trees | **License:** Open Source (Zenodo)
AccessDroid is a lightweight dynamic analysis tool that detects **screen reader accessibility issues in Android apps** via semantics trees [citation:11]. Key characteristics:
- **Semantics-aware detection**: Analyzes the accessibility semantics tree rather than just the raw UI tree, enabling detection of issues that other tools miss 
- **Three issue categories**: semantics separation, semantics downshift, and semantics omission 
- **High precision**: Achieves **98.8% precision and 98.3% recall** on the PoseCheck benchmark (361 pages from 50 real-world apps), with **15ms average detection time per page** 
- **Visual annotation**: Highlights detected semantics nodes with red bounding boxes on the device screen 
- **Exportable reports**: UI tree, semantics tree, and issue reports exported as plain text 

It outperforms Android Accessibility Scanner, detecting **12.2% higher recall** on content description omission issues [citation:13]. **Trade-off:** Android-only, and requires ADB setup.
**Best for:** Android developers and researchers wanting deep semantics-tree analysis for screen reader accessibility, accepting the ADB-based workflow.

### GTXiLib
**Stack:** Objective-C / Swift (CocoaPods) | **License:** Apache-2.0 (Google)
GTXiLib (Google Toolbox for Accessibility for iOS) is an **iOS accessibility testing framework** that integrates with XCTest and can be used with any XCTest-based framework such as EarlGrey [citation:12]. Key characteristics:
- **Zero-code-change integration**: Install GTX checks in your test class's `+setUp` method, and existing test cases double as accessibility tests 
- **Built-in checks**: `checkForAXLabelPresent`, `checkForAXTraitDontConflict`, and a collection of `allGTXChecks()` 
- **Custom checks**: Write your own `GTXCheckBlock` for project-specific rules (e.g., ensuring accessibility labels do not end with `.png`) 
- **Test failure on violation**: GTX runs checks before test tearDown and fails the test if any accessibility check fails 

Installation via CocoaPods with `use_modular_headers!` (not `use_frameworks!`) [citation:12]. **Trade-off:** iOS-only, and checks are limited to what you register.
**Best for:** iOS teams already using XCTest wanting to add accessibility checks to existing tests with minimal code changes, accepting the framework's built-in check limitations.

### A11yArgus
**Stack:** Python / DroidBot / UI Automator / OCR | **License:** Research prototype (ACM)
A11yArgus is a research prototype that combines **UI hierarchy extraction, geometric reasoning, and OCR** to detect **13 accessibility issue types**, including six novel ones not covered by existing tools (overlapping components, missing accessible names, gesture-only navigation, error message detection) [citation:1]. Key characteristics:
- **WCAG 2.1/2.2 mapping**: All findings mapped to success criteria across all POUR principles (Perceivable, Operable, Understandable, Robust) 
- **Hybrid approach**: Structural UI tree inspection + layout geometry analysis + OCR-based validation 
- **High accuracy**: **91.9% precision, 97.8% recall, F1-score of 94.8%** on 200 Android apps 
- **Key findings**: Text resizing and touch target issues affect the widest range of apps; most issues fall under WCAG Level AA 

**Important:** This is a research tool, not a production-ready product—it requires setup of DroidBot and UI Automator, and is Android-only [citation:1]. **Best for:** Researchers and advanced teams wanting state-of-the-art detection of novel accessibility issue categories on Android, accepting research-prototype maturity.

### Android Accessibility Scanner
**Stack:** Android App (Google) | **License:** Free (Google)
Android Accessibility Scanner is Google's official on-device accessibility testing tool, available on the Play Store. It provides suggestions to improve app accessibility by scanning the screen and identifying issues like small touch targets, low contrast, and missing content descriptions. It is widely used as a baseline in academic comparisons [citation:13] and remains the most accessible starting point for Android accessibility testing.
**Trade-off:** It requires manual navigation (does not auto-traverse apps), and its detection depth is less than research tools like AccessDroid on semantics-specific issues [citation:13].
**Best for:** Android developers wanting a free, no-setup starting point for accessibility testing directly on their device.

---

## 📊 Comparison at a Glance

| Software | License | Stack | Platform | Screen Reader Analysis | WCAG Coverage | Self-Hosted | Best For |
|----------|---------|-------|----------|------------------------|---------------|-------------|----------|
| **BrowserStack** | Proprietary | Cloud | iOS + Android | ✅ TalkBack/VoiceOver | ✅ 2.1/2.2 | ❌ | Real-device + screen readers |
| **Evinced** | Proprietary | Cloud | iOS + Android | (Check) | ✅ | ❌ | No-SDK flow analysis |
| **Deque axe Mobile** | Proprietary | Appium drivers | iOS + Android | ❌ | ✅ | ❌ | Appium workflow integration |
| **Level Access** | Proprietary | Cloud/On-device | iOS + Android | ❌ | ✅ | (Desktop) | Native-framework depth |
| **Siteimprove** | Proprietary | Android App | Android | ❌ | ✅ | ❌ | On-device overlay testing |
| **AccessDroid** | Open Source | Python/ADB | Android | ✅ Semantics tree | ✅ Mapped | ✅ | Deep semantics analysis |
| **GTXiLib** | Apache-2.0 | iOS/XCTest | iOS | ❌ (Label checks) | ✅ Checks | ✅ | XCTest accessibility checks |
| **A11yArgus** | Research | Python/OCR | Android | (Check) | ✅ 2.1/2.2 | ✅ | Novel issue detection |
| **Accessibility Scanner** | Free | Android App | Android | ❌ | ✅ | ✅ | Free starting point |

---

## 🤝 Contributing

Contributions are welcome! If you know of an open-source Mobile App Accessibility Testing tool that should be listed here, please open a pull request with:

- Project name and URL
- Brief description (1–2 sentences)
- Stack and license
- Why it stands out

Please ensure the project is actively maintained (releases within the last 12 months) and genuinely open-source.

**Note on the open-source ecosystem:** The open-source landscape for **mobile app accessibility testing** is **fragmented and research-heavy** compared to web accessibility tooling. **GTXiLib** is the most mature open-source option for iOS, integrating directly into XCTest with minimal code changes [citation:12]. For Android, **AccessDroid** provides state-of-the-art semantics-tree analysis with near-perfect precision on screen reader issues [citation:11], while **A11yArgus** demonstrates novel detection categories (overlapping components, gesture-only navigation) but remains a research prototype [citation:1]. **Android Accessibility Scanner** remains the most accessible free starting point, though its detection depth trails specialized tools [citation:13]. Commercial platforms like BrowserStack and Evinced offer broader platform coverage, screen reader integration, and WCAG 2.2 support that open-source tools do not yet replicate [citation:2][citation:3].

---

## 📄 License

This list is released under CC0 1.0 Universal (Public Domain). The software projects listed retain their respective licenses.

---

⭐ **If this list helped you discover a useful tool, please star the repo!** ⭐
