# Privacy & Consent Compliance Watchlist 🛡️

A curated watchlist and security monitoring resource tracking the top open-source GDPR compliance and consent management tools for small businesses.

---

## Overview

Small businesses operating online or handling European user data are required by the General Data Protection Regulation (GDPR) and the ePrivacy Directive to obtain explicit, informed, and freely given consent before running non-essential tracking cookies or scripts. Additionally, growing businesses must manage Data Subject Access Requests (DSARs) and maintain transparency.

This repository monitors the **top 5 open-source GDPR compliance and consent management solutions**, evaluates their maintenance activity, and flags potential security concerns and vulnerabilities identified in their open issues.

---

## Comparison Matrix

| Tool | Focus Area | Tech Stack | Stars | Maintenance Status | Issue Tracker |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **[orestbida/cookieconsent](#1-orestbidacookieconsent)** | Universal Cookie Consent & Preference Center | Vanilla JS | ~5.6k+ | Active (2026) | [Issues](https://github.com/orestbida/cookieconsent/issues) |
| **[kiprotect/klaro](#2-kiprotectklaro)** | Privacy & Script Consent Manager | JS / React | ~1.5k+ | Active (2026) | [Issues](https://github.com/kiprotect/klaro/issues) |
| **[AmauriC/tarteaucitron.js](#3-amaurictarteaucitronjs)** | Turnkey GDPR/CNIL Cookie Compliance | Vanilla JS | ~1.0k+ | Very Active (2026) | [Issues](https://github.com/AmauriC/tarteaucitron.js/issues) |
| **[ethyca/fides](#4-ethycafides)** | Privacy Engineering, CMP & DSAR Automation | Python / TypeScript | ~480+ | Very Active (2026) | [Issues](https://github.com/ethyca/fides/issues) |
| **[Mastermindzh/react-cookie-consent](#5-mastermindzhreact-cookie-consent)** | React / Next.js Consent Banner | React / TS | ~640+ | Very Active (2026) | [Issues](https://github.com/Mastermindzh/react-cookie-consent/issues) |

---

## Monitored Tools

### 1. orestbida/cookieconsent

- **Repository**: [https://github.com/orestbida/cookieconsent](https://github.com/orestbida/cookieconsent)
- **Direct Issue Tracker**: [orestbida/cookieconsent Issues](https://github.com/orestbida/cookieconsent/issues)

#### Description
`orestbida/cookieconsent` is one of the most widely adopted open-source cookie consent plugins on GitHub. Written in lightweight, dependency-free vanilla JavaScript (~5 KB gzipped), it provides a compliant consent banner, a granular user preference center, customizable cookie categories (necessary, analytics, marketing, etc.), and script blocking capabilities. It also natively supports Google Consent Mode (GCM v2) and multi-language translations out of the box.

#### Maintenance Activity
- **Stars & Adoption**: Over 5,670+ stars, 600+ forks, and widespread use across production websites.
- **Commit Frequency**: Highly active, with ongoing v3 releases, accessibility updates (WCAG target sizes and keyboard navigation), and quick community triage throughout 2025 and 2026.

#### Reported Security Concerns & Vulnerabilities (Open Issues)
1. **Static Analysis & Sanitization Gaps** ([#813](https://github.com/orestbida/cookieconsent/issues/813)): GitHub Code Scanning / CodeQL flagged high-severity alerts related to incomplete multi-character sanitization and potential input sanitization gaps when processing user configuration strings and DOM content.
2. **Category Consent Enforcement Bug** ([#805](https://github.com/orestbida/cookieconsent/issues/805)): A bug report indicates that in certain configurations, a category set as disabled or non-readonly could still be treated as enabled, risking unauthorized script execution without affirmative user consent.
3. **Accessibility Focus Trap Leak** ([#828](https://github.com/orestbida/cookieconsent/issues/828)): Using `Shift+Tab` immediately upon opening the preferences modal can break the focus trap, causing keyboard focus to escape the modal into the underlying page content.

---

### 2. kiprotect/klaro

- **Repository**: [https://github.com/kiprotect/klaro](https://github.com/kiprotect/klaro)
- **Direct Issue Tracker**: [kiprotect/klaro Issues](https://github.com/kiprotect/klaro/issues)

#### Description
Klaro! is an open-source, privacy-friendly consent manager and script management platform developed by KIProtect. It intercepts scripts, iframes (YouTube, Google Maps), and tracking pixels directly in the browser DOM until the user grants explicit permission. It offers a floating badge for visitors to update preferences at any time, supports contextual consent placeholders, and integrates smoothly into standalone websites and CMS platforms (WordPress, TYPO3).

#### Maintenance Activity
- **Stars & Adoption**: Over 1,510+ stars, 250+ forks.
- **Commit Frequency**: Regularly maintained by maintainers and community contributors with pull request reviews, dependency upgrades, and ongoing compatibility patches through 2025 and 2026.

#### Reported Security Concerns & Vulnerabilities (Open Issues)
1. **CSP Inline Style Attribute Violations** ([#480](https://github.com/kiprotect/klaro/issues/480)): Klaro copies inline style attributes directly onto elements using `element.setAttribute()`. Under strict Content Security Policies that disallow `'unsafe-inline'`, this triggers browser security policy violations and can block elements from displaying properly.
2. **CSP `eval` Execution Errors** ([#331](https://github.com/kiprotect/klaro/issues/331)): Dynamic script evaluation upon user acceptance triggers `eval` CSP violations (`script-src`), requiring site operators to either permit `'unsafe-eval'` (an XSS risk) or suffer broken tracking tags in hardened environments.
3. **Consent Update Race Condition in Google Tag Manager** ([#564](https://github.com/kiprotect/klaro/issues/564)): A reported race condition where `google-tag-manager.onAccept` may fire prior to updating consent variables (`ad_storage`, `analytics_storage`), potentially executing tracking before consent state has propagated.
4. **Security Reporting Channel** ([#544](https://github.com/kiprotect/klaro/issues/544)): Community inquiries highlight the need for a formalized `SECURITY.md` and responsible vulnerability disclosure process.

---

### 3. AmauriC/tarteaucitron.js

- **Repository**: [https://github.com/AmauriC/tarteaucitron.js](https://github.com/AmauriC/tarteaucitron.js)
- **Direct Issue Tracker**: [AmauriC/tarteaucitron.js Issues](https://github.com/AmauriC/tarteaucitron.js/issues)

#### Description
Originating in France and designed to strictly align with French CNIL and European GDPR requirements, `tarteaucitron.js` is a turnkey cookie manager. It provides native, out-of-the-box blocking and consent mechanisms for more than 150 third-party services (Google Analytics 4, Tag Manager, Facebook Pixel, YouTube, reCAPTCHA, Piwik PRO, etc.) without requiring custom integration code. It supports Google Consent Mode v2 and multi-language banners.

#### Maintenance Activity
- **Stars & Adoption**: Over 1,050+ stars, 450+ forks, and widespread European public sector / business adoption.
- **Commit Frequency**: Very actively maintained by author Amauri Champeaux. Frequent releases (v1.34.0 released in 2026), prompt pull request merges, and exceptional issue hygiene (<10 open issues total).

#### Reported Security Concerns & Vulnerabilities (Open Issues)
1. **URL Scheme Sanitization (Defense-in-Depth)** ([#1405](https://github.com/AmauriC/tarteaucitron.js/issues/1405)): An open issue flagged to enforce explicit protocol validation (`http:` and `https:`) on links used for privacy policies, read-more links, and source URLs, preventing potential open redirects or pseudo-protocol code execution (such as `javascript:` links).
2. **Server-Side vs. Client-Side State Synchronization** ([#1412](https://github.com/AmauriC/tarteaucitron.js/issues/1412)): Reports addressing potential discrepancies when coordinating server-side tracking configurations with client-side script blockers, ensuring consent state is consistently enforced across both layers.

---

### 4. ethyca/fides

- **Repository**: [https://github.com/ethyca/fides](https://github.com/ethyca/fides)
- **Direct Issue Tracker**: [ethyca/fides Issues](https://github.com/ethyca/fides/issues)

#### Description
`fides` by Ethyca is an open-source privacy engineering and compliance platform. Unlike front-end-only cookie banners, Fides delivers an end-to-end privacy stack: an integrated Consent Management Platform (CMP with banners, preference centers, Google Consent Mode v2, and IAB TCF 2.2), combined with back-end automated orchestration for GDPR / CCPA Data Subject Access Requests (DSAR/DSR for right to access and right of erasure) and privacy data mapping.

#### Maintenance Activity
- **Stars & Adoption**: 480+ stars, 160+ forks, backed by an active engineering organization and open-source contributors.
- **Commit Frequency**: Enterprise-grade development pace with daily commits, weekly releases (e.g., v2.86.x in 2026), comprehensive automated CI testing, and extensive documentation.

#### Reported Security Concerns & Vulnerabilities (Open Issues)
1. **Predictable Salt & Documentation Discrepancy on Privacy Identity Indexing** ([#3653](https://github.com/ethyca/fides/issues/3653)): Fides indexes privacy request identities using SHA-512 with a predictable salt to facilitate lookup matches. While intended for index comparison, an inaccurate docstring stated it was for password hashing with a generated salt ([CWE-1116](https://cwe.mitre.org/data/definitions/1116.html)), highlighting crypto-hygiene risks and potential developer misuse.
2. **Vulnerable Stale Dependency in Frontend Admin UI** ([#3702](https://github.com/ethyca/fides/issues/3702)): The admin UI includes `xlsx` 0.18.5 (SheetJS) for datamap export functionality. This npm version is unmaintained and contains known vulnerabilities (including CVE-2023-30533 Prototype Pollution).
3. **Dual Encryption Key Configuration Confusion** ([#2699](https://github.com/ethyca/fides/issues/2699)): Inconsistent dual configuration between `security.app_encryption_key` and `user.encryption_key` across database columns (such as data protection officer and controller records), creating administrative confusion and key management friction.

---

### 5. Mastermindzh/react-cookie-consent

- **Repository**: [https://github.com/Mastermindzh/react-cookie-consent](https://github.com/Mastermindzh/react-cookie-consent)
- **Direct Issue Tracker**: [Mastermindzh/react-cookie-consent Issues](https://github.com/Mastermindzh/react-cookie-consent/issues)

#### Description
`react-cookie-consent` is the leading dedicated cookie consent component for React and Next.js applications. Designed for single-page apps (SPAs) and modern web platforms, it provides a lightweight, highly customizable banner with explicit Accept and Decline triggers, custom styling, cookie attribute configurations (`SameSite`, `Secure`), and callback handlers (`onAccept`, `onDecline`) to cleanly gate analytics and tracking pixels.

#### Maintenance Activity
- **Stars & Adoption**: Over 640+ stars, 150+ forks, and more than 300,000+ weekly downloads on npm.
- **Commit Frequency**: Actively maintained with zero open bug backlogs. Regularly upgraded to support modern frontend toolchains (e.g., React 19, Vite 8, TypeScript 6/7, Storybook 10).

#### Reported Security Concerns & Vulnerabilities (Open Issues)
1. **Automated Supply Chain & Dependency Tracking** ([#230](https://github.com/Mastermindzh/react-cookie-consent/issues/230)): Maintains an active Renovate Dependency Dashboard monitoring all upstream dependencies (such as `js-cookie`, `@mui/material`, and GitHub Actions) to prevent supply-chain vulnerabilities.
2. **Browser Storage Lifetime & ITP Constraints (Operational Consideration)** ([#160](https://github.com/Mastermindzh/react-cookie-consent/issues/160)): Cookie state stored solely via client-side JavaScript cookies is subject to strict browser storage restrictions (such as Safari ITP and Brave capping script-written cookies to 7 days), which can lead to frequent re-prompting or unintended expiration of opt-out records if server-side cookies are not implemented.

---

## Best Practice Recommendations for Small Businesses

1. **Explicit Prior Consent (No Opt-In by Default)**: Ensure no non-essential cookies or third-party tracking scripts execute before user consent is confirmed. Pre-ticked checkboxes or implied consent ("by continuing to browse, you agree") do not meet GDPR standards.
2. **CSP Hardening**: When implementing consent managers like Klaro, configure strict Content Security Policy headers while testing for inline style or script evaluation violations. Avoid adding `'unsafe-inline'` or `'unsafe-eval'` whenever possible.
3. **Google Consent Mode v2**: For businesses utilizing Google Tag Manager or GA4, verify that `analytics_storage` and `ad_storage` signals are updated prior to firing downstream tags to avoid race conditions.
4. **Regular Dependency Auditing**: Monitor upstream advisories on tools handling DOM injection and export files (`xlsx`, DOMPurify, etc.) using automated scanning tools like Dependabot, Renovate, or Snyk.
