# 1 Way Heating & Air — HVAC Website + AI Lead Automation 🔧

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)
![n8n](https://img.shields.io/badge/n8n-EA4B71?style=flat-square&logo=n8n&logoColor=white)
![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)

A responsive, animated website for **1 Way Heating & Air**, built as a **sales demo** showing how a local HVAC business can capture leads automatically. It includes an FAQ chatbot, a guided service-request flow, and an n8n webhook that sends new leads to the business's CRM and Google Sheets.

> ⚠️ **Demo project.** The business details (name, phone number, ratings) are sample content for demonstration purposes. The site runs in **demo mode** until a real n8n webhook URL is configured — requests are validated and shown as received, but nothing is sent anywhere.

## ✨ Features

- 📱 **Fully responsive animated site** — mobile-first, dark/light theme support, smooth motion
- 💬 **FAQ chatbot** — answers common heating & cooling questions on-site
- 🧭 **Guided service-request flow** — collects name, phone, service type, urgency, and problem description step by step
- 🔄 **n8n lead automation** — submitted requests are validated and POSTed to an n8n webhook, which routes the lead to a CRM record and a Google Sheets log
- 🧪 **Demo mode** — with no webhook configured, the full flow works locally without sending data anywhere
- 🔍 **SEO-ready** — semantic HTML, meta descriptions, and HVACBusiness schema.org markup

## 🔀 How the Lead Flow Works

```
Visitor → Chatbot / Service-request form → n8n Webhook
                                              ├── CRM → lead record created
                                              └── Google Sheets → lead logged as "New"
```

1. A visitor opens the chatbot or the service-request flow.
2. The site validates the input (name, phone, service, urgency, problem).
3. The lead is POSTed as JSON to the configured n8n webhook URL.
4. n8n validates, routes, and logs the lead (CRM + Google Sheets).

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Frontend | HTML5, CSS3, vanilla JavaScript (single-file site) |
| Automation | n8n (webhook → CRM + Google Sheets) |
| No build step | Open `index.html` directly or serve statically |

## 🚀 Run Locally

No installation needed — it's a single static file:

```bash
# Option 1: just open index.html in a browser
# Option 2: serve it locally
npx serve .
# or
python -m http.server 8000
```

Then visit `http://localhost:8000` (or `http://localhost:3000` with `serve`).

## 🔌 Connect a Real n8n Webhook

1. In n8n, create a workflow starting with a **Webhook** node (POST) and add your CRM / Google Sheets steps.
2. Copy the webhook's **production URL**.
3. In `index.html`, find the `CONFIG` block near the top of the `<script>` section and set:

```js
const CONFIG = {
  N8N_WEBHOOK_URL: "https://your-n8n-instance/webhook/your-webhook-id",
  // ...
};
```

4. Reload the page — leads will now be sent to your workflow. Leave the URL empty to stay in demo mode.

> 💡 A matching lead-capture workflow template is available in [n8n-ai-automation-templates](https://github.com/hamidraza-bot/n8n-ai-automation-templates).

## 📁 Project Structure

```
├── index.html   # Complete site: markup, styles, chatbot & webhook logic
├── README.md
└── LICENSE
```

## 📄 License

MIT — see [LICENSE](LICENSE).

---

Built by [Hamid Raza](https://github.com/hamidraza-bot) · AI Automation Engineer · [Fiverr](https://www.fiverr.com/hamid_buildai)
