# 🚀 Claude-Code + Gemini Setup on Linux (Complete Guide)

### **Requirements**

* Linux OS (Ubuntu/Debian recommended)
* Node.js ≥ 18
* NPM
* Gemini API Key (from Google)

---

### **Step 0 — Confirm Node.js**

```bash
node --version
```

* Agar version 18+ nahi hai → install: [https://nodejs.org](https://nodejs.org)

---

### **Step 1 — Install Claude-Code & Router**

```bash
npm install -g @anthropic-ai/claude-code @musistudio/claude-code-router
```

---

### **Step 2 — Create Config Folders**

```bash
mkdir -p $HOME/.claude
mkdir -p $HOME/.claude-code-router
```

> `$HOME/.claude` usually already exists.

---

### **Step 3 — Create/Edit Router Config**

Open config.json in Vim or Nano:

```bash
vim ~/.claude-code-router/config.json
```

Paste this JSON (replace `YOUR_GEMINI_KEY` with your actual key):

```json
{
  "LOG": true,
  "LOG_LEVEL": "info",
  "HOST": "127.0.0.1",
  "PORT": 3456,
  "API_TIMEOUT_MS": 600000,
  "Providers": [
    {
      "name": "gemini",
      "api_base_url": "https://generativelanguage.googleapis.com/v1beta/models/",
      "api_key": "YOUR_GEMINI_KEY",
      "models": [
        "gemini-2.5-flash",
        "gemini-2.0-flash"
      ],
      "transformer": {
        "use": ["gemini"]
      }
    }
  ],
  "Router": {
    "default": "gemini,gemini-2.5-flash",
    "background": "gemini,gemini-2.5-flash",
    "think": "gemini,gemini-2.5-flash",
    "longContext": "gemini,gemini-2.5-flash",
    "longContextThreshold": 60000
  }
}
```

Save & exit Vim: `Esc` → `:wq` → Enter

---

### **Step 4 — Set Gemini API Key Globally**

```bash
# Temporary for current session
export GOOGLE_API_KEY="YOUR_GEMINI_KEY"

# Permanent for all sessions
echo 'export GOOGLE_API_KEY="YOUR_GEMINI_KEY"' >> ~/.bashrc
source ~/.bashrc

# Verify
echo $GOOGLE_API_KEY
```

---

### **Step 5 — Ensure No Auth Conflict**

Check for old Anthropic token:

```bash
echo $ANTHROPIC_AUTH_TOKEN
```

Unset if exists:

```bash
unset ANTHROPIC_AUTH_TOKEN
```

* Permanently remove from `~/.bashrc` if needed.

---

### **Step 6 — Start Claude-Code Router**

```bash
ccr start
```

* If already running, terminal shows: `Service is already running in the background.`

---

### **Step 7 — Run Claude**

```bash
claude
```

* Or run code analysis in a project folder:

```bash
cd /path/to/project
ccr code
```

* Type a test message:

```text
hi
```

Claude should reply using **Gemini API**.

---

### ✅ Notes / Tips

* No `/login` needed for Gemini-only setup.
* `$HOME/.claude` is mandatory; `.claude-code-router` optional for advanced routing.
* Always start `ccr start` first, then run `claude`.
* API key already set globally → can run from any directory.
* Warning about “Auth conflict” is gone once `ANTHROPIC_AUTH_TOKEN` is unset.

---
