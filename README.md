

````markdown
# 🚀 Gemini CLI Setup & MCP Configuration

```bash
# Uninstall existing Gemini CLI (if any)
sudo npm uninstall -g @google/gemini-cli

# Install Gemini CLI globally
sudo npm install -g @google/gemini-cli

# Verify Gemini CLI installation
gemini

# Navigate to Gemini configuration folder
cd ~/.gemini

# List files inside the folder
ls
````

# MCP JSON Configuration Example

1. Go to GitHub → **Settings** → **Developer settings** → **Personal access tokens** → **Generate new token**
2. Open the Gemini settings file in Vim:

```bash
vim settings.json
```

3. Paste/update the following JSON configuration:

```json
{
  "ide": {
    "enabled": true,
    "hasSeenNudge": true
  },
  "security": {
    "auth": {
      "selectedType": "oauth-personal"
    }
  },
  "mcpServers": {
    "github": {
      "httpUrl": "https://api.githubcopilot.com/mcp/",
      "headers": {
        "Authorization": "your_github_personal_access_token_here"
      },
      "timeout": 5001
    }
  }
}
```

> 💡 Tip: Replace `"your_github_personal_access_token_here"` with your actual GitHub PAT.

---

# Vim Paste & Save Instructions

1️⃣ **Normal mode me aana**
Press `Esc` (Vim normal mode me aa jaayega)

2️⃣ **File save karna**
Type:

```vim
:w
```

Press `Enter` → Ye file save kar dega

3️⃣ **File save karke exit karna**
Type:

```vim
:wq
```

Press `Enter` → File save ho jaayegi aur Vim close ho jaayega

4️⃣ **Save kiye bina exit karna**
Type:

```vim
:q!
```

Press `Enter` → Vim close ho jaayega bina save kiye

```
Kya mai wo add kar doon?
```
