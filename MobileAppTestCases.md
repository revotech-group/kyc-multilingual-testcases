# Multilingual Copy Verification - KYC Mobile App 


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
| TC-01 | Splash | Splash Screen | Launch app | Splash text, app name, and any taglines in Spanish. |
| TC-02 | Welcome | Welcome Screen | Launch app and verify welcome message | All text and call-to-action in Spanish. |
| TC-03 | TC | TC Start Screen | Open TC Start screen | Texts and labels localized in Spanish. |
| TC-04 | TC | TC Details Screen | Open TC Details screen | All details text in Spanish, no English remnants. |
| TC-05 | TC | TC Decline Popup | Trigger decline action | Popup text fully localized in Spanish. |
| TC-06 | Location Capture | Location Instruction Screen | Open location instruction screen | Instructional texts in Spanish. |
| TC-07 | Location Capture | Location Success Screen | Complete location capture | Success message displayed in Spanish. |
| TC-08 | Location Capture | Location Denied Screen | Deny location permission | Error message (“Permiso de ubicación denegado”) shown. |
| TC-09 | Come Back | Come Back Popup | Trigger comeback popup | Popup text localized in Spanish. |
| TC-10 | Come Back | Come Back Screen | Open comeback screen | Header and button text localized in Spanish. |
| TC-11 | Doc Capture – Doc Selection | Doc Selection Screen (Mandatory List) | Open doc selection screen | Mandatory document list localized in Spanish. |
| TC-12 | Doc Capture – Doc Selection | Doc Selection Screen (Optional List) | Open optional list | Optional document list localized in Spanish. |
| TC-13 | Doc Capture – Doc Selection | Mandatory Doc Skip Popup | Attempt to skip mandatory doc | Warning popup localized in Spanish. |
| TC-14 | Doc Capture – Doc Instruction | Doc Front Instruction Screen - One Sided | Start front doc capture | Instructions localized and grammatically correct in Spanish. |
| TC-15 | Doc Capture – Doc Instruction | Doc Front Instruction Screen - Two Sided | Start two-sided doc capture | Both front/back instructions localized in Spanish. |
| TC-16 | Doc Capture – Doc Instruction | Doc Front Instruction Screen - Multipage | Start multi-page doc capture | Each page instruction displayed in Spanish. |
| TC-17 | Doc Capture – Doc Instruction | Doc Back Instruction Screen - Two Sided | Capture back side | Text and hint localized in Spanish. |
| TC-18 | Doc Capture – Doc Scanner | Doc Scanner One Sided | Open doc scanner | Instruction labels and UI text in Spanish. |
| TC-19 | Doc Capture – Doc Scanner | Doc Scanner Two Sided | Open two-sided scanner | Text localized correctly in Spanish. |
| TC-20 | Doc Capture – Doc Scanner | Doc Scanner Multipage | Open multipage scanner | All scanning hints localized in Spanish. |
| TC-21 | Doc Capture – Doc Scanner | Camera Access Denied Screen | Deny camera permission | Error text localized (“Acceso a la cámara denegado”). |
| TC-22 | Doc Capture – Doc Preview | Doc Preview Screen | Open preview screen | Labels and buttons localized in Spanish. |
| TC-23 | Doc Capture – Doc Preview | Doc Uploading Popup | Upload document | Uploading popup text localized in Spanish. |
| TC-24 | Doc Capture – Doc Retry | Invalid Doc | Submit invalid doc | Error message localized in Spanish. |
| TC-25 | Doc Capture – Doc Retry | Doc Not Readable | Try unreadable doc | “Documento ilegible” message shown. |
| TC-26 | Doc Capture – Doc Retry | Doc Not Readable, Low Confidence | Submit low-confidence doc | Low confidence warning localized in Spanish. |
| TC-27 | Doc Capture – Doc Retry | Doc Not Classified, Low Confidence | Submit unclassified doc | Proper Spanish message displayed. |
| TC-28 | Doc Capture – Doc Retry | Doc Not Classified | Submit completely unrecognized doc | Default fallback text localized in Spanish. |
| TC-29 | Doc Capture – Medicare IRN | Medicare IRN Screen | Open Medicare IRN entry screen | All field labels localized in Spanish. |
| TC-30 | Doc Capture – Doc Success | Doc Success for ID Proofing | Complete ID proofing | Success message in Spanish. |
| TC-31 | Doc Capture – Doc Success | Doc Success for Address Proofing | Complete address proofing | Success message localized in Spanish. |
| TC-32 | NFC | NFC Instruction Screen | Start NFC process | Instructional text localized in Spanish. |
| TC-33 | Review Edit | Review Edit Screen | Open review edit screen | All text localized in Spanish. |
| TC-34 | Review Edit | Review Edit Confirmation Popup | Trigger review confirmation | Popup fully localized in Spanish. |
| TC-35 | Review Edit | Review Edit Screen Calendar Bar | Open calendar bar | All text in Spanish. |
| TC-36 | Review Edit | Review Edit Form Validation | Submit invalid form | Validation error messages localized in Spanish. |
| TC-37 | Doc Expiry | Doc Expiry Screen | Open doc expiry screen | Text localized (“Documento caducado”). |
| TC-38 | Doc Expiry | Doc Expiry Reject Popup | Trigger reject popup | Popup text localized in Spanish. |
| TC-39 | Address Recency | Doc Recency Screen | Open doc recency screen | All UI text localized in Spanish. |
| TC-40 | Name Match | Doc Name Match Screen | Open name match screen | Labels and warnings in Spanish. |
| TC-41 | Face Capture | Face Instruction Screen | Open face instruction screen | Instructions localized in Spanish. |
| TC-42 | Face Capture | Liveness Screen | Perform liveness check | Liveness guidance text localized in Spanish. |
| TC-43 | Face Capture | Face Preview Screen | Open preview | UI text localized in Spanish. |
| TC-44 | Face Capture | Face Uploading Popup | Upload face capture | Uploading text localized in Spanish. |
| TC-45 | ACN Capture | ACN Instruction Screen | Open ACN instruction | Instruction localized in Spanish. |
| TC-46 | ACN Capture | ACN Capture Screen | Capture ACN | Field names localized in Spanish. |
| TC-47 | ACN Capture | ACN Form Validation | Submit incomplete form | Validation error in Spanish. |
| TC-48 | ACN Capture | ACN Skip Popup | Attempt to skip ACN | Skip warning localized in Spanish. |
| TC-49 | Thank You | Thank You Screen | Complete verification | Thank you message in Spanish. |
| TC-50 | Landscape Mode | Doc Scanner in Landscape | Rotate device | Layout and text adapt correctly in Spanish. |
| TC-51 | Landscape Mode | Face Scanner in Landscape | Rotate device | Text remains localized in Spanish. |
| TC-52 | Landscape Mode | KYC Screens in Landscape | Test all KYC screens in landscape | All labels localized in Spanish. |
| TC-53 | Redirect | Thank You Redirect Screen | Trigger redirect | Message localized in Spanish. |
| TC-54 | Redirect | Sorry Redirect Screen | Trigger sorry redirect | Message localized in Spanish. |
| TC-55 | Redirect | Comeback Redirect Screen | Trigger comeback redirect | All text localized in Spanish. |
| TC-56 | Error | No Link Sorry Screen | Open without link | “Enlace no válido” shown. |
| TC-57 | Error | Outage Sorry Screen | Simulate outage | Outage text localized in Spanish. |
| TC-58 | Error | Liveness Timeout Sorry Screen | Wait for timeout | Timeout message localized in Spanish. |
| TC-59 | Error | Jailbroken Sorry Screen | Use jailbroken device | Security message localized in Spanish. |
| TC-60 | Error | SSL Pinning Sorry Screen | Disable SSL pinning | SSL warning localized in Spanish. |
| TC-61 | Error | Minimum Version Sorry Screen | Use outdated app | Update warning localized in Spanish. |
| TC-62 | Error | Invalid Verification Sorry Screen | Trigger invalid verification | Error message localized in Spanish. |
| TC-63 | Error | Verification Completed Sorry Screen | Open completed verification | Message localized in Spanish. |
| TC-64 | Error | TC Decline Sorry Screen | Decline TC | Decline message localized in Spanish. |
| TC-65 | Error | General Sorry Screen | Trigger generic error | Generic message localized in Spanish. |
| TC-66 | Error | Connection Lost Popup | Disconnect network | “Sin conexión a Internet” message shown. |


---


## Expected Result (General):
1. 100% visible text localized to target language.

2. No string key placeholders like translation_key_login_button.
