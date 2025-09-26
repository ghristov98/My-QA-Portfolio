# QA Testing Report: Rainbow Ethereum Wallet (Beta v1.3)

<img width="1592" height="631" alt="image" src="https://github.com/user-attachments/assets/2f690041-2647-41a7-8b5d-d8e5e30cf8fd" />


> **Project Type**: Manual Quality Assurance & Security Testing  
> **Client**: Rainbow (Confidential Beta)  
> **Role**: QA Tester  
> **Duration**: September 2025  
> **Platform**: Android (Samsung Galaxy S24 Ultra, Android 15)

---

##  Overview

This assignment was commissioned to **evaluate the effectiveness of Rainbow’s newly developed in-house AI authentication system**, designed to **compare facial biometrics from a user’s government-issued ID with real-time selfies and liveness videos** during onboarding.

As stated in the testing brief:
> _“Rainbow’s newly improved authentication-algorithm will compare the user’s documents to facial features in real-time… the in-house developed AI will compare between the features on the document and the features of the tester.”_

My role was to **stress-test this AI pipeline** by submitting a wide range of valid, invalid, partial, and synthetic inputs—and assess whether the system could reliably detect fraud, enforce liveness, and validate identity.

---

##  Scope of Testing

- **User Registration Flow**  
- **KYC Verification Modules**:
  - Government ID Upload & Validation
  - Live Selfie Capture (Face Scan)
  - Face + ID Co-Verification Photo
  - Liveness Video Challenge
  - Proof-of-Address Submission
- **Security & Usability Heuristics**
- **Cross-Device Compatibility** (Android v8+)

- Each step was designed to feed data into Rainbow’s proprietary AI for:
- Facial feature matching (ID photo ↔ live face)
- Liveness detection
- Document authenticity checks
- Consistency across multi-modal inputs

>  **99 test cases executed** across 6 functional modules  
>  **Full visual documentation** with annotated screenshots at every step

---

##  Critical Findings

Despite the stated AI capabilities, **no meaningful server-side validation or biometric analysis occurred** during testing:

- **69 bugs logged** — **65 classified as Critical**
- **KYC bypasses**: System accepted:
  - Fake or partial ID images
  - Selfies without faces or with obstructions (sunglasses, hats)
  - Photos containing *only* an ID or *only* a face (not both)
  - AI-generated faces and non-compliant liveness videos
  - Arbitrary files as proof-of-address (no OCR or validation)
- **No server-side validation** or real-time AI analysis during verification
- **Non-functional UI elements** (e.g., “I already have a wallet”, “Terms of Use”)

>  **Overall pass rate: 66.7%**  
>  **Conclusion**: The app’s **AI-powered KYC system failed to perform its core function**—enabling trivial bypass of identity verification. This creates a **high-risk vulnerability** for mass fraudulent account creation.

##  Recommendations

To make the AI pipeline production-ready, Rainbow must implement:
- **Server-side facial matching** (ID photo ↔ live selfie) with confidence scoring
- **Active liveness detection** (e.g., challenge-response: “blink”, “turn left”)
- **Document validation** via MRZ parsing, hologram detection, and edge completeness
- **Real-time capture guidance** (e.g., overlay frames, lighting feedback)
- **OCR + manual review fallback** for proof-of-address

---

##  Tools & Methodology

- **Manual exploratory & scenario-based testing**
- **Boundary & negative testing** (e.g., invalid emails, weak passwords)
- **Fraud simulation** using synthetic/fake inputs
- **Device**: Samsung S24 Ultra (Android 15, One UI 7.0)
- **Reporting**: Structured test cases, bug tracking (BR-1 to BR-69), Telegram submission

---

##  Deliverables

- Comprehensive **QA Test Report** (99 test cases, 69 bug reports)
- Annotated **screenshots** for every screen and failure scenario
- Actionable **UX & security improvement recommendations**

>  *All personal/test data was securely handled and auto-deleted post-test per client policy.*

---

##  Outcome

My findings directly influenced the client’s decision to **halt release** and prioritize **KYC pipeline hardening**. This project underscores the critical role of rigorous manual QA in **crypto security**, where flawed identity verification can enable financial fraud at scale.

---

*Confidential project conducted under NDA. Public details shared with permission for portfolio use only. Full report available upon request.*
