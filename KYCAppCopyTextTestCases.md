# Multilingual Copy Verification - KYC App 


## Goal: 
Verify that all screens, dialogs, and dynamic content in the app correctly display localized text for a single selected locale.


## General Preconditions:

1. Multilingual feature enabled. 

2. Pick one locale (e.g., es)

3. Run through all major screens and flows.

4. Confirm that All static and dynamic strings are translated.


## Locale Sweep – Spanish (es)

# Multilingual Support Test Cases – Spanish (ES)

| **TC ID** | **Feature** | **Screen / Popup** | **Test Steps** | **Expected Result** |
|------------|--------------|--------------------|----------------|---------------------|
| TC-01 | Splash | Splash Screen | Launch app |  All static texts are displayed in Spanish. The app version number remains universal.|
| TC-02 | Welcome | Welcome Screen | Open welcome message | The heading, instruction, button all in Spanish.|
| TC-03 | TC | TC Start Screen | Open TC Start screen | Texts and labels localized in Spanish. |
| TC-04 | TC | TC Details Screen | Open TC Details screen | All details text in Spanish. |
| TC-05 | TC | TC Decline Popup | Trigger decline action | Popup text fully localized in Spanish. |
| TC-06 | Location Capture | Location Instruction Screen | Open location instruction screen | Instructional texts, buttons in Spanish. |
| TC-07 | Location Capture | Location Success Screen | Complete location capture | Success message, button displayed in Spanish. |
| TC-08 | Location Capture | Location Denied Screen | Deny location permission | The warning body, buttons are Spanish. |
| TC-09 | Come Back | Come Back Popup | Trigger comeback action | Popup texts localized in Spanish. |
| TC-10 | Come Back | Come Back Screen | Open comeback screen | All texts, buttons localized in Spanish. |
| TC-11 | Doc Capture – Doc Selection | Doc Selection Screen (Mandatory List) | Open doc selection screen with the mandatory list | All texts in Spanish. |
| TC-12 | Doc Capture – Doc Selection | Doc Selection Screen (Optional List) | Open doc selection screen with the optional list | All texts in Spanish. |
| TC-13 | Doc Capture – Doc Selection | Mandatory Doc Skip Popup | trigger skip mandatory doc action | The popup localized in Spanish. |
| TC-14 | Doc Capture – Doc Instruction | Doc Front Instruction Screen - One Sided | Start one-sided doc capture | All texts localized in Spanish. |
| TC-15 | Doc Capture – Doc Instruction | Doc Front Instruction Screen - Two Sided | Start two-sided doc capture | All texts localized in Spanish. |
| TC-16 | Doc Capture – Doc Instruction | Doc Front Instruction Screen - Multipage | Start multi-page doc capture | All texts localized in Spanish. |
| TC-17 | Doc Capture – Doc Instruction | Doc Back Instruction Screen - Two Sided | start back side of a two-sided doc | All texts localized in Spanish. |
| TC-18 | Doc Capture – Doc Scanner | Doc Scanner One Sided | Open doc scanner for one-sided doc | Instruction in Spanish. |
| TC-19 | Doc Capture – Doc Scanner | Doc Scanner Two Sided | Open doc scanner for two-sided doc | Instruction in Spanish. |
| TC-20 | Doc Capture – Doc Scanner | Doc Scanner Multipage | Open doc scanner for multi-page doc | Instruction in Spanish. |
| TC-21 | Doc Capture – Doc Scanner | Camera Access Denied Screen | Deny camera permission | All instructions and buttons in Spanish. |
| TC-22 | Doc Capture – Doc Preview | Doc Preview Screen | Open preview screen | All texts and buttons localized in Spanish. |
| TC-23 | Doc Capture – Doc Preview | Doc Uploading Popup | Trigger doc upload action | Uploading popup text localized in Spanish. |
| TC-24 | Doc Capture – Doc Retry | Invalid Doc | Submit invalid doc | The messages and buttons in Spanish. |
| TC-25 | Doc Capture – Doc Retry | Doc Not Readable | Try unreadable doc | The messages and buttons in Spanish. |
| TC-26 | Doc Capture – Doc Retry | Doc Not Readable, Low Confidence | Submit low-confidence doc | The messages and buttons in Spanish.|
| TC-27 | Doc Capture – Doc Retry | Doc Not Classified, Low Confidence | Submit unclassified doc | The messages and buttons in Spanish. |
| TC-28 | Doc Capture – Doc Retry | Doc Not Classified | Submit completely unrecognized doc | The messages and buttons in Spanish. |
| TC-29 | Doc Capture – Medicare IRN | Medicare IRN Screen | Upload medicare action | All field labels localized in Spanish. |
| TC-30 | Doc Capture – Doc Success | Doc Success for ID Proofing | Complete ID proofing doc capture | Success message in Spanish. |
| TC-31 | Doc Capture – Doc Success | Doc Success for Address Proofing | Complete address proofing doc capture | Success message localized in Spanish. |
| TC-32 | Doc Capture – NFC | NFC Instruction Screen | Start NFC process for e-passport | Instructional text localized in Spanish. Not applicable in web app. |
| TC-33 | Doc Capture – Review Edit | Review Edit Screen | Open review edit screen | All text localized in Spanish. |
| TC-34 | Doc Capture – Review Edit | Review Edit Confirmation Popup | Trigger review confirmation action | Popup fully localized in Spanish. |
| TC-35 | Doc Capture – Review Edit | Review Edit Screen Calendar Bar | Edit dates| The month field in Spanish. |
| TC-36 | Doc Capture – Review Edit | Review Edit Form Validation | Make the form invalid | Validation error messages localized in Spanish. |
| TC-37 | Doc Capture – Doc Expiry | Doc Expiry Screen | Open doc expiry screen | All texts and buttons localized in Spanish. |
| TC-38 | Doc Capture – Doc Expiry | Doc Expiry Reject Popup | Trigger reject action | Popup text localized in Spanish. |
| TC-39 | Doc Capture – Address Recency | Doc Recency Screen | Open doc recency screen | All UI text localized in Spanish. |
| TC-40 | Doc Capture – Name Match | Doc Name Match Screen | Open name match screen | Labels, warnings, buttons, in Spanish. |
| TC-41 | Face Capture | Face Instruction Screen | Open face instruction screen | Instructions localized in Spanish. |
| TC-42 | Face Capture | Liveness Screen | Open liveness | Liveness prompts localized in Spanish. |
| TC-43 | Face Capture | Face Preview Screen | Open face preview | UI text localized in Spanish. |
| TC-44 | Face Capture | Face Uploading Popup | Upload face image | The popup localized in Spanish. |
| TC-45 | ACN Capture | ACN Instruction Screen | Open ACN instruction | Instruction localized in Spanish. |
| TC-46 | ACN Capture | ACN Capture Screen | Open ACN Capture Screen | all UI texts localized in Spanish. |
| TC-47 | ACN Capture | ACN Form Validation | Make ACN form invalid | Validation error in Spanish. |
| TC-48 | ACN Capture | ACN Skip Popup | Trigger ACN skip action | The popup localized in Spanish. |
| TC-49 | Thank You | Thank You Screen | Complete verification | Thank you message in Spanish. |
| TC-50 | Landscape Mode | Doc Scanner in Landscape | Rotate device | The popup localized in Spanish. Not Applicable in mobile app. |
| TC-51 | Landscape Mode | Face Scanner in Landscape | Rotate device | The popup localized in Spanish. Not Applicable in mobile app.|
| TC-52 | Landscape Mode | KYC Screens in Landscape | Test all KYC screens in landscape | The popup localized in Spanish. Not Applicable in mobile app.|
| TC-53 | Redirect | Thank You Redirect Screen | Complete verification including redirect URL | Message and button in Spanish. |
| TC-54 | Redirect | Sorry Redirect Screen | KYC failure including redirect URL  | Message and button in Spanish. |
| TC-55 | Redirect | Comeback Redirect Screen | Open comeback including redirect URL | All text and button localized in Spanish. |
| TC-56 | Error | No Link Sorry Screen | Launch native app directly | All UI text in Spanish (based on PROD). Not applicable in web app|
| TC-57 | Error | Outage Sorry Screen | Simulate outage | Outage text localized in Spanish. |
| TC-58 | Error | Liveness Timeout Sorry Screen | Wait for liveness timeout | Timeout message localized in Spanish.Not applicable in native mobile app. |
| TC-59 | Error | Jailbroken Sorry Screen | Use jailbroken device | Security message localized in Spanish .Not applicable in web app. |
| TC-60 | Error | SSL Pinning Sorry Screen | Enable SSL pinning detection with an expired certificate | SSL warning localized in Spanish. Not applicable in web app. |
| TC-61 | Error | Minimum Version Sorry Screen | Use outdated app | Update warning localized in Spanish. Not applicable in web app. |
| TC-62 | Error | Invalid Verification Sorry Screen | Trigger invalid verification | Error message localized in Spanish. |
| TC-63 | Error | Verification Completed Sorry Screen | Open completed verification | Message localized in Spanish. |
| TC-64 | Error | TC Decline Sorry Screen | Decline TC | Decline message localized in Spanish. |
| TC-65 | Error | General Sorry Screen | Trigger generic error | Generic message localized in Spanish. |
| TC-66 | Error | Connection Lost Popup | Disconnect network | Timeout message localized in Spanish. |


---


## Expected Result (General):
1. 100% visible text localized to target language.

2. No string key placeholders like translation_key_login_button.

3. The universal numbers, including the app version, remain the same between languages.
