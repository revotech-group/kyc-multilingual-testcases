# Multilingual Support – Edge Test Cases


## Goal: 
This document outlines additional multilingual and integration test scenarios for locale handling, KYC SDK and KYC app behavior.


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

## **TC-02: Missing Locale JSON Fallback (en)**
**Configuration:**
`en.json` intentionally removed from kyc-app (https://cdn.test.truuth.id/locales/kyc-app/v1/) and/or kyc-websdk (https://cdn.test.truuth.id/locales/kyc-websdk/v1/) folders of platform locales repo .  

**Test Steps:**
1. Launch KYC web SDK / web app in 'en'   
2. Verify behavior when 'en.json' locale file is unavailable.

**Expected Result:**  
String key placeholders (e.g. welcome_page_title) or blank placeholders appear in KYC app and/or KYC web SDK.

---

## **TC-03: Missing Tenant level Locale Files**
**Configuration:**
`es.json` intentionally removed from tenant locales repo.  

**Test Steps:**
1. Launch KYC web SDK / app in 'es' using the defected tenant
2. Verify behavior when 'es.json' tenant locale file is unavailable.

**Expected Result:**  
All the dynamic copy texts should fallback to 'en'.

---

## **TC-04: Missing Platform Level Metadata Locale Files**
**Configuration:**
`es.json` intentionally removed from document-metadata folder (https://cdn.test.truuth.id/locales/document-metadata/v1/)

**Test Steps:**
1. Launch KYC app in a tenant and platform supported locale like 'es'
2. Verify behavior when 'es.json' metadata locale file is unavailable.

**Expected Result:**  
All the metadata copy text should fallback to 'en'.

---

## **TC-05: Multilingual disabled - No Locale object in tenant setting**
**Configuration:**
No locale object in tenant setting

**Test Steps:**
1. Launch KYC app in a tenant and platform supported locale

**Expected Result:**  
All the metadata copy text should fallback to 'en'.

---

## **TC-06: Multilingual disabled - Locale object disabled in tenant settings**
**Configuration:**
 "locale": {
        "enabled": false, 
        "default": "en", 
        "supported": ["es", "fr", "en"], 
        "detectionOrder": ["query", "device", "default"]
    }

**Test Steps:**
1. Launch KYC app in a tenant and platform supported locale

**Expected Result:**  
All the metadata copy text should fallback to 'en'.

---

## **TC-07: Multilingual disabled - empty detectionOrder List in tenant settings**
**Configuration:**
 "locale": {
        "enabled": true, 
        "default": "en", 
        "supported": ["es", "fr", "en"], 
        "detectionOrder": []
    }

**Test Steps:**
1. Launch KYC app in a tenant and platform supported locale

**Expected Result:**  
All the metadata copy text should fallback to 'en'.

---

## **TC-08: Multilingual enabled - No Locale value Provided**
**Configuration:**
 "locale": {
        "enabled": true, 
        "supported": ["es", "fr", "en"], 
        "detectionOrder": [default]
    }
**Test Steps:**
1. Launch KYC app in a tenant and platform supported locale

**Expected Result:**  
All the metadata copy text should fallback to 'en'.

---

## **TC-09: KYC WEB SDK Timeout Message (Localized if multilingual enabled)**
**Configuration:**
KYC web SDK configured with 'timeoutMessage':'SDK was timedout.'.  
`timeoutMessage` key exists in tenant level locale file (`es.json`).

**Test Steps:**
1. Launch KYC web SDK in a tenant and platform supported locale ('es')
1. Simulate network delay exceeding timeout.  
2. Observe displayed timeout message.

**Expected Result:**  
The SDK configured timeout will be overwitten by a localised tenant level timeout message.

---

## **TC-10: KYC WEB SDK Timeout Message ( if multilingual disabled)**
**Configuration:**
KYC web SDK configured with 'timeoutMessage':'SDK was timedout.'.  

**Test Steps:**
1- Disable multilingual in tenant settings
1. Launch KYC web SDK 
1. Simulate network delay exceeding timeout.  
2. Observe displayed timeout message.

**Expected Result:**  
The SDK configured timeout will be displayed.

---

## **TC-11: Missing Primary Font**
**Configuration:**
Primary font: `Noto Sans`  
Fallback font: `Open Sans`

**Test Steps:**
1. Remove Noto Sans asset file from KYC app .
2. Launch KYC app   
3. Check text rendering font.

**Expected Result:**  
The font should fallback to 'Open Sans' since the primary font is not available.

---

## **TC-12: Independent Launch via Email Invitation**
**Configuration:**
KYC app accessible via standalone email invitation link.

**Test Steps:**
1. Open email invitation.  
2. Launch KYC app directly (no SDK embedding).  
3. Verify localization behavior.

**Expected Result:**  
App applies fallback locale (en) correctly.  
All texts are in english.

---

## **TC-13: Mobile Access via KYC Web SDK**
**Configuration:**
Access KYC native mobile app via Web SDK.  
"locale": {
        "enabled": true, 
        "default": "en", 
        "supported": ["es", "fr", "en"], 
        "detectionOrder": ["query", "device", "default"]
    }

**Test Steps:**
1. Launch Web SDK in 'es'.  
2. Launch Web SDK entry point.  
3. Complete KYC flow and observe text.

**Expected Result:**  
All SDK and app texts displayed in Spanish.  
Localization consistent with native mobile experience.
