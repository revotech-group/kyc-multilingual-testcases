# Multilingual Support – Edge Test Cases


## Goal: 
This document outlines additional multilingual and integration test scenarios for locale handling, KYC SDK and KYC app behavior.


## General Preconditions:

1. Multilingual feature enabled. 

2. Pick one locale (e.g., es)


---

## Locale Sweep – Spanish (es)

## **TC-01: CORS Configuration for Locale JSON**
**Configuration:**
Locale JSON files hosted on CDN with CORS enabled.

**Test Steps:**
1. Launch the KYC demo app from a domain different from where the locale JSON files are hosted.  
2. Observe network requests for locale files.  
3. Check browser console for any CORS-related errors.

**Expected Result:**  
All locale files load successfully without CORS errors. Localization applies correctly on UI.

---

## **TC-02: Missing Locale JSON Fallback**
**Configuration:**
`en.json` intentionally removed from server.  

**Test Steps:**
1. Launch application with locale:'en'  
2. Verify behavior when 'en.json' locale file is unavailable.

**Expected Result:**  
String key placeholders (e.g. welcome_page_title) or blank placeholders appear.

---

## **TC-03: Missing Tenant IP Framework related Locale Files**
**Configuration:**
`en.json` intentionally removed from server.  

**Test Steps:**
1. Launch application with 'locale':'es' as a tenant supported locale
2. Verify behavior when 'en.json' locale file is unavailable.

**Expected Result:**  
String key placeholders (e.g. welcome_page_title) or blank placeholders appear.

---

## **TC-03: Missing Fallback Locale and Default**
**Configuration:**
`es-ES.json` and `en.json` both unavailable.  
Default locale points to missing file.

**Test Steps:**
1. Launch application with `?locale=es-ES`.  
2. Observe on-screen text and console behavior.

**Expected Result:**  
Application loads safely with hardcoded or placeholder defaults.  
User experience remains intact; error logged internally.

---

## **TC-04: Missing Tenant Metadata**
**Configuration:**
Tenant-level metadata file (`metadata.json`) removed.  
Locale detection enabled.

**Test Steps:**
1. Launch application with a tenant URL.  
2. Observe localization initialization flow.

**Expected Result:**  
App initializes with default metadata and locale.  
No crash or “undefined” values displayed.

---

## **TC-05: SDK Timeout Message (Localized)**
**Configuration:**
SDK configured with timeout = 10 seconds.  
`timeout_message` key exists in `es-ES.json`.

**Test Steps:**
1. Simulate network delay exceeding 10 seconds.  
2. Observe displayed timeout message.

**Expected Result:**  
Timeout message shown in Spanish (e.g., “Tiempo de espera agotado”).  
Formatting and grammar correct.

---

## **TC-06: SDK Timeout Message (Missing in JSON)**
**Configuration:**
`timeout_message` key removed from `es-ES.json`.  
Fallback message available in `en.json`.

**Test Steps:**
1. Trigger SDK timeout condition.  
2. Observe message displayed.

**Expected Result:**  
Timeout message displayed in English (fallback locale).  
No raw key name or placeholder text shown.

---

## **TC-07: Primary and Fallback Fonts**
**Configuration:**
Primary font: `Open Sans`  
Fallback font: `Noto Sans`

**Test Steps:**
1. Switch between English and Spanish locales.  
2. Check accented characters (á, é, í, ó, ñ) across devices (Android/iOS).  
3. Compare text rendering in both fonts.

**Expected Result:**  
Localized characters render correctly in both fonts.  
No missing glyphs, broken accents, or layout shifts.

---

## **TC-08: Deployment in US-Prod Environment**
**Configuration:**
Environment: `us-prod`  
Supported locales: `["en-US", "es-ES", "fr-FR"]`

**Test Steps:**
1. Deploy build to US production.  
2. Launch app using `?locale=es-ES`.  
3. Check text, date, and currency formatting.

**Expected Result:**  
Spanish localization loads correctly.  
Regional formatting (dates, currency) follow US standards.

---

## **TC-09: Independent Launch via Email Invitation**
**Configuration:**
KYC app accessible via standalone email invitation link.

**Test Steps:**
1. Open email invitation.  
2. Launch KYC app directly (no SDK embedding).  
3. Verify localization behavior.

**Expected Result:**  
App applies selected locale (e.g., Spanish) correctly.  
All texts localized without SDK dependency.

---

## **TC-10: Mobile Access via KYC Web SDK**
**Configuration:**
Access KYC app through mobile browser via Web SDK.  
Supported locales: `["en", "es", "fr"]`.

**Test Steps:**
1. Set device language to Spanish.  
2. Launch Web SDK entry point.  
3. Complete KYC flow and observe text.

**Expected Result:**  
All SDK and app texts displayed in Spanish.  
Localization consistent with native mobile experience.
