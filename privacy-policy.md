# Privacy Policy for Flow Studio - Batch Manager

**Last updated:** April 27, 2026  
**Extension Version:** 1.2.0  
**Developer Contact:** linhbp0808@gmail.com

---

## 1. Overview

Flow Studio - Batch Manager ("Extension", "we", "us", or "our") is a Chrome browser extension that helps users manage prompts and automate content generation workflows on the Google Labs Flow platform. This Privacy Policy describes in detail what data the Extension accesses, how it is used, where it is stored, and with whom it may be shared.

**Our core principle: The Extension does not collect, transmit, or store any user data on external servers controlled by the developer. All data remains on your local device.**

---

## 2. Data We Access and Process

The following is a complete list of all types of user data the Extension accesses:

### 2.1 User-Created Content
| Data Type | Description | Purpose |
|---|---|---|
| **Prompt text** | Text descriptions you type into the Extension | Sent to Google Labs Flow to generate images/videos |
| **Reference images** | Images you upload as style/character references | Sent to Google Labs Flow alongside your prompts |
| **Generated content** | AI-generated images and videos returned by Google Labs Flow | Displayed in the Extension UI; optionally downloaded to your device |

### 2.2 User Configuration Data
| Data Type | Description | Purpose |
|---|---|---|
| **Extension settings** | Model selection, orientation, quantity, language preferences, theme | Saved locally to preserve your preferred configuration |
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
| **Clipboard content** | Text or image data from your clipboard | Read **only** when you explicitly perform a paste action within the Extension interface (e.g., pasting prompts or reference images). Never read in the background. |

### 2.5 Browser Tab Information
| Data Type | Description | Purpose |
|---|---|---|
| **Active tab URL** | URL of the currently active browser tab | Used solely to detect whether you have Google Labs Flow open, enabling the Extension to establish a connection |

---

## 3. How We Use Data

All data processing occurs **locally in your browser**. Specifically:

- **Prompt text and reference images** are used exclusively to construct and send generation requests that you explicitly initiate.
- **Extension settings and project data** are used to restore your workspace between sessions.
- **API credentials** are used only when you click a button to generate prompts via a third-party AI service. They are sent directly to the endpoint URL you specified — the developer never has access to your keys.
- **Clipboard data** is read only in response to your explicit paste action and is never stored beyond the immediate use.
- **Tab information** is used only to identify whether a Google Labs Flow tab is available for communication.

---

## 4. Data Storage

| Storage Location | Data Stored | Mechanism |
|---|---|---|
| **Local browser storage** | Settings, projects, task queues, API keys, preferences | `chrome.storage.local` (browser-native, encrypted at rest by Chrome) |
| **In-memory only** | Clipboard data, temporary image blobs during upload/merge | Discarded when the Extension is closed or the action completes |

- **No data is stored on any server controlled by the developer.**
- **Data retention:** Data persists in local storage until you manually delete it (by clearing projects, uninstalling the Extension, or clearing browser data).
- **No telemetry, analytics, crash reports, or usage metrics are collected.**

---

## 5. Data Sharing — Third Parties That Receive User Data

The Extension sends user data **only** to the following parties, and **only** when you explicitly initiate an action:

### 5.1 Google Labs Flow (`labs.google`)
| Data Sent | When |
|---|---|
| Prompt text, reference images, generation parameters | When you click "Tạo" (Generate), "Tạo tất cả" (Run All), or similar generation buttons |
| Upscale requests | When you click the upscale button on a result |

This communication occurs via script injection into the Google Labs Flow page running in your browser. The Extension automates the same actions you would perform manually on the Flow website. Data handling by Google is governed by [Google's Privacy Policy](https://policies.google.com/privacy) and [Google Labs Terms of Service](https://labs.google/tos/).

### 5.2 Google Gemini (`gemini.google.com`)
| Data Sent | When |
|---|---|
| Browser tab navigation only | When you select Gemini as the AI provider for batch prompt generation; the Extension opens or navigates to a Gemini tab |

The Extension interacts with Gemini through the browser tab interface. Data handling is governed by [Google's Privacy Policy](https://policies.google.com/privacy).

### 5.3 User-Configured Third-Party API Endpoints (Optional)
| Data Sent | When |
|---|---|
| Prompt text (in the request body), API key (in the Authorization header) | When you click "Tạo prompt" (Generate prompt) or "Bắt đầu" (Start batch) after configuring a third-party API |

**Important:** If you configure a third-party API (such as an OpenAI-compatible service or Google Gemini API), your prompt data and API key will be sent directly from your browser to the endpoint URL you provided. The developer of this Extension:
- Does **not** control, operate, or have access to these third-party services
- Does **not** act as an intermediary — requests go directly from your browser to the endpoint
- Does **not** have access to your API keys
- Cannot guarantee the privacy practices of these third-party services

### 5.4 No Other Parties
- **We do not sell, rent, trade, or share any user data with any other third parties.**
- **We do not use any advertising, analytics, or tracking services.**
- **We do not embed any third-party SDKs or scripts that collect data.**

---

## 6. Permissions Justification

The Extension requests the following Chrome permissions. Each is explained below:

| Permission | Justification |
|---|---|
| `activeTab` | Detect whether the current tab is a Google Labs Flow page to enable the Extension's connection |
| `tabs` | Query and manage browser tabs to communicate with Google Labs Flow and optionally open Gemini tabs |
| `storage` | Save Extension settings, projects, task queues, and user preferences locally |
| `unlimitedStorage` | Store large amounts of task queue data and project history (including generated image/video references) locally without hitting Chrome's default storage limits |
| `scripting` | Inject automation scripts into the Google Labs Flow page to execute generation requests, upload reference images, and retrieve results — replicating actions you would perform manually |
| `sidePanel` | Display the Extension's user interface as a Chrome Side Panel |
| `downloads` | Download generated images and videos to your device when you click the download button |
| `clipboardRead` | Read clipboard content when you explicitly paste text or images into the Extension |

### Host Permissions
| Host | Justification |
|---|---|
| `https://labs.google/*` | Communicate with the Google Labs Flow platform to execute generation workflows |
| `https://gemini.google.com/*` | Optionally interact with Google Gemini for AI-powered prompt generation |

---

## 7. User Rights and Data Control

You have full control over your data:

- **View your data:** All settings, projects, and task queues are visible within the Extension interface.
- **Export your data:** Use the "Xuất dự án JSON" (Export project JSON) feature to download your project data.
- **Delete your data:** 
  - Delete individual projects or clear the task queue from within the Extension
  - Uninstall the Extension to remove all locally stored data
  - Clear the Extension's storage via Chrome Settings → Extensions → Flow Studio → Details → "Clear storage"
- **Revoke permissions:** You can disable or uninstall the Extension at any time through Chrome's extension management page.

---

## 8. Security

- All data is stored using Chrome's built-in `chrome.storage.local` API, which is sandboxed and inaccessible to other extensions or websites.
- All communications with Google Labs Flow and third-party APIs occur over HTTPS.
- API keys are stored in browser local storage and are never transmitted to the developer.

---

## 9. Children's Privacy

The Extension is not directed at children under the age of 13 and does not knowingly collect data from children.

---

## 10. Changes to This Privacy Policy

We may update this Privacy Policy to reflect changes in the Extension's functionality or for legal compliance. The "Last updated" date at the top will be revised accordingly. We encourage you to review this policy periodically.

---

## 11. Contact Us

If you have questions, concerns, or requests regarding this Privacy Policy or your data, please contact us:

- **Email:** linhbp0808@gmail.com
- **Discord Community:** [https://discord.gg/WH2csC6ut3](https://discord.gg/WH2csC6ut3)
