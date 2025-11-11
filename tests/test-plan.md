# 📋 Test Plan – Book Store App QA Project  
**Team:** `PLP Testers`  
**Version:** 1.1 (rewritten)  
**Date:** 2025-11-11  

---

## 1. Objective & Scope
Prove—through risk-based testing—that the React Book Store satisfies every functional (FR) and non-functional (NFR) requirement, including 10 intentionally seeded defects, before the 18 Nov 2025 production release.  
Core focus: cart → checkout → payment flow, WCAG 2.1 AA, performance budgets (LCP ≤ 2.5 s, TTI ≤ 1 s), cross-browser stability, and security hygiene.

---

## 2. In-Scope Features (FR map)
| Area | IDs | Description |
|------|-----|-------------|
| Catalog | FR-C01 | browse, search, lazy images |
| Cart | FR-O01–O03 | add, update qty, sub-total, stock guard |
| Checkout | FR-O04–O05 | wizard, validation, Paystack payment |
| Orders | FR-O06 | history, status life-cycle |
| Admin | FR-M01–M05 | CRUD, inventory, moderation |
| Reviews | FR-U01–U03 | post-purchase rating, sanitisation |
| Returns | FR-R01–R03 | 7-day window, refund simulation |
| Notifications | FR-N01–N02 | in-app bell, unread count, mark read |
| A11y | FR-X01 | WCAG 2.1 AA |
| Performance | FR-X02 | LCP ≤ 2.5 s, TTI ≤ 1 s |
| Security | FR-S01–S03 | XSS prevention, URL whitelist |
| Seeded Defects | — | 10 bugs (currency, rounding, XSS, etc.) |

---

## 3. Out-of-Scope
- Native mobile apps (iOS/Android)  
- Email/SMS delivery (in-app only)  
- PCI-DSS audit of Paystack SDK  
- Load testing &gt; 500 concurrent users (deferred to Phase-2)

---

## 4. Environments
| Tier | URL | Browsers | Devices | Throttling |
|------|-----|----------|---------|------------|
| Local | `http://localhost:3000` | Chrome 142, Firefox 132, Safari 17 | Win-11 14″, Samsung A34, iPhone 12 Pro | none |
| Staging | `https://bookstore-staging.netlify.app` | + Edge 129 | add Galaxy Tab S8 | Fast-3G |

Screen-reader combo: NVDA 2024 + Firefox, VoiceOver + Safari iOS.

---

## 5. Tools
- **Test mgmt:** Jira Kanban  
- **Exploratory:** RapidReporter 2.3  
- **A11y:** axe-core 4.9, WAVE, Lighthouse  
- **Perf:** Lighthouse-CI, WebPageTest, React Profiler  
- **Network:** MSW 2.1 for mock latency/errors  
- **Automation:** Cypress 13 (e2e), React Testing Library (unit)  
- **CSV validation:** Python pytest  
- **Security:** OWASP ZAP baseline scan

---

## 6. Risks & Mitigations
| Risk | Impact | Likelihood | Mitigation |
|------|--------|------------|------------|
| Paystack test key expires | High | Low | calendar alert + key-rotation script |
| Stock race condition | Major | Medium | pessimistic UI lock + dual-tab test |
| Currency mismatch (UI vs gateway) | Major | Medium | explicit USD test run |
| CSV export decimal comma | Minor | High | force `locale=en-US` in export util |
| Seeded XSS flagged by client | Major | Low | documented in report; safe-markdown lib |

---

## 7. Test Types & Targets
| Type | Coverage Target |
|------|-----------------|
| Functional | 100 % P1 flows, 80 % P2 |
| Accessibility | 0 critical WCAG 2.1 AA violations |
| Performance | LCP ≤ 2.5 s, TTI ≤ 1 s, Lighthouse 90+ |
| Compatibility | zero P1 bugs on latest 2 Chrome, Firefox, Safari, Edge |
| Security | zero high-severity OWASP ZAP alerts |
| Exploratory | ≥ 5 sessions/week, 30 bugs logged |

---

## 8. Entry / Exit Criteria
**Entry**  
- Code frozen 24 h before cycle  
- Staging deployment green on CI  
- Test data seeded (`/data/seed.json` v1.3)

**Exit**  
- All P1 defects closed or accepted  
- No critical a11y or security issues  
- Performance budget met on 3 consecutive runs  
- ≥ 90 % FR traceability with evidence

---

## 9. Deliverables & Schedule
| Artifact | Due | Owner |
|----------|-----|-------|
| This test plan | Nov 5 | QA Lead |
| Test cases | Nov 11 | Whole team |
| Defect log | Nov 11 (draft) → Nov 18 (final) | Everyone |
| Final report | Nov 18 | QA Lead |
| Video presentation | Nov 18 | PM + Designer |

---

## 10. Sign-Off
| Role | Name | Signature | Date |
|------|------|-----------|------|
| QA Lead | Asmamaw Yismaw | AY | 02 Nov 2025 |
| Risk Analyst | Jostina Mwamburi | JM | 02 Nov 2025 |
| Test Executor | Whitney Shisia | WS | 04 Nov 2025 |
