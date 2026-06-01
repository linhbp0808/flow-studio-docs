# Privacy Policy for Flow Studio - Batch Manager

**Last updated:** June 2, 2026
**Extension Version:** 1.5.0
**Developer Contact:** linhbp0808@gmail.com

---

## 1. Overview

Flow Studio - Batch Manager ("Extension") is a Chrome browser extension that helps users manage prompts and automate content generation workflows on the Google Labs Flow platform. This Privacy Policy describes what data the Extension accesses, how it is used, where it is stored, and with whom it may be shared.

**Our core principles:** The Extension uses no analytics, ads, tracking, or data selling. Your settings and any API keys you enter are stored only on your local device and are never sent to the developer. During normal side-panel use, your content stays between your browser and the services you direct it to (Google Labs Flow / Gemini, under your own account). The **only** developer-operated server involved is the optional companion Prompt Studio backend: if you choose to use that web app, the prompts and reference images you submit there are sent to it solely to generate prompts (see Section 6.4).

---

## 2. Data We Access and Process

### 2.1 User-Created Content

| Data Type | Description | Purpose |
|---|---|---|
| **Prompt text** | Text descriptions you type into the Extension | Sent to Google Labs Flow to generate images/videos |
| **Reference images** | Images you upload as style/character references | Sent to Google Labs Flow alongside your prompts |
| **Generated content** | AI-generated images and videos returned by Google Labs Flow | Displayed in the Extension UI; optionally downloaded to your device |

### 2.2 User Configuration Data

| Data Type | Description | Purpose |
|---|---|---|
| **Extension settings** | Model selection, orientation, quantity, language preferences, theme, music presets | Saved locally to preserve your preferred configuration |
| **Project data** | Named project containers with associated task queues and results | Saved locally for workflow organization |
| **Task queue** | List of prompts and their generation status/results | Saved locally to track batch generation progress |

### 2.3 API Credentials (User-Provided, Optional)

| Data Type | Description | Purpose |
|---|---|---|
| **Third-party API keys** | API keys for services such as OpenAI-compatible endpoints or Google Gemini API | Stored locally in your browser; used only to make direct API calls to endpoints you configure |
| **API endpoint URLs** | Base URLs for third-party AI services you configure | Stored locally; used to route prompt generation requests |
| **API model names** | AI model identifiers you specify | Stored locally; included in API requests you initiate |

### 2.4 Clipboard Data

| Data Type | Description | Purpose |
|---|---|---|
| **Clipboard content** | Text or image data from your clipboard | Read **only** when you explicitly perform a paste action within the Extension interface. Never read in the background. |

### 2.5 Browser Tab Information

| Data Type | Description | Purpose |
|---|---|---|
| **Active tab URL** | URL of the currently active browser tab | Used solely to detect whether you have Google Labs Flow open |

---

## 3. Remote Configuration Updates

The Extension periodically fetches a UI configuration file (`flow-selectors.json`) from GitHub (`raw.githubusercontent.com`) to maintain compatibility with Google Labs Flow interface changes and to update configurable content such as contact links.

| Detail | Value |
|---|---|
| **What is fetched** | A JSON configuration file containing UI selectors, contact menu links, feature URLs, and the list of companion Prompt Studio domains where the relay bridge may be injected |
| **User data sent** | None — this is a one-way download with no user data transmitted |
| **Cache duration** | Up to 1 hour (stored in `chrome.storage.local`) |
| **Fallback** | Built-in default values are used if the fetch fails |

This mechanism allows the developer to fix compatibility issues and update links without requiring users to reinstall the Extension. No executable code is ever downloaded or run — the file contains data only. Bridge injection is limited to the Extension's declared host permissions, so this file cannot cause injection into arbitrary websites.

---

## 4. How We Use Data

Most user data processing occurs **locally in your browser** (the only exception is the optional companion Prompt Studio backend — see Section 6.4):

- **Prompt text and reference images** are used exclusively to construct generation requests you explicitly initiate.
- **Extension settings and project data** are used to restore your workspace between sessions.
- **API credentials** are used only when you click a button to generate prompts via a third-party AI service. They are sent directly to the endpoint you specified — the developer never has access to your keys.
- **Clipboard data** is read only in response to your explicit paste action and is never stored beyond immediate use.
- **Tab information** is used only to identify whether a Google Labs Flow tab is available.

---

## 5. Data Storage

| Storage Location | Data Stored | Mechanism |
|---|---|---|
| **Local browser storage** | Settings, projects, task queues, API keys, preferences, remote config cache | `chrome.storage.local` |
| **In-memory only** | Clipboard data, temporary image blobs during upload/merge | Discarded when the action completes |

- During normal side-panel use, no user data is stored on developer-operated servers. If you use the optional companion Prompt Studio web app, the content you submit there is processed by a developer-operated backend to generate prompts, and — if you sign in — your account email is stored to identify your account (see Section 6.4).
- **No telemetry, analytics, crash reports, or usage metrics are collected.**

---

## 6. Data Sharing — Third Parties That Receive User Data

### 6.1 Google Labs Flow (`labs.google`)

Prompt text, reference images, and generation parameters — sent when you click Generate or Run All. Data handling by Google is governed by [Google's Privacy Policy](https://policies.google.com/privacy) and [Google Labs Terms of Service](https://labs.google/tos/).

### 6.2 Google Gemini (`gemini.google.com`)

Prompt text and reference images — when Gemini is used as the AI provider (including through the in-browser relay), your prompts and any reference images are sent to your own logged-in Gemini session to produce the text/analysis used for prompt generation. Data handling is governed by [Google's Privacy Policy](https://policies.google.com/privacy).

### 6.3 User-Configured Third-Party API Endpoints (Optional)

Prompt text and API key — sent directly from your browser to the endpoint URL you configured. The developer does not act as an intermediary and has no access to your API keys or the data processed by those services.

### 6.4 Companion Prompt Studio Backend (`promptveo.spam.pro.vn`) — Optional, Developer-Operated

This applies **only if you choose to use the optional companion Prompt Studio web app.** When you do, the prompts and reference images you submit there are sent to a backend operated by the developer to build cinematic prompts, and the Extension relays these requests through your browser (for example, to your own in-browser Gemini session). If you sign in with Google Sign-In, your email address is used to identify your account and save your work; the developer does not receive your Google password. This content is used solely to provide the prompt-generation feature and is **not** sold, rented, or used for advertising. The Extension's core side-panel features do not require or use this server.

### 6.5 GitHub (`raw.githubusercontent.com`)

No user data is sent. The Extension only downloads a read-only configuration JSON file from this address to update UI selectors, links, and the list of companion Prompt Studio domains.

### 6.6 No Other Parties

- We do not sell, rent, trade, or share any user data with any other third parties.
- We do not use any advertising, analytics, or tracking services.
- We do not embed any third-party SDKs or scripts that collect data.

---

## 7. Permissions Justification

| Permission | Justification |
|---|---|
| `activeTab` | Detect whether the current tab is a Google Labs Flow page to enable the Extension's connection |
| `tabs` | Query and manage browser tabs to communicate with Google Labs Flow and optionally open Gemini tabs |
| `storage` | Save Extension settings, projects, task queues, remote config cache, and user preferences locally |
| `unlimitedStorage` | Store large amounts of task queue data and project history locally without hitting Chrome's default storage limits |
| `scripting` | Inject automation scripts into the Google Labs Flow page to execute generation requests, upload reference images, and retrieve results |
| `sidePanel` | Display the Extension's user interface as a Chrome Side Panel |
| `downloads` | Download generated images and videos to your device when you click the download button |
| `clipboardRead` | Read clipboard content when you explicitly paste text or images into the Extension |

### Host Permissions

| Host | Justification |
|---|---|
| `https://labs.google/*` | Communicate with the Google Labs Flow platform to execute generation workflows |
| `https://gemini.google.com/*` | Optionally interact with Google Gemini for AI-powered prompt generation |
| `https://raw.githubusercontent.com/*` | Fetch the UI configuration file for compatibility updates and link management |
| `https://*.spam.pro.vn/*` | Communicate with the optional companion Prompt Studio web app and the developer's prompt-generation backend, which run on subdomains of spam.pro.vn (e.g., `promptveo.`, `llm-direct.`), to build prompts and relay requests |
| `http://localhost/*`, `http://127.0.0.1/*` | Allow running the Prompt Studio backend locally for development and self-hosting |

---

## 8. User Rights and Data Control

You have full control over your data:

- **View your data:** All settings, projects, and task queues are visible within the Extension interface.
- **Export your data:** Use the "Xuất dự án JSON" (Export project JSON) feature to download your project data.
- **Delete your data:** Delete individual projects or clear the task queue from within the Extension, or uninstall the Extension to remove all locally stored data.
- **Revoke permissions:** Disable or uninstall the Extension at any time through Chrome's extension management page.

---

## 9. Security

- All data is stored using Chrome's built-in `chrome.storage.local` API, which is sandboxed and inaccessible to other extensions or websites.
- All external communications occur over HTTPS.
- API keys are stored in browser local storage and are never transmitted to the developer.

---

## 10. Children's Privacy

The Extension is not directed at children under the age of 13 and does not knowingly collect data from children.

---

## 11. Changes to This Privacy Policy

We may update this Privacy Policy to reflect changes in the Extension's functionality or for legal compliance. The "Last updated" date at the top will be revised accordingly. We encourage you to review this policy periodically.

---

## 12. Contact Us

If you have questions, concerns, or requests regarding this Privacy Policy or your data, please contact us:

- **Email:** linhbp0808@gmail.com
- **Discord Community:** [https://discord.gg/WH2csC6ut3](https://discord.gg/WH2csC6ut3)
