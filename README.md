# Multilingual Support - Test Cases 

### TC-1: Query First Priority (Successful)
**Configuration:**
```json
{"enabled": true, "default": "fr", "supported": ["es-ES", "en", "fr"], "detectionOrder": ["query", "device", "default"]}
```

**Test Steps:**
1. Set browser language to `fr-FR` (valid)
2. Access application with `?locale=es-ES` (valid)
3. Verify application uses Spanish (Spain) locale

**Expected Result:** Query parameter takes priority, device detection skipped

### TC-2: Query First Priority (Failed) → Device Fallback
**Configuration:**
```json
{"enabled": true, "default": "en", "supported": ["es", "fr", "en"], "detectionOrder": ["query", "device", "default"]}
```

**Test Steps:**
1. Set browser language to `fr-FR` (valid - root supported)
2. Access application with `?locale=de-DE` (invalid - not supported)
3. Verify application uses French (root) locale

**Expected Result:** Query fails, device detection used, default skipped

### TC-3: Query & Device Failed → Default Applied
**Configuration:**
```json
{"enabled": true, "default": "es", "supported": ["es", "en"], "detectionOrder": ["query", "device", "default"]}
```

**Test Steps:**
1. Set browser language to `fr-FR` (invalid - root not supported)
2. Access application with `?locale=fr-FR` (invalid - root not supported)
3. Verify application uses Spanish locale

**Expected Result:** Both query and device fail, default applied

### TC-4: Device First Priority
**Configuration:**
```json
{"enabled": true, "default": "en", "supported": ["es-ES", "fr", "en"], "detectionOrder": ["device", "query", "default"]}
```

**Test Steps:**
1. Set browser language to `es-ES` (valid)
2. Access application with `?locale=fr` (valid)
3. Verify application uses Spanish (Spain) locale

**Expected Result:** Device detection takes priority over query per configured order

### TC-5: Device First (Failed) → Query Fallback
**Configuration:**
```json
{"enabled": true, "default": "en", "supported": ["es", "fr", "en"], "detectionOrder": ["device", "query", "default"]}
```

**Test Steps:**
1. Set browser language to `de-DE` (invalid)
2. Access application with `?locale=es-MX` (valid - root supported)
3. Verify application uses Spanish (root) locale

**Expected Result:** Device fails, query used, default skipped

### TC-6: Default Only Detection
**Configuration:**
```json
{"enabled": true, "default": "es", "supported": ["es", "fr", "en"], "detectionOrder": ["default"]}
```

**Test Steps:**
1. Set browser language to `fr-FR` (valid)
2. Access application with `?locale=fr` (valid)
3. Verify application uses Spanish locale

**Expected Result:** Only default detection used, query and device completely ignored

### TC-7: Default Only with Root Fallback
**Configuration:**
```json
{"enabled": true, "default": "es-MX", "supported": ["es", "en"], "detectionOrder": ["default"]}
```

**Test Steps:**
1. Access application with any query parameters
2. Set any browser language
3. Verify application uses Spanish (root) locale

**Expected Result:** Default regional falls back to root, query/device ignored

### TC-8: Empty Detection Order (Multilingual Disabled Behavior)
**Configuration:**
```json
{"enabled": true, "default": "es", "supported": ["es", "fr", "en"], "detectionOrder": []}
```

**Test Steps:**
1. Set browser language to `es-ES` (valid)
2. Access application with `?locale=fr` (valid)
3. Verify application uses English locale

**Expected Result:** Empty detection order = multilingual disabled, always use English

### TC-9: Query Only Configuration
**Configuration:**
```json
{"enabled": true, "default": "fr", "supported": ["es", "fr", "en"], "detectionOrder": ["query"]}
```

**Test Steps:**
1. Set browser language to `es-ES` (valid)
2. Access application without query parameters
3. Verify application uses English (fallback)

**Expected Result:** Only query detection attempted, device and default skipped

### TC-10: Complex Spanish Variant Handling
**Configuration:**
```json
{"enabled": true, "default": "en", "supported": ["es-ES", "en"], "detectionOrder": ["query", "device", "default"]}
```

**Test Sequence:**
1. **Test A:** `?locale=es-MX` + device=`fr-FR` → English applied (es root not supported)
2. **Test B:** `?locale=es-ES` + device=`fr-FR` → Spanish (Spain) applied (exact match)
3. **Test C:** No query + device=`es-MX` → English applied (es root not supported)

**Expected Result:** Only exact Spanish variants supported, root fallback not allowed

### TC-11: French Root Language Support
**Configuration:**
```json
{"enabled": true, "default": "en", "supported": ["fr", "en"], "detectionOrder": ["device", "query", "default"]}
```

**Test Sequence:**
1. **Test A:** device=`fr-FR` + `?locale=es-ES` → French (root) applied
2. **Test B:** device=`fr-CA` + no query → French (root) applied
3. **Test C:** device=`es-ES` + `?locale=fr-FR` → French (root) applied

**Expected Result:** All French regional variants fall back to French root

### TC-12: Mixed English Variant Support
**Configuration:**
```json
{"enabled": true, "default": "en-GB", "supported": ["en-US", "en-GB"], "detectionOrder": ["query", "device", "default"]}
```

**Test Sequence:**
1. **Test A:** `?locale=en-GB` → English (UK) applied (exact match)
2. **Test B:** `?locale=en` → English (UK) applied (query fails, device fails, default succeeds)
3. **Test C:** device=`en-US` → English (US) applied (exact match)
4. **Test D:** device=`en-CA` → English (UK) applied (regional not supported)

**Expected Result:** Specific English variants supported, root English not explicitly supported

### TC-13: Platform Limitations with Detection Order
**Configuration:**
```json
{"enabled": true, "default": "fr", "supported": ["es", "fr", "en"], "detectionOrder": ["query", "device", "default"]}
```
**Platform Support:** ["en", "es"] (no French)

**Test Steps:**
1. Set browser language to `fr-FR` (valid for tenant)
2. Access application without query parameters
3. Verify application uses Spanish (root) locale

**Expected Result:** Device French fails platform check, falls through to default French which also fails platform check, ultimately uses English

### TC-14: All Detection Sources Valid - Order Respect
**Configuration:**
```json
{"enabled": true, "default": "fr", "supported": ["es", "fr", "en"], "detectionOrder": ["query", "device", "default"]}
```

**Test Steps:**
1. Set browser language to `fr-FR` (valid)
2. Access application with `?locale=es-MX` (valid)
3. Verify application uses Spanish (root) locale

**Expected Result:** Query takes priority despite device and default being valid

---


## Detection Order Scenarios Matrix

| Detection Order | Query | Device | Default | Result | Reason |
|----------------|-------|--------|---------|--------|---------|
| `["query", "device", "default"]` | `es-ES` | `fr-FR` | `en` | `es-ES` | Query first, valid |
| `["query", "device", "default"]` | `fr` | `es-ES` | `en` | `fr` | Query first, valid |
| `["query", "device", "default"]` | `invalid` | `es-MX` | `en` | `es` | Query fail, device root valid |
| `["query", "device", "default"]` | `invalid` | `invalid` | `fr` | `fr` | Query/device fail, default valid |
| `["device", "query", "default"]` | `es-ES` | `fr-FR` | `en` | `fr` | Device first, valid |
| `["device", "query", "default"]` | `es-ES` | `invalid` | `en` | `es-ES` | Device fail, query valid |
| `["device", "default"]` | `es-ES` | `fr-FR` | `en` | `fr` | Device first, valid |
| `["device", "default"]` | `es-ES` | `invalid` | `en-AU` | `en-AU` | Device fail, default valid |
| `["query", "default"]` | `es-ES` | `fr-FR` | `en` | `es-ES` | Query first, valid |
| `["query", "default"]` | `invalid` | `es-ES` | `en-AU` | `en-AU` | Query fail, default valid |
| `["query"]` | `es-ES` | `fr-FR` | `en` | `es-ES` | Query only, valid |
| `["query"]` | `invalid` | `fr-FR` | `en` | `en` | Query only, invalid |
| `["device"]` | `es-ES` | `fr-FR` | `fr` | `fr` | Device only, valid |
| `["device"]` | `es-ES` | `invalid` | `fr` | `en` | Device only, invalid |
| `["default"]` | `es-ES` | `fr-FR` | `fr` | `fr` | Default only, valid |
| `["default"]` | `es-ES` | `fr-FR` | `invalid` | `en` | Default only, invalid |
| `[]` | `es-ES` | `fr-FR` | `fr` | `en` | Empty order = disabled |

