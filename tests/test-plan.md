# 📋 Test Plan – Book Store App QA Project  
**Team:** PLP Testers  
**Version:** 2.0  
**Date:** November 17, 2025  
**Project:** Book Store E-Commerce Web Application  
**Application Version:** 1.1.0

---

## 1. OBJECTIVE & SCOPE

### 1.1 Test Objectives
Validate that the React-based Book Store E-Commerce Application satisfies all functional (FR) and non-functional (NFR) requirements before the production release. Testing will focus on:

- **Business-Critical Flows**: Cart → Checkout → Payment → Order Tracking
- **Accessibility Compliance**: WCAG 2.1 AA standards
- **Performance Targets**: LCP ≤ 2.5s, TTI ≤ 1.0s
- **Cross-Browser Compatibility**: Latest 2 versions of major browsers
- **Security Hygiene**: XSS prevention, input sanitization

### 1.2 Success Criteria
- All P1 (Critical) defects resolved or accepted
- No critical accessibility or security violations
- Performance budgets met consistently
- ≥90% requirements traceability with evidence
- All core user journeys functional

---

## 2. IN-SCOPE FEATURES

### 2.1 Functional Requirements Coverage

| Feature Area | FR Codes | Description | Priority |
|--------------|----------|-------------|----------|
| **Catalog Management** | FR-M01 | Browse, search, filter, sort, lazy image loading | High |
| **Cart Operations** | FR-O01 | Add, update quantity, remove, subtotal calculation, stock validation, persistence | High |
| **Checkout Process** | FR-O02 | Multi-step wizard, form validation, coupon application | High |
| **Payment Integration** | FR-O03 | Paystack integration, success/cancel/error handling, currency display | High |
| **Order Management** | FR-O04, FR-O05 | Order history, status lifecycle, CSV export | High |
| **Returns & Refunds** | FR-R01, FR-R02 | 7-day return window, refund processing, audit trail | Medium |
| **Reviews & Ratings** | FR-U01, FR-U02 | Post-purchase reviews, duplicate prevention, moderation | Medium |
| **Q&A System** | FR-U03 | Safe markdown support, URL validation | Medium |
| **Admin Console** | FR-M01, FR-M02, FR-M03 | Catalog CRUD, inventory management, order updates | High |
| **Notifications** | FR-N01, FR-N02 | In-app notifications, unread count, mark as read | Low |
| **Accessibility** | FR-X01 | WCAG 2.1 AA compliance, keyboard navigation, screen reader support | High |
| **Performance** | FR-X02 | LCP ≤ 2.5s, TTI ≤ 1.0s, lazy loading | High |
| **Compatibility** | FR-X03 | Cross-browser support (Chrome, Firefox, Safari, Edge) | High |
| **Security** | FR-X04, FR-S01 | XSS prevention, input sanitization, URL whitelisting | High |

### 2.2 Test Coverage Targets

| Test Type | Coverage Target | Rationale |
|-----------|-----------------|-----------|
| Functional | 100% P1 flows, 80% P2 flows | Business-critical paths must work |
| Accessibility | 0 critical WCAG 2.1 AA violations | Legal compliance requirement |
| Performance | LCP ≤ 2.5s, TTI ≤ 1.0s, Lighthouse ≥90 | User experience standard |
| Compatibility | Zero P1 bugs on latest 2 browser versions | Market coverage |
| Security | Zero high-severity OWASP ZAP alerts | Security baseline |
| Exploratory | ≥5 sessions/week | Unscripted bug discovery |

---

## 3. OUT-OF-SCOPE

The following items are explicitly excluded from this test cycle:

- ❌ Native mobile applications (iOS/Android)
- ❌ Email/SMS delivery systems (in-app notifications only)
- ❌ PCI-DSS compliance audit of Paystack SDK
- ❌ Load testing beyond 500 concurrent users (deferred to Phase 2)
- ❌ Internationalization/localization (English only)
- ❌ Backend API testing (frontend integration only)
- ❌ Database performance testing

---

## 4. TEST ENVIRONMENTS

### 4.1 Environment Configuration

| Environment | URL | Purpose | Status |
|-------------|-----|---------|--------|
| **Local Development** | `http://localhost:3000` | Development testing, debugging | Active |
| **Staging** | `https://bookstore-staging.netlify.app` | Integration testing, UAT | Active |
| **Production** | TBD | Live environment (post-release) | Pending |

### 4.2 Browser & Device Matrix

| Browser | Version | Operating System | Devices | Priority |
|---------|---------|------------------|---------|----------|
| Chrome | 142 | Windows 11, macOS 14 | Desktop, Laptop | P1 |
| Firefox | 132 | Windows 11, macOS 14 | Desktop, Laptop | P1 |
| Safari | 17 | macOS 14, iOS 17 | Desktop, iPhone 12 Pro | P1 |
| Edge | 129 | Windows 11 | Desktop, Laptop | P2 |
| Chrome Mobile | 142 | Android 13 | Samsung Galaxy A34 | P2 |
| Safari Mobile | 17 | iOS 17 | iPhone 12 Pro | P2 |

### 4.3 Network Conditions

| Network Type | Download | Upload | Latency | Test Scope |
|--------------|----------|--------|---------|------------|
| WiFi (Fast) | 100 Mbps | 20 Mbps | 10ms | Primary testing |
| 4G | 4 Mbps | 1 Mbps | 50ms | Mobile testing |
| 3G (Slow) | 1.5 Mbps | 750 Kbps | 100ms | Performance testing |

### 4.4 Accessibility Testing Setup

| Tool | Version | Purpose |
|------|---------|---------|
| NVDA | 2024 | Screen reader testing (Windows + Firefox) |
| VoiceOver | Latest | Screen reader testing (macOS + Safari, iOS) |
| axe DevTools | 4.9 | Automated accessibility scanning |
| WAVE | Latest | Visual accessibility evaluation |

---

## 5. TEST TOOLS & TECHNOLOGIES

### 5.1 Test Management
- **Jira**: Test case management, defect tracking
- **Confluence**: Test documentation, knowledge base
- **Git**: Version control for test artifacts

### 5.2 Test Automation
- **Cypress 13**: End-to-end testing
- **React Testing Library**: Component testing
- **Jest 29**: Unit testing framework
- **MSW 2.1**: API mocking for network testing

### 5.3 Quality Analysis
- **axe-core 4.9**: Accessibility testing
- **Lighthouse 11**: Performance, accessibility, SEO audits
- **Lighthouse CI**: Continuous performance monitoring
- **WebPageTest**: Detailed performance analysis
- **React Profiler**: Component performance analysis

### 5.4 Security Testing
- **OWASP ZAP 2.14**: Security vulnerability scanning
- **DOMPurify**: XSS prevention validation
- **npm audit**: Dependency vulnerability checking

### 5.5 Exploratory Testing
- **RapidReporter 2.3**: Session-based test management
- **Chrome DevTools**: Network, performance, console debugging

---

## 6. RISKS & MITIGATION STRATEGIES

### 6.1 Risk Register

| Risk ID | Risk Description | Probability | Impact | Risk Level | Mitigation Strategy | Owner |
|---------|------------------|-------------|--------|------------|---------------------|-------|
| R01 | Paystack test key expires during testing | Low | High | Medium | Set calendar alerts; maintain key rotation script | QA Lead |
| R02 | Stock race condition allows overselling | Medium | High | **High** | Implement pessimistic UI lock; dual-tab testing | Dev Team |
| R03 | Currency mismatch between UI and gateway | Medium | Major | **High** | Explicit USD test runs; validation checks | QA Team |
| R04 | CSV export uses comma instead of dot for decimals | High | Minor | Medium | Force `locale=en-US` in export utility | Dev Team |
| R05 | Test environment instability | Low | Medium | Low | Backup local environment; staging monitoring | DevOps |
| R06 | Incomplete test data | Medium | Medium | Medium | Maintain seed data scripts; data validation | QA Team |
| R07 | Browser compatibility issues | Low | High | Medium | Test on all target browsers early | QA Team |
| R08 | Performance degradation under load | Medium | High | **High** | Performance testing in each sprint | QA Team |

### 6.2 Risk Mitigation Timeline

- **Week 1**: Identify and document all risks
- **Week 2**: Implement mitigation strategies for High risks
- **Week 3**: Monitor and adjust mitigation effectiveness
- **Ongoing**: Weekly risk review meetings

---

## 7. ENTRY & EXIT CRITERIA

### 7.1 Entry Criteria

Testing will begin when ALL of the following conditions are met:

✅ Code freeze 24 hours before test cycle start  
✅ Staging environment deployed and stable  
✅ All P1 features implemented and unit tested  
✅ Test data seeded in test environment  
✅ Test cases reviewed and approved  
✅ Test environment access granted to QA team  
✅ Defect tracking system configured

### 7.2 Exit Criteria

Testing will be considered complete when ALL of the following are achieved:

✅ All test cases executed (100% execution rate)  
✅ All P1 (Critical) defects resolved or accepted  
✅ No open P2 (High) defects blocking core functionality  
✅ Zero critical accessibility violations (WCAG 2.1 AA)  
✅ Zero high-severity security vulnerabilities  
✅ Performance budgets met (LCP ≤ 2.5s, TTI ≤ 1.0s)  
✅ ≥90% requirements traceability documented  
✅ Test report completed and approved  
✅ Stakeholder sign-off received

### 7.3 Suspension & Resumption Criteria

**Testing will be suspended if:**
- Critical environment issues prevent testing
- More than 5 P1 defects are open simultaneously
- Test data corruption occurs
- Major scope changes are introduced

**Testing will resume when:**
- Environment issues are resolved
- P1 defect count reduced below threshold
- Test data restored and validated
- Scope changes approved and test cases updated

---

## 8. TEST DELIVERABLES & SCHEDULE

### 8.1 Deliverables

| Deliverable | Description | Format | Owner | Due Date |
|-------------|-------------|--------|-------|----------|
| Test Plan | This document | Markdown | QA Lead | Nov 5, 2025 |
| Test Cases | Detailed test scenarios | Markdown | QA Team | Nov 11, 2025 |
| Defect Log | Bug tracking document | Markdown | QA Team | Nov 18, 2025 |
| Test Report | Summary of test results | Markdown | QA Lead | Nov 18, 2025 |
| Comprehensive Report | Executive summary | Markdown | QA Lead | Nov 18, 2025 |
| Traceability Matrix | Requirements coverage | Markdown | QA Team | Nov 18, 2025 |
| Test Evidence | Screenshots, videos, logs | Files | QA Team | Nov 18, 2025 |

### 8.2 Test Schedule

| Phase | Activities | Start Date | End Date | Duration | Status |
|-------|-----------|------------|----------|----------|--------|
| **Planning** | Test strategy, test plan creation | Nov 1, 2025 | Nov 4, 2025 | 4 days | ✅ Complete |
| **Design** | Test case development, review | Nov 5, 2025 | Nov 7, 2025 | 3 days | ✅ Complete |
| **Execution** | Test execution, defect logging | Nov 8, 2025 | Nov 14, 2025 | 7 days | ✅ Complete |
| **Reporting** | Test report, metrics analysis | Nov 15, 2025 | Nov 17, 2025 | 3 days | ✅ Complete |
| **Sign-Off** | Stakeholder review, approval | Nov 18, 2025 | Nov 18, 2025 | 1 day | ⏳ Pending |

### 8.3 Resource Allocation

| Role | Name | Responsibility | Allocation |
|------|------|----------------|------------|
| QA Lead | Asmamaw Yismaw | Test strategy, reporting, stakeholder communication | 100% |
| Test Engineer | Whitney Shisia | Test execution, automation, defect logging | 100% |
| Test Engineer | Jostina Mwamburi | Test execution, exploratory testing, documentation | 100% |

---

## 9. TEST APPROACH & STRATEGY

### 9.1 Test Types

#### 9.1.1 Functional Testing
- **Scope**: All user-facing features and workflows
- **Approach**: Manual and automated testing
- **Coverage**: 100% P1 flows, 80% P2 flows
- **Tools**: Cypress, React Testing Library

#### 9.1.2 Integration Testing
- **Scope**: End-to-end user journeys
- **Approach**: Automated E2E tests
- **Coverage**: All critical paths
- **Tools**: Cypress

#### 9.1.3 Accessibility Testing
- **Scope**: WCAG 2.1 AA compliance
- **Approach**: Automated + manual testing
- **Coverage**: All pages and components
- **Tools**: axe-core, NVDA, VoiceOver

#### 9.1.4 Performance Testing
- **Scope**: Load times, responsiveness
- **Approach**: Automated performance audits
- **Coverage**: All pages
- **Tools**: Lighthouse, WebPageTest

#### 9.1.5 Security Testing
- **Scope**: XSS, input validation, authentication
- **Approach**: Automated scanning + manual testing
- **Coverage**: All user inputs
- **Tools**: OWASP ZAP, manual penetration testing

#### 9.1.6 Compatibility Testing
- **Scope**: Cross-browser, cross-device
- **Approach**: Manual testing on target platforms
- **Coverage**: All major browsers and devices
- **Tools**: BrowserStack (if needed)

#### 9.1.7 Exploratory Testing
- **Scope**: Unscripted testing for edge cases
- **Approach**: Session-based testing
- **Coverage**: ≥5 sessions per week
- **Tools**: RapidReporter

### 9.2 Test Prioritization

Tests are prioritized using risk-based approach:

**P1 (Critical)**: Must pass before release
- Core shopping flow (browse → cart → checkout → payment)
- Payment processing
- Order creation
- Admin authentication

**P2 (High)**: Should pass before release
- Filtering and sorting
- Order management
- Admin CRUD operations
- Accessibility compliance

**P3 (Medium)**: Nice to have
- Reviews and ratings
- Q&A system
- Advanced admin features

**P4 (Low)**: Future enhancements
- Performance optimizations
- UI polish
- Additional features

---

## 10. DEFECT MANAGEMENT

### 10.1 Defect Lifecycle

```
New → Assigned → In Progress → Fixed → Verified → Closed
                                    ↓
                                Reopened (if verification fails)
```

### 10.2 Defect Severity Definitions

| Severity | Definition | Example | Response Time |
|----------|------------|---------|---------------|
| **Critical** | System crash, data loss, security breach | Payment processing fails completely | Immediate |
| **Major** | Core functionality broken, no workaround | Cannot add items to cart | 24 hours |
| **Minor** | Feature works with issues, workaround exists | Sort order incorrect | 1 week |
| **Trivial** | Cosmetic issues, typos | Button color slightly off | Backlog |

### 10.3 Defect Priority Definitions

| Priority | Definition | Timeline |
|----------|------------|----------|
| **High** | Must fix before release | Current sprint |
| **Medium** | Should fix soon | Next sprint |
| **Low** | Fix when possible | Backlog |

---

## 11. COMMUNICATION PLAN

### 11.1 Status Reporting

| Report Type | Frequency | Audience | Owner |
|-------------|-----------|----------|-------|
| Daily Standup | Daily | QA Team | QA Lead |
| Test Status Report | Daily | Project Team | QA Lead |
| Defect Summary | Daily | Dev Team | QA Team |
| Weekly Summary | Weekly | Stakeholders | QA Lead |
| Final Report | End of Cycle | All Stakeholders | QA Lead |

### 11.2 Escalation Path

1. **Level 1**: QA Team → Dev Team (technical issues)
2. **Level 2**: QA Lead → Dev Lead (blocking issues)
3. **Level 3**: QA Lead → Project Manager (critical decisions)
4. **Level 4**: Project Manager → Stakeholders (go/no-go decisions)

---

## 12. ASSUMPTIONS & DEPENDENCIES

### 12.1 Assumptions

- Test environment will be stable and available
- Test data will be accurate and sufficient
- Paystack test environment will be accessible
- Team members will be available as planned
- No major scope changes during test cycle

### 12.2 Dependencies

- Development team completes features on time
- Staging environment deployed 24h before testing
- Test data seeded before test execution
- Defect fixes delivered within agreed timelines
- Stakeholders available for reviews and approvals

---

## 13. APPROVAL & SIGN-OFF

### 13.1 Test Plan Approval

This test plan has been reviewed and approved by:

| Role | Name | Signature | Date |
|------|------|-----------|------|
| QA Lead | Asmamaw Yismaw | AY | Nov 17, 2025 |
| Test Engineer | Whitney Shisia | WS | Nov 17, 2025 |
| Test Engineer | Jostina Mwamburi | JM | Nov 17, 2025 |

### 13.2 Stakeholder Acknowledgment

**Status:** ⏳ Pending stakeholder review

| Role | Name | Signature | Date |
|------|------|-----------|------|
| Project Manager | _______________ | _____ | _________ |
| Development Lead | _______________ | _____ | _________ |
| Product Owner | _______________ | _____ | _________ |

---

## 14. DOCUMENT REVISION HISTORY

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | Nov 5, 2025 | Asmamaw Yismaw | Initial draft |
| 1.1 | Nov 11, 2025 | Whitney Shisia | Added test schedule details |
| 2.0 | Nov 17, 2025 | Asmamaw Yismaw | Updated with actual test results, fixed inconsistencies |

---

## 15. APPENDICES

### Appendix A: Glossary

| Term | Definition |
|------|------------|
| **FR** | Functional Requirement |
| **NFR** | Non-Functional Requirement |
| **LCP** | Largest Contentful Paint (performance metric) |
| **TTI** | Time to Interactive (performance metric) |
| **WCAG** | Web Content Accessibility Guidelines |
| **XSS** | Cross-Site Scripting |
| **P1/P2/P3** | Priority levels (1=Critical, 2=High, 3=Medium) |
| **UAT** | User Acceptance Testing |

### Appendix B: References

- [WCAG 2.1 Guidelines](https://www.w3.org/WAI/WCAG21/quickref/)
- [OWASP Testing Guide](https://owasp.org/www-project-web-security-testing-guide/)
- [Lighthouse Documentation](https://developers.google.com/web/tools/lighthouse)
- [Cypress Best Practices](https://docs.cypress.io/guides/references/best-practices)

---

**END OF TEST PLAN**

**Document Status:** Final  
**Next Review Date:** Post-Release (November 24, 2025)
