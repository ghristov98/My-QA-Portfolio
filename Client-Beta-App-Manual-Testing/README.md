# QA Testing Report: Rainbow Ethereum Wallet (Beta v1.3)

<img width="1592" height="631" alt="image" src="https://github.com/user-attachments/assets/2f690041-2647-41a7-8b5d-d8e5e30cf8fd" />


> **Project Type**: Manual Quality Assurance & Security Testing  
> **Client**: Rainbow (Confidential Beta)  
> **Role**: QA Tester  
> **Duration**: September 2025  
> **Platform**: Android (Samsung Galaxy S24 Ultra, Android 15)

---

##  Overview

As part of a confidential QA engagement with **Finax Solutions**, I conducted an end-to-end manual test of the unreleased **Rainbow Beta v1.3**—an Ethereum wallet application with integrated KYC (Know Your Customer) identity verification.

The primary objective was to evaluate the **user onboarding flow**, **authentication security**, and **KYC pipeline robustness**, with special focus on preventing identity fraud and ensuring a seamless user experience.

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

>  **99 test cases executed** across 6 functional modules  
>  **Full visual documentation** with annotated screenshots at every step

---

##  Critical Findings

Despite a polished UI, the beta revealed **severe security vulnerabilities** in its KYC pipeline:

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
>  **Recommendation**: **Do not release** without major security fixes

---

##  Key Recommendations Provided

1. Implement **server-side document validation** (MRZ parsing, hologram checks)
2. Integrate **liveness detection** (blink, head turn) in selfie/video flows
3. Enforce **dual presence** (face + ID) in co-verification photos
4. Add **OCR + address matching** for proof-of-residence
5. Fix broken navigation and improve password/email validation

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
