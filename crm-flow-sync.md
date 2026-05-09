# Privacy Policy – CRM Flow Sync

**Effective date: 2026-05-01**

CRM Flow Sync is a productivity utility designed to synchronize and organize CRM data entries to optimize professional workflows. Our primary goal is to enhance data consistency and user efficiency within CRM environments by streamlining manual input processes and providing a unified interface for data management.

---

## Who We Are

Developed and maintained by an individual developer for use within Salesforce OCE Lightning environments.
Contact: [johnnychiangwork@gmail.com](mailto:johnnychiangwork@gmail.com)

---

## Data the Extension Accesses

### Read from Salesforce (your own tenant)

When you run a task, the extension calls the Aura API on your Salesforce instance (`*.lightning.force.com`) to read:

- Doctor / account names and Salesforce record IDs — to create visit records
- Calendar events and availability — to find empty days
- Existing call and product records — to build and submit visits

This data is processed entirely within your browser and sent only back to your own Salesforce instance. It is never transmitted to any server operated by this extension.

### Stored in your browser

| Storage | Key | Content | Survives browser close? |
|---|---|---|---|
| `chrome.storage.local` | `productNames` | Comma-separated product names (user preference) | Yes |
| `chrome.storage.local` | `visitCount` | Number of visits to create per day (user preference) | Yes |
| `chrome.storage.session` | `task` | Task type, status, and result details during an active task | No — cleared when the task ends or the browser closes |
| `chrome.storage.session` | `taskProgress` | Progress counter (current, total, label) during an active task | No — cleared when the task ends or the browser closes |

Persistently stored data consists only of your own product name and visit count preferences. No personal identifiers are stored persistently.

---

## How Data Is Used

- Doctor names and Salesforce IDs are used solely to create and submit visit records inside your Salesforce tenant.
- Calendar data is used solely to identify empty days within your selected date range.
- Product names are used to filter available products when attaching them to visits.
- No data is used for advertising, profiling, or any purpose outside of the extension's stated automation function.

---

## Data Sharing

The extension does **not** share any data with third parties. All network requests go exclusively to `*.lightning.force.com` — your own Salesforce tenant. There are no analytics libraries, crash-reporting services, or external APIs of any kind.

---

## What the Extension Does Not Do

- Does **not** transmit data to any server other than your Salesforce tenant
- Does **not** use cookies for tracking (only your existing Salesforce session cookies are forwarded in Salesforce API calls, as required for authentication)
- Does **not** store authentication tokens, passwords, or session cookies
- Does **not** run on any website other than `*.lightning.force.com`
- Does **not** include analytics, telemetry, or crash reporting of any kind

---

## Permissions Justification

| Permission | Why it is needed |
|---|---|
| `storage` | Save user preferences (product names, visit count) and temporary task state |
| `activeTab` + `tabs` | Detect when the active tab is an OCE Lightning page; send cancellation signals to the content script by tab ID |
| `scripting` | Inject automation scripts into the Salesforce page (MAIN world) to access the Aura framework and call its API. The injected scripts only interact with Salesforce's internal framework to perform actions initiated by the user and do not exfiltrate any data. |
| `sidePanel` | Display the extension's control panel in Chrome's side panel UI |
| Host: `https://*.lightning.force.com/*` | Limit the extension's access strictly to Salesforce Lightning domains |

---

## Data Retention

User preferences are retained in `chrome.storage.local` until you uninstall the extension or clear the data manually. Session data is cleared automatically when the task ends or the browser is closed.

---

## Changes to This Policy

If this policy is updated, the effective date at the top will be revised. Continued use of the extension after any change constitutes acceptance of the updated policy.

---

## Contact

Questions or concerns: [johnnychiangwork@gmail.com](mailto:johnnychiangwork@gmail.com)
