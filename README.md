# WebChat.js v1.0.0

> **AI-powered website chatbot** that automatically reads your entire site and answers visitor questions in real time — no backend required.

<p align="center">
  <img src="https://img.shields.io/badge/version-1.0.0-7c3aed?style=flat-square" alt="version">
  <img src="https://img.shields.io/badge/license-MIT-00e5cc?style=flat-square" alt="license">
  <img src="https://img.shields.io/badge/zero%20dependencies-✓-22c55e?style=flat-square" alt="zero deps">
  <img src="https://img.shields.io/badge/lazy%20loaded-✓-f59e0b?style=flat-square" alt="lazy load">
  <img src="https://img.shields.io/badge/built%20by-Niloy%20Kanti%20Paul-7c3aed?style=flat-square" alt="author">
</p>

---

## ✨ What is WebChat.js?

WebChat.js is a lightweight, **production-ready** embeddable AI chatbot widget for any website. It scrapes your site content, understands context, and delivers intelligent answers using top-tier AI providers — with a robust offline fallback.

Just drop in a single `<script>` tag. No server, no database, no complex setup. **Built-in lazy loading ensures your main page load speed is never compromised.**

**Perfect for**: Portfolios, agency sites, SaaS landing pages, e-commerce, documentation, and personal brands.

---

## 🚀 Quick Start

### Option 1: Drop-in Script (Recommended)

```html
<script src="https://webchat-js.pages.dev/webchat.min.js"
  data-webchat
  data-deepseek-key="sk-XXXXXXXXXXXXXXXXXXXXXXXX"
  data-groq-key="gsk_XXXXXXXXXXXXXXXXXXXXXXXX"
  data-bot-name="Maya's Assistant"
  data-primary-color="#7c3aed"
  data-accent-color="#00e5cc"
  data-position="bottom-right"
  data-theme="auto"
  data-lazy-load="true"
  data-lazy-scrape="true"
  data-enable-popup="true">
</script>
```

### Option 2: Programmatic Initialization

```html
<script src="https://webchat-js.pages.dev/webchat.min.js"></script>
<script>
  const chat = new WebChat({
    deepseekApiKey: 'sk-xxx',
    groqApiKey:     'gsk_xxx',
    glmApiKey:      'xxx',

    botName:        "Maya's Assistant",
    primaryColor:   "#7c3aed",
    accentColor:    "#00e5cc",
    position:       "bottom-right",
    theme:          "auto",
    
    // Performance & Lazy Loading
    lazyLoad:       true,
    lazyScrape:     true,
    initDelay:      2000,
    scrapeDelay:    500,

    enablePopup:    true,
    persistConversation: true
  });
</script>
```

---

## 🤖 AI Providers & Failover

WebChat tries providers in priority order and automatically falls back if one fails.

| Provider   | Free Tier      | Speed       | Quality    | Link |
|------------|----------------|-------------|------------|------|
| **DeepSeek** | Generous      | ⚡⚡⚡       | ★★★★★     | [platform.deepseek.com](https://platform.deepseek.com) |
| **Groq**     | Yes (fast)    | ⚡⚡⚡⚡     | ★★★★☆     | [console.groq.com](https://console.groq.com) |
| **GLM-4**    | Yes           | ⚡⚡        | ★★★★☆     | [open.bigmodel.cn](https://open.bigmodel.cn) |

> **Pro tip**: You only need **one working key** to start. Smart Local Fallback ensures the bot always responds.

---

## ⚙️ Configuration Options

### Core & Theming

| Attribute                    | Type     | Default                  | Description |
|-----------------------------|----------|--------------------------|-----------|
| `data-deepseek-key`         | string   | `''`                     | DeepSeek API key (highest priority) |
| `data-groq-key`             | string   | `''`                     | Groq API key |
| `data-glm-key`              | string   | `''`                     | GLM-4 API key |
| `data-bot-name`             | string   | `'Site Assistant'`       | Chatbot display name |
| `data-primary-color`        | color    | `'#7c3aed'`              | Main brand color |
| `data-accent-color`         | color    | `'#00e5cc'`              | Accent / gradient color |
| `data-position`             | string   | `'bottom-right'`         | `bottom-right` \| `bottom-left` \| `bottom-center` |
| `data-theme`                | string   | `'auto'`                 | `light` \| `dark` \| `auto` |
| `data-bot-avatar`           | url      | `null`                   | Custom bot avatar image |

### Performance & Lazy Loading

| Attribute                      | Type      | Default | Description |
|-------------------------------|-----------|---------|-------------|
| `data-lazy-load`              | boolean   | `true`  | Defer full widget initialization until interaction or timeout |
| `data-lazy-scrape`            | boolean   | `true`  | Defer website scraping until the chat window is opened |
| `data-init-delay`             | number    | `2000`  | Delay (ms) before auto-initializing if user doesn't interact |
| `data-scrape-delay`           | number    | `500`   | Delay (ms) before scraping starts after chat is opened |

### Behavior & UX

| Attribute                      | Type      | Default | Description |
|-------------------------------|-----------|---------|-----------|
| `data-enable-popup`           | boolean   | `true`  | Contextual engagement popups |
| `data-popup-interval`         | number    | `3000`  | Popup interval (ms) |
| `data-max-popups`             | number    | `5`     | Max popups per session |
| `data-open-on-load`           | boolean   | `false` | Auto-open chat on page load |
| `data-sound-enabled`          | boolean   | `false` | Enable sound effects |
| `data-persist-conversation`   | boolean   | `true`  | Save chat history in session |
| `data-show-suggestions`       | boolean   | `true`  | Show smart suggestion chips |
| `data-show-branding`          | boolean   | `true`  | Show powered-by footer |

---

## 🎯 Key Features

- **Zero-Impact Lazy Loading** — Defers DOM building and scraping so your main page loads instantly
- **Automatic Website Scraping** — Reads current page + internal links
- **Smart Offline Fallback** — Answers questions using scraped content when APIs are unavailable
- **Sentiment-Aware Responses** — Detects urgency or frustration and adjusts tone
- **Dynamic Suggestion Chips** — Context-aware quick replies
- **Beautiful Glassmorphism UI** — Smooth animations and modern design
- **Mobile-First & Responsive**
- **Conversation Export** — Download chat as JSON
- **In-chat Controls** — Sound toggle, expand/minimize, search, clear
- **Rate Limiting & Token Tracking**

---

## 🔌 JavaScript API

```js
const chat = new WebChat({ /* options */ });

chat.open();
chat.close();
chat.toggle();
chat.send("Tell me about your services");
chat.clear();
chat.destroy();

console.log(chat.getHistory());
console.log(chat.getTokenUsage());
chat.setTheme('dark');
```

---

## 🧠 How It Works

1. **Lazy Initialization** — Script loads with zero impact. Only the toggle button is rendered initially. The full UI and scraping are deferred until the user interacts or a short timeout passes.
2. **Context Building** — Scrapes headings, sections, FAQs, contact info, and navigation (triggered exactly when needed).
3. **User Interaction** — Message → Sentiment detection → Rate limit check.
4. **AI Response** — Tries DeepSeek → Groq → GLM-4 → Smart Local Fallback.
5. **Delivery** — Typewriter animation + refreshed suggestions.

---

## 📦 Files

- `webchat.js` — Full readable source
- `webchat.min.js` — **Recommended** production build (minified & optimized)

---

## 🔐 Security & Production Notes

- API keys are client-side. For high-traffic sites, consider proxying requests through your backend.
- All output is sanitized to prevent XSS.
- Client-side rate limiting is included; pair with server-side protection if needed.
- **Performance**: Lazy loading is enabled by default (`lazyLoad: true`, `lazyScrape: true`) to guarantee zero impact on Core Web Vitals.

---

## 📄 License

**MIT License** — Free for both personal and commercial use.

---

## 👤 Author

**Niloy Kanti Paul**  
Software Engineer & AI Developer

- **Portfolio**: [https://dev-nkp.github.io/](https://dev-nkp.github.io/)
- **GitHub**: [https://github.com/dev-nkp](https://github.com/dev-nkp)
- **LinkedIn**: [linkedin.com/in/niloy-kanti-paul](https://www.linkedin.com/in/niloy-kanti-paul/)

---

<p align="center">
  Made with ❤️ for better web experiences<br>
  <strong>Star ⭐ this repo if you find it useful!</strong>
</p>
