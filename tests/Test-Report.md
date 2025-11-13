# 📊 Final Test Report – Book Store App QA Project  
**Team:** PLP Testers  
**Product Version:** 1.1.0  
**Report Date:** 2025-11-14  
**Test Window:** 2025-11-05 → 2025-11-14  

---

## 1. Executive Summary
React-based Book Store (cart + checkout + Paystack) tested for **9 days**; **26 test cases**, **8 defects logged** (5 intentionally seeded).  
**100 % FR traceability** achieved; **performance & a11y budgets met**; **two Major / High-priority bugs block release** (oversell & price rounding).

---

## 2. Test Strategy
Risk-based focus on:  
- Cart → Checkout → Payment (business-critical)  
- WCAG 2.1 AA (legal risk)  
- LCP ≤ 2.5 s / TTI ≤ 1 s (UX risk)  
- Latest 2 browsers + responsive (market risk)  

**Techniques:** exploratory, Cypress e2e, axe, Lighthouse CI, OWASP ZAP baseline.

---

## 3. Scope & Coverage Overview
| Category | #Tests | Pass | Fail | Seeded | Cov. |
|----------|--------|------|------|---------|------|
| Functional | 18 | 15 | 0 | 3 | 100 % |
| A11y | 3 | 2 | 0 | 1 | 100 % |
| Performance | 2 | 2 | 0 | 0 | 100 % |
| Compatibility | 2 | 2 | 0 | 0 | 100 % |
| Security | 1 | 0 | 0 | 1 | 100 % |
| **Total** | **26** | **21** | **0** | **5** | **100 %** |

*(“Fail” = 0; seeded defects are accepted and documented.)*

---

## 4. Test Environments & Tools
- **Local:** `http://localhost:3000` (commit `bfb73f8`)
- **Staging:** `https://bookstore-staging.netlify.app`
- **Browsers:** Chrome 142, Firefox 132, Safari 17, Edge 129
- **Devices:** Win-11 laptop, Samsung A34, iPhone 12 Pro
- **Mgmt:** Jira Kanban **Automation:** Cypress 13 **A11y:** axe-core 4.9 **Perf:** Lighthouse 11 **Security:** OWASP ZAP 2.14

---

## 5. Defect Summary
| ID | Summary | Severity | Priority | Affected FR | Status |
|----|---------|----------|----------|-------------|--------|
| BUG-CART-01 | Stock race allows oversell | **Major** | **High** | FR-O03 | NEW |
| BUG-CART-02 | Float rounding → $19.994 shown | **Major** | **High** | FR-O02 | NEW |
| BUG-CART-03 | Remove button lacks aria-label | **Minor** | **Medium** | FR-X01 | NEW |
| Seeded-01 | Currency mismatch UI vs gateway | **Major** | **High** | FR-O03 | ACCEPTED |
| Seeded-02 | Return window accepts day 8 | **Minor** | **Low** | FR-R01 | ACCEPTED |
| Seeded-03 | XSS via markdown link | **Major** | **Medium** | FR-U03/S01 | ACCEPTED |
| Seeded-04 | Notification badge not updated | **Minor** | **Low** | FR-N02 | ACCEPTED |
| Seeded-05 | Search ignores diacritics | **Minor** | **Low** | FR-C01 | ACCEPTED |

*Evidence & reproduction steps: `tests/defect-log.md`*

---

## 6. Non-Functional Results
### Accessibility
- **axe automated:** 1 violation (BUG-CART-03)  
- **Manual WCAG 2.1 AA checklist:** 95 % compliant (focus, labels, color contrast OK)

### Performance (Lighthouse avg 3 runs)
| Metric | Target | Achieved | Status |
|--------|--------|----------|--------|
| LCP | ≤ 2.5 s | 2.1 s | ✔ |
| TTI | ≤ 1.0 s | 0.9 s | ✔ |
| Accessibility score | ≥ 90 | 94 | ✔ |

### Compatibility & Security
- **Cross-browser UI:** zero P1 deviations  
- **ZAP baseline:** no high-severity alerts; XSS defect intentionally seeded

---

## 7. Risk Register
| Risk | Probability | Impact | Mitigation / Owner |
|------|-------------|--------|--------------------|
| Oversell on concurrent drop | Medium | High | Implement server-side stock reservation (BE team) |
| Price display inaccuracy | Low | Medium | Replace float with `toMinorUnits` utility (FE #42) |
| a11y lawsuit potential | Low | High | Fix aria-label & schedule quarterly external audit |

---

## 8. Recommendations
1. **Resolve Major/High defects BUG-CART-01 & ‑02 before release.**  
2. Introduce **pessimistic stock lock** at checkout-start to close race window.  
3. **CI gate:** run Cypress + Lighthouse on every PR (P1 flows budgeted).  
4. **Expand device matrix** → Chrome-for-Android low-end & 4G throttling.  
5. **Quarterly a11y re-audit** to maintain WCAG 2.1 AA compliance.

---

## 9. Go / No-Go Statement
**CONDITIONAL GO** – all P1 user journeys work, performance & security targets met.  
**NO-GO** if Major/High defects remain open → both violate commercial correctness.

---

## 10. Appendices
A. [Traceability Matrix](./traceability-matrix.md)  
B. [Defect Log](./defect-log.md)  
C. [Test Cases](./test-cases.md)  
D. Evidence bundle: `tests/evidence/*` (screens, videos, LH reports, axe JSON)

---