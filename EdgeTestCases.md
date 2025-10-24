# Multilingual Support – Edge Test Cases


## Goal: 
This document outlines additional multilingual and integration test scenarios for locale handling across the KYC SDK and KYC App.


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

## **TC-02: Missing fallback resource file (en) - KYC web SDK**
**Configuration:**
en.json intentionally removed from:
- kyc-websdk → https://cdn.test.truuth.id/locales/kyc-websdk/v1/
  
{"enabled": true, "default": "en", "supported": ["en"], "detectionOrder": ["default"]}

**Test Steps:**
1. Launch the KYC Web SDK in English (en).
2. Verify behavior when the kyc web sdk en.json file is unavailable.

**Expected Result:**  
String key placeholders (e.g., invitee_details_page_title) appear in the KYC Web SDK copy texts.

---

## **TC-03: Missing fallback resource file (en) - KYC app**
**Configuration:**
en.json intentionally removed from:
- kyc-app → https://cdn.test.truuth.id/locales/kyc-app/v1/
  
{"enabled": true, "default": "en", "supported": ["en"], "detectionOrder": ["default"]}

**Test Steps:**
1. Launch the KYC app in English (en).
2. Verify behavior when the kyc app en.json file is unavailable.

**Expected Result:**  
String key or blank placeholders (e.g., invitee_details_page_title) appear in the KYC app copy texts.

---

## **TC-04: Missing fallback resource file (en) - Liveness Web SDK**
**Configuration:**
en.json intentionally removed from:
- liveness-websdk → https://cdn.test.truuth.id/locales/liveness-websdk/v1/
  
{"enabled": true, "default": "en", "supported": ["en"], "detectionOrder": ["default"]}

**Test Steps:**
1. Launch KYC journey in English (en).
2. Verify behavior when the liveness en.json file is unavailable.

**Expected Result:**  
String key placeholders (e.g., prompt_instruction) appear in the liveness copy texts.

---

## **TC-05: Missing Tenant-Level Locale Files**
**Configuration:**
en.json intentionally removed from:
- tenant-locales → https://cdn.test.truuth.id/kyc/welcomeemailkyc/locales/es.json
  
{"enabled": true, "default": "es", "supported": [es"], "detectionOrder": ["default"]} 

**Test Steps:**
1. Launch the KYC Web SDK in Spanish (es) using the affected tenant.
2. Verify behavior when the tenant-level es.json file is unavailable.

**Expected Result:**  
All IP framework copy texts fallback to English (en) coming from the backend .

---

## **TC-05: Missing Meta data Locale Files**
**Configuration:**
en.json intentionally removed from:
- document-metadata → https://cdn.test.truuth.id/locales/document-metadata/v1/
  
{"enabled": true, "default": "es", "supported": [es"], "detectionOrder": ["default"]} 

**Test Steps:**
1. Launch the KYC Web SDK in Spanish (es) using the affected tenant.
2. Verify behavior when the metadata es.json file is unavailable.

**Expected Result:**  
All metadata copy texts in KYC review edit fallback to English (en) coming from the backend .

---

## **TC-05: Multilingual Disabled – No Locale Object in Tenant Settings**
**Configuration:**
Tenant configuration does not include a locale object.

**Test Steps:**
1. Launch the KYC App in a supported locale.
2. Observe language behavior.
3. 
**Expected Result:**  
All the metadata copy texts should fallback to 'en'.

---

## **TC-06: Multilingual Disabled – Locale Object Present but Disabled**
**Configuration:**
 "locale": {
        "enabled": false, 
        "default": "en", 
        "supported": ["es", "fr", "en"], 
        "detectionOrder": ["query", "device", "default"]
    }

**Test Steps:**
1. Launch the KYC App in any supported locale.
2. Observe text and localization behavior.

**Expected Result:**  
All texts fallback to English (en).

---

## **TC-07: Multilingual Enabled – Empty Detection Order**
**Configuration:**
 "locale": {
        "enabled": true, 
        "default": "en", 
        "supported": ["es", "fr", "en"], 
        "detectionOrder": []
    }

**Test Steps:**
1. Launch the KYC App in any supported locale.
2. Observe which locale is applied.

**Expected Result:**  
All texts fallback to English (en).

---

## **TC-08: Multilingual Enabled – No Detection Value Provided**
**Configuration:**
 "locale": {
        "enabled": true, 
        "supported": ["es", "fr", "en"], 
        "detectionOrder": [default]
    }
**Test Steps:**
1. Launch the KYC App in any supported locale.
2. Observe which locale is applied.

**Expected Result:**  
All texts fallback to English (en).

---

## **KYC Web SDK Timeout Message (Multilingual Enabled)**
**Configuration:**
timeoutMessage: "SDK was timed out." configured in SDK.
"timeoutMessage" key exists in tenant-level locale file (es.json).

**Test Steps:**
1. Launch the KYC Web SDK in Spanish (es).
2. Simulate a network delay exceeding the timeout.
3. Observe the displayed timeout message.

**Expected Result:**  
The configured SDK timeout message is overridden by the localized tenant-level message.

---

## **TC-10: KYC Web SDK Timeout Message (Multilingual Disabled)**
**Configuration:**
- Multilingual disabled in tenant settings.
- timeoutMessage: "SDK was timed out." configured in SDK.  

**Test Steps:**
1. Disable multilingual in tenant settings.
2. Launch the KYC Web SDK.
3. Simulate a network delay exceeding the timeout.
4. Observe the displayed timeout message.
   
**Expected Result:**  
The SDK-configured timeout message is displayed as-is.

---

## **TC-11: Missing Primary Font**
**Configuration:**
Primary font: `Noto Sans`  
Fallback font: `Open Sans`

**Test Steps:**
1. Remove the Noto Sans font asset from the KYC App.
2. Launch the KYC App.
3. Observe the text rendering font.

**Expected Result:**  
Text should fallback to Open Sans when the primary font is unavailable.

---

## **TC-12: Independent Launch via Email Invitation**
**Configuration:**
KYC App accessible via standalone email invitation link (not embedded in SDK) with no locale as the query.
{"enabled": true, "default": "es", "supported": ["es"], "detectionOrder": ["query", "device", "default"]}

**Test Steps:**
1. Open the email invitation link.
2. Launch the KYC App directly.
3. Verify localization behavior.

**Expected Result:**  
The app applies the fallback locale (es) correctly.
All texts appear in Spanish.

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
1. Launch the Web SDK in Spanish (es).
2. Complete the KYC flow on mobile.
3. Observe localization across SDK and App.

**Expected Result:**  
All SDK and App texts display in Spanish.
Localization remains consistent with the native mobile experience.

## **TC-14: Network disconnection**
**Configuration:**
Multilingual enabled.

**Test Steps:**
1. Launch the Web SDK/App in Spanish (es).
2. Simulate network disconnection in the middle of the journey.
3. Observe localization across SDK / App.

**Expected Result:**  
All SDK/ App static texts display in Spanish unless the journey blocked due to the connection issue.

## **TC-15: Backward Comaptibility in KYC mobile app**
**Configuration:**
Install the old KYC mobile app version from production.

**Test Steps:**
1. Launch the Web SDK/App with multilingual disabled.
3. Observe the end-to-end journey.

**Expected Result:**  
The full journey should work with no issue.
