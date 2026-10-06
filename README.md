<!-- STREAMING_CHUNK:Drafting project title, badges, and overview... -->
# KeyVerify Pro — Advanced API Key Inspector & Benchmark

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg?style=flat-square)](LICENSE)
[![Zero Backend](https://img.shields.io/badge/Architecture-100%25_Client--Side-11ff99?style=flat-square)](#security--zero-storage-model)
[![Styling: Tailwind](https://img.shields.io/badge/UI-Tailwind_CSS_CDN-3b9eff?style=flat-square)](https://tailwindcss.com)
[![Privacy: In-Memory](https://img.shields.io/badge/Storage-Zero_Persistence-ff801f?style=flat-square)](#security--zero-storage-model)

An editorial, high-performance developer sandbox designed to inspect, benchmark, and audit API keys directly in the browser without server-side relays or credential storage.

Built with pure HTML, Tailwind CSS, and vanilla JavaScript following the high-contrast **Resend developer editorial design system** (pure black `#000000` canvas, Domaine/Instrument serif typography, Geist Mono code wells, and atmospheric status glows).

---

<!-- STREAMING_CHUNK:Documenting key features and capabilities... -->
## ✨ Key Features

### 1. Dual Inspector Modes
* **Single Inspector:** Deep per-key probing with request telemetry, latency breakdown, header inspections, and live response payloads.
* **Bulk Batch Auditor:** Multi-key parallel auditor. Paste multiple keys (one per line); the engine automatically classifies provider signatures and runs concurrent evaluations with exportable **CSV** and **JSON** summaries.

### 2. Shannon Entropy & Malformation Detection
* Computes real-time Shannon Entropy (bits per character) for every input key.
* Immediately flags dummy keys, truncated copy-pastes, and low-randomness inputs before firing network requests.

### 3. Live 3-Stage Jitter Pulse Benchmarking
* Fires three sequential requests with micro-intervals to measure:
  * Minimum Latency (ms)
  * Average Round-Trip Time (ms)
  * Peak Latency (ms)
  * **Jitter Dispersion (±ms)** to gauge endpoint connectivity and stability.

<!-- STREAMING_CHUNK:Listing capability discovery and multi-language exports... -->
### 4. Deep Model & Capability Discovery
* Automatically probes downstream endpoints to surface usable permissions:
  * **Google Gemini:** Retrieves available models (`gemini-1.5-pro`, `gemini-2.0-flash`, etc.).
  * **OpenAI / Groq / DeepSeek:** Identifies authenticated model catalogs.
  * **GitHub / Hugging Face:** Extracts authenticated user handles, public repository tallies, and plan tiers.

### 5. Multi-Language Code Generator
* Live-compiles copy-paste ready boilerplates for:
  * `cURL` (CLI)
  * Python (`requests`)
  * Node.js (`fetch` / native ES modules)
  * `.env` environment variable mapping
  * One-click **Markdown Audit Report** for sharing with security or engineering teams.

### 6. Bilingual Diagnostic Intelligence
* Provides contextual status codes and troubleshooting advice in **Marathi** and **English**, explaining precise fixes for billing issues, missing scopes, rate limits, and server-side timeouts.

---

<!-- STREAMING_CHUNK:Outlining supported providers and signature detection... -->
## 🔌 Supported Providers & Auto-Detection

The application auto-detects provider formats on keystroke/paste:

| Provider | Signature Prefix | Default Probe Endpoint | Auth Mechanism |
|---|---|---|---|
| **Google Gemini** | `AIzaSy...` | `generativelanguage.googleapis.com` | URL Query (`?key=...`) |
| **Anthropic Claude** | `sk-ant-...` | `api.anthropic.com/v1/models` | Header (`x-api-key`) |
| **OpenAI** | `sk-...` | `api.openai.com/v1/models` | Bearer Token |
| **Groq Cloud** | `gsk_...` | `api.groq.com/openai/v1/models` | Bearer Token |
| **DeepSeek** | `sk-...` | `api.deepseek.com/models` | Bearer Token |
| **Mistral AI** | Any Bearer | `api.mistral.ai/v1/models` | Bearer Token |
| **GitHub PAT** | `ghp_...` / `github_pat_...` | `api.github.com/user` | Bearer Token |
| **Hugging Face** | `hf_...` | `huggingface.co/api/whoami-v2` | Bearer Token |
| **Custom Endpoint** | Any | Configurable URL | GET / POST / Custom Header |

---

<!-- STREAMING_CHUNK:Explaining the security and zero-storage model... -->
## 🔒 Security & Zero-Storage Model

KeyVerify Pro was architected to protect sensitive developer credentials:

1. **No External Backend:** All calls originate directly from your web browser sandbox. There is no middleman backend or remote database.
2. **Zero Persistent Storage:** Credentials are never written to `localStorage`, `sessionStorage`, or cookies to avoid persistent leak vectors.
3. **Session-Only Memory:** History entries are kept in ephemeral JavaScript runtime variables. A browser tab refresh wipes all session data completely.
4. **Masked Exposure:** History views and markdown export reports redact tokens (e.g., `AIzaSy...4a89`).
5. **Smart CORS Proxy Toggle:** Some providers (e.g., OpenAI) block browser-direct origin calls. A client-side opt-in proxy bypass (`corsproxy.io` / `allorigins`) can be toggled without saving credentials on the proxy host.

---

<!-- STREAMING_CHUNK:Documenting HTTP status codes and diagnostics... -->
## 📊 HTTP Status Diagnostic Matrix

| HTTP Code | Diagnostic Interpretation | Recommended Action |
|---|---|---|
| `200 OK` | Key is valid, active, and authorized. | Safe to deploy in your production `.env` / secret manager. |
| `401 Unauthorized` | Invalid, mistyped, revoked, or expired token. | Regenerate a fresh key from the provider's developer console. |
| `403 Forbidden` | Valid key lacking necessary permissions or billing. | Verify credit card/billing enablement and token scopes. |
| `429 Too Many Requests` | Free-tier exhaustion or rate limit triggered. | Wait for quota reset interval or upgrade plan concurrency. |
| `5xx Server Error` | Upstream provider outage or gateway timeout. | Check provider status page; issue is external to your key. |

---

<!-- STREAMING_CHUNK:Adding quick start and local installation steps... -->
## 🚀 Quick Start

Because KeyVerify Pro is delivered as a consolidated single-file web application, no build tools, Node runtime, or package managers are required.

### Option 1: Open Directly in Browser
Double-click `index.html` on your machine, or run:
```bash
# macOS
open index.html

# Linux
xdg-open index.html

# Windows
start index.html
```

### Option 2: Run via Local HTTP Server
```bash
# Using Python 3
python -m http.server 8000

# Using Node.js
npx serve .
```
Navigate to `http://localhost:8000` in any modern web browser.

---

<!-- STREAMING_CHUNK:Providing file structure and design system tokens... -->
## 🎨 Design System Specifications

Inspired by the Resend editorial design language:

* **Canvas:** Pure `#000000` true black.
* **Surface Elevations:**
  * `{colors.surface-deep}` (`#06060a`) — Code well background.
  * `{colors.surface-card}` (`#0a0a0c`) — Standard card elevation.
  * `{colors.surface-elevated}` (`#101012`) — Ghost controls and button surfaces.
* **Hairlines:** Translucent white borders (`rgba(255, 255, 255, 0.06)` and `0.14`) replace drop shadows.
* **Typography:**
  * Headlines: **Instrument Serif** / Domaine Display equivalent (`line-height: 1.0`, tight tracking).
  * UI Elements: **Inter** (`font-sans`).
  * Code Wells: **Geist Mono** (`font-mono`).

---

<!-- STREAMING_CHUNK:Adding contributing and licensing sections... -->
## 🤝 Contributing

Contributions to add more provider presets or enhance diagnostic rules are welcome!

1. Fork the repository.
2. Create your feature branch (`git checkout -b feature/new-provider-preset`).
3. Commit your changes (`git commit -m 'feat: Add Cohere API preset'`).
4. Push to the branch (`git push origin feature/new-provider-preset`).
5. Open a Pull Request.

---

## 📄 License

This project is open-source and released under the [MIT License](LICENSE).
