<img width="1860" height="317" alt="image" src="https://github.com/user-attachments/assets/c484ecc8-abf0-4f3f-b0f5-61446a323857" />


# TransferGo Mobile App – QA & Security Assessment

> **Status**: Functional but **not secure**  
> **Test Date**: October 2025  
> **Platform**: Android (Samsung Galaxy S24 Ultra, Android 15)  
> **App Version**: v4.156.0.5  

This repository contains a manual quality assurance and security evaluation of the **TransferGo international money transfer app** (Android). The assessment focused on user onboarding, KYC verification, payment flows, and security resilience—executed independently for educational and professional portfolio purposes.

---

## 🔍 Overview

A comprehensive test cycle was performed across **97 test cases** in **7 core modules**, including registration, identity verification, card binding, international transfers, and negative/security testing. While all intended user workflows passed successfully, **critical security and reliability issues** were uncovered that impact real-world trust and safety.

---

## 📌 Key Findings

### ✅ **What Worked Well**
- 100% pass rate in core user journeys (registration, transfers, receiver management)
- Clear fee and FX rate transparency
- Secure handling of payment details (e.g., CVV never stored)
- Structured, regulation-compliant onboarding (AML/KYC questionnaire)

### ⚠️ **Critical Risks Identified**
- **Account Takeover via 4-Digit PIN**  
  Brute-force access to real accounts was possible using common PINs and publicly available phone numbers.  
  → **Severity: Critical** (`BR-3`, `BR-4`)
  
- **Undelivered Transfers**  
  Funds were **debited immediately** but **never arrived** to recipients after **48+ hours**, with no status updates.  
  → **Service reliability failure**

- **KYC Misleading Feedback**  
  Fake ID uploads received a “Thank you! Verification successful” message—yet all transfers were later blocked with no explanation.  
  → **Severity: Medium** (`BR-1`, `BR-2`)

- **Weak Email Validation**  
  Accepted RFC 5322–noncompliant formats (e.g., leading/trailing dots, hyphen-starting domains).  
  → **Severity: Medium** (`BR-5` to `BR-9`)

- **Unresponsive Support**  
  An urgent in-app support request received **no response** within 48+ hours, contradicting “24/7 support” claims.

---

## 🛠 Recommendations

To achieve production-grade security, the following fixes are essential:

| Area | Action |
|------|--------|
| **Authentication** | Replace 4-digit PIN with **6-digit code** or **mandatory biometric login**; enforce **lockout after 3 failed attempts** |
| **Email Validation** | Reject malformed emails per **RFC 5322** (e.g., `...user@domain.com`, `user@-domain.com`) |
| **KYC UX** | Replace “Verification successful” with: _“Your ID is under review. Transfers may be delayed for security.”_ |
| **Transfer Transparency** | Provide **real-time status**, delivery ETAs, and **immediate alerts** for delays or suspensions |
| **Support** | Implement a **<30-minute SLA** for urgent issues |
| **Form Validation** | Disable “Continue” until valid inputs (e.g., ≥2 characters for names, valid DOB) |

---

## 🧪 Testing Scope

| Module | Test Cases | Pass Rate |
|-------|-----------|----------|
| User Registration | 68 | 100% |
| KYC Verification | 9 | 100% |
| Card Management | 4 | 100% |
| Transfer Flow | 10 | 100% |
| Receiver Management | 11 | 100% |
| Negative & Security Testing | 17 | 70.6% |

> 🔒 **Note**: All testing was performed ethically. No private user data was accessed or retained beyond what is publicly available or self-provided.

---

## 📎 Deliverables

- Full test report: [`TransferGo - REPORT.docx`](TransferGo - REPORT.docx)  
- 9 logged bugs (2 Critical, 7 Medium) + 2 service reliability observations  
- Annotated findings with actionable remediation steps

---

## 🚫 Release Readiness

> ❌ **Not recommended** for high-value or sensitive financial use until **`BR-3`, `BR-4`, `BR-5`, and `BR-9`** are resolved.  
>  
> While the app is **user-friendly and regulation-compliant**, the **authentication flaw** and **post-payment opacity** create unacceptable risk exposure.

---

## ℹ️ Additional Info

- **Regulated by**: FCA (UK) & Bank of Lithuania  
- **Public Ratings**: Google Play ★4.6, App Store ★4.7, Trustpilot ★4.4  
- **Common user complaints**: Delays in high-risk corridors, slow refunds, support responsiveness  

This report is shared for **educational and professional portfolio purposes only**. All findings are derived from public app usage and ethically conducted testing.
