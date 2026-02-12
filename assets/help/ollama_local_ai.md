# Local AI Setup

**Private, offline-capable AI powered by your own computer.**

Run AI models locally with Ollama, LM Studio, or any OpenAI-compatible server.

---

## What is Local AI?

Local AI runs AI models directly on your Mac/PC instead of sending data to cloud providers like OpenAI or Google. With local AI servers, Jot can:

- ✅ Generate note titles offline
- ✅ Enhance and summarize content privately
- ✅ Extract action items without network access
- ✅ Process unlimited requests at zero cost
- ✅ Keep all your data on your device

---

## Why Use Local AI?

| Feature | Cloud AI (OpenAI/Gemini) | Local AI (Ollama/LM Studio) |
|---------|--------------------------|-------------------|
| **Privacy** | Data sent to third parties | Everything stays on your device |
| **Cost** | $0.01–$0.15 per request | **$0.00** (completely free) |
| **Internet** | Required | Works offline after setup |
| **Speed** | 1–3 seconds | 0.5–2 seconds (with GPU) |
| **Model Size** | Massive (100B+ params) | Optimized (7B–8B params) |
| **Setup** | API key only | Download models, run server |

**Best for:** Desktop users who value privacy, have capable hardware, or want unlimited AI usage.

---

## Choose Your Local AI Server

Jot supports three local AI options:

| Server | Best For | Setup Difficulty | Models |
|--------|----------|------------------|--------|
| **Ollama** | CLI users, automation | Easy (terminal commands) | 100+ models |
| **LM Studio** | GUI users, beginners | Easiest (visual interface) | 1000+ models |
| **Generic OpenAI** | Advanced users, custom setups | Varies | Depends on server |

All three provide the same privacy and cost benefits. Choose based on your preference.

---

## Quick Start: Ollama (CLI)

### 1. Install Ollama

Open Terminal and run:
```bash
brew install ollama
```

Or download from [ollama.com/download](https://ollama.com/download)

### 2. Start Ollama Server

```bash
ollama serve
```

Leave this terminal window open. Ollama runs in the background.

### 3. Download a Model

In a **new** terminal window:
```bash
ollama pull phi3:mini
```

**Recommended models:**
- `phi3:mini` (2.3 GB) — Fast, great for titles/tags
- `llama3:8b` (4.7 GB) — Better quality for summaries
- `mistral:7b` (4.1 GB) — Balanced speed/quality

### 4. Configure in Jot

1. Open **Settings → AI Dashboard**
2. Tap **"Scan for Local AI Services"**
3. Jot will auto-discover Ollama at `http://localhost:11434`
4. Tap **"Use This"** to configure automatically
5. Done!

---

## Quick Start: LM Studio (GUI)

### 1. Download LM Studio

Visit [lmstudio.ai](https://lmstudio.ai) and download for your platform:
- macOS (Intel or Apple Silicon)
- Windows (10/11)
- Linux (Ubuntu, Fedora)

### 2. Install and Launch

- **macOS:** Drag to Applications folder, open LM Studio
- **Windows:** Run installer, launch from Start menu
- **Linux:** Extract archive, run `./LM-Studio`

### 3. Download a Model

1. Click **"Search"** tab in LM Studio
2. Search for `Phi-3-mini` or `Llama-3-8B`
3. Click **Download** next to your chosen model
4. Wait for download to complete (2-5 GB)

**Recommended models:**
- `Phi-3-mini-4k-instruct` (2.3 GB) — Fast, efficient
- `Llama-3-8B-Instruct` (4.7 GB) — Higher quality
- `Mistral-7B-Instruct` (4.1 GB) — Good balance

### 4. Start Local Server

1. Click **"Local Server"** tab in LM Studio
2. Select your downloaded model from dropdown
3. Click **"Start Server"**
4. Server starts at `http://localhost:1234` (default)

### 5. Configure in Jot

**Option A: Auto-Discovery (Recommended)**
1. Open **Settings → AI Dashboard** in Jot
2. Tap **"Scan for Local AI Services"**
3. Jot will find LM Studio at `http://localhost:1234`
4. Tap **"Use This"** → Done!

**Option B: Manual Configuration**
1. Open **Settings → AI Dashboard** in Jot
2. Tap **"Configure Provider"**
3. Select **"Local Server (OpenAI-Compatible)"**
4. Enter Base URL: `http://localhost:1234/v1`
5. Leave API Key blank
6. Tap **"Test Connection"**
7. If successful, tap **"Save"**

---

## Quick Start: Generic OpenAI-Compatible Server

Jot works with any server that implements the OpenAI Chat Completions API, including:
- **LocalAI** (multi-model server)
- **llama.cpp** (C++ inference)
- **text-generation-webui** (Gradio interface)
- **vLLM** (high-performance serving)
- **Ollama** (manual configuration)
- **Custom servers** implementing `/v1/chat/completions`

### Setup Steps

1. Start your OpenAI-compatible server
2. Note the Base URL (e.g., `http://localhost:8000/v1`)
3. In Jot:
   - **Settings → AI Dashboard → Configure Provider**
   - Select **"Local Server (OpenAI-Compatible)"**
   - Enter your Base URL
   - Optional: Enter API key if your server requires authentication
   - Tap **"Test Connection"**
   - Save if successful

### Endpoint Requirements

Your server must implement:
- `GET /v1/models` — List available models
- `POST /v1/chat/completions` — Generate chat responses
- Optional: `POST /v1/chat/completions` with `stream: true` — Streaming responses

---

## Quick Start (Windows/Linux) - Ollama

### Windows
1. Download installer from [ollama.com/download](https://ollama.com/download)
2. Run `ollama serve` in PowerShell
3. Open new PowerShell: `ollama pull phi3:mini`
4. Use auto-discovery in Jot or configure manually

### Linux
```bash
curl -fsSL https://ollama.com/install.sh | sh
ollama serve &
ollama pull phi3:mini
```

Then use auto-discovery in Jot.

---

## Configuration

### Auto-Discovery (Recommended)

Jot can automatically find local AI servers:

1. **Settings → AI Dashboard**
2. Tap **"Scan for Local AI Services"**
3. Wait 5-15 seconds
4. Discovered servers appear with:
   - Server name (Ollama, LM Studio, etc.)
   - URL and port
   - Available models
5. Tap **"Use This"** on your preferred server

**Scanned ports:**
- `1234` (LM Studio default)
- `8080` (common generic)
- `8000` (LocalAI, text-gen-webui)
- `11434` (Ollama default)
- `5000` (flask apps)

**Discovery checks both:**
- `127.0.0.1` (IPv4 localhost)
- `[::1]` (IPv6 localhost)

### Manual Configuration

If auto-discovery doesn't work or you have a custom setup:

1. **Settings → AI Dashboard → Configure Provider**
2. Select provider type:
   - **"Ollama"** for Ollama servers
   - **"Local Server (OpenAI-Compatible)"** for LM Studio, LocalAI, etc.
3. Enter **Base URL**:
   - Ollama: `http://localhost:11434`
   - LM Studio: `http://localhost:1234/v1`
   - Custom: Your server's URL
4. **API Key** (optional):
   - Leave blank for local servers
   - Enter if your server has authentication
5. Tap **"Test Connection"**
6. If green checkmark appears, tap **"Save"**

---

## Server URLs by Type

### Ollama
**Default:** `http://localhost:11434`

**Custom ports:**
If you run Ollama on a different port:
1. Settings → AI Dashboard → Configure Provider
2. Select "Ollama"
3. Enter `http://localhost:YOUR_PORT`
4. Tap "Test Connection"

### LM Studio
**Default:** `http://localhost:1234/v1`

**Note:** The `/v1` suffix is required for LM Studio.

**Custom ports:**
If you changed the port in LM Studio settings:
1. Check port in LM Studio → Local Server tab
2. In Jot: Settings → AI Dashboard → Configure Provider
3. Select "Local Server (OpenAI-Compatible)"
4. Enter `http://localhost:YOUR_PORT/v1`

### LocalAI
**Default:** `http://localhost:8080/v1`

### text-generation-webui
**Default:** `http://localhost:5000/v1`

**Enable API mode:** Run with `--api` flag

### llama.cpp
**Default:** `http://localhost:8080`

**Start server:**
```bash
./server -m models/your-model.gguf --port 8080
```

Then configure as "Local Server (OpenAI-Compatible)" with `http://localhost:8080/v1`

---

## Model Selection
## Model Selection

### Ollama Models
**Default:** `phi3:mini` (fastest)

**Change model:**
1. Settings → AI Dashboard → Model Selector
2. Select from dropdown (shows installed models only)
3. If model missing, download it:
   ```bash
   ollama pull llama3:8b
   ```
4. Refresh model list in Jot

### LM Studio Models
**Default:** Model you selected in LM Studio's "Local Server" tab

**Change model:**
1. **In LM Studio:**
   - Go to "Local Server" tab
   - Stop server if running
   - Select different model from dropdown
   - Click "Start Server"
2. **In Jot:**
   - Model list updates automatically
   - Select new model in Settings → AI Dashboard

### Available Models (All Servers)

| Model | Size | Speed | Quality | Best For | Works With |
|-------|------|-------|---------|----------|------------|
| `phi3:mini` / `Phi-3-mini` | 2.3 GB | ⚡️⚡️⚡️ | ⭐️⭐️⭐️ | Titles, tags, quick tasks | All servers |
| `llama3:8b` / `Llama-3-8B` | 4.7 GB | ⚡️⚡️ | ⭐️⭐️⭐️⭐️ | Summaries, content | All servers |
| `mistral:7b` / `Mistral-7B` | 4.1 GB | ⚡️⚡️ | ⭐️⭐️⭐️⭐️ | Balanced all-around | All servers |
| `gemma:7b` / `Gemma-7B` | 5.0 GB | ⚡️⚡️ | ⭐️⭐️⭐️⭐️ | Google's Gemma | All servers |
| `qwen2.5:7b` / `Qwen-2.5-7B` | 4.7 GB | ⚡️⚡️ | ⭐️⭐️⭐️⭐️ | Multilingual | All servers |

**Download models:**
- **Ollama:** `ollama pull <model-name>`
- **LM Studio:** Use built-in model search
- **Other servers:** Check server documentation

**Browse models:**
- Ollama: [ollama.com/library](https://ollama.com/library)
- LM Studio: [huggingface.co](https://huggingface.co/models?library=gguf)

---

## Using Local AI in Jot

Once configured, Local AI works **exactly like cloud AI**:

- Select text → **Enhance with AI**
- Empty note → **Generate Title**
- Long content → **Summarize**
- Meeting notes → **Extract Action Items**
- Voice notes → **Transcribe & Convert**

**The only difference:** Your data never leaves your computer.

### Provider Preference

**Prefer Local AI over Cloud:**
1. Settings → AI Dashboard
2. Enable **"Prefer Local AI"**
3. Jot tries local server first, falls back to cloud if needed

**Benefits:**
- Maximum privacy when local server available
- Automatic fallback ensures reliability
- Save on cloud API costs

---

## Troubleshooting

### General: "Cannot connect to server"

**Check server is running:**
- **Ollama:** Terminal shows "Ollama is running"
- **LM Studio:** "Server Running" status in Local Server tab
- **Other:** Check server logs/console

**Test connection manually:**
```bash
# Ollama
curl http://localhost:11434/api/tags

# LM Studio or OpenAI-compatible
curl http://localhost:1234/v1/models

# Should return JSON, not error
```

**Fix:**
1. Stop and restart server
2. Check firewall isn't blocking localhost
3. Verify port number matches Jot configuration
4. Try auto-discovery: Settings → AI Dashboard → "Scan for Local AI"

---

### Ollama: "Server not running"

**Fix 1:** Start server
```bash
# Ollama
ollama serve

# LM Studio: Click "Start Server" in Local Server tab
```

**Fix 2:** Check if already running
```bash
# macOS/Linux (Ollama)
ps aux | grep ollama

# Windows (Ollama)
tasklist | findstr ollama

# LM Studio: Look for "Server Running" status
```

**Fix 3:** Restart server
```bash
# Ollama
killall ollama
ollama serve

# LM Studio: Stop → Start in Local Server tab
```

---

### LM Studio: "Model not loaded"

**Fix:** Select and load model
1. Open LM Studio
2. Go to "Local Server" tab
3. Select model from dropdown
4. Click "Start Server" or "Reload Model"
5. Wait for "Model loaded successfully" message

**If model not in list:**
1. Go to "Search" tab
2. Download model (e.g., `Phi-3-mini-4k-instruct`)
3. Return to "Local Server" tab
4. Select newly downloaded model

---

### "Model not found" or "No models available"

**Fix (Ollama):** Download the model
```bash
ollama pull phi3:mini
```

**Fix (LM Studio):** Download via Search tab

**Check installed models:**
```bash
# Ollama
ollama list

# LM Studio: Check "My Models" tab

# OpenAI-compatible:
curl http://localhost:YOUR_PORT/v1/models
```

---

### "Connection refused" or wrong port

**Check server URL matches:**
| Server | Expected URL in Jot |
|--------|---------------------|
| Ollama | `http://localhost:11434` |
| LM Studio | `http://localhost:1234/v1` |
| LocalAI | `http://localhost:8080/v1` |
| Custom | Your server's URL |

**Steps:**
1. Settings → AI Dashboard → Configure Provider
2. Verify Base URL matches table above
3. For LM Studio: Check port in Local Server tab
4. Tap "Test Connection"
5. If fails, try auto-discovery

**Test manually:**
```bash
# Ollama
curl http://localhost:11434/api/tags

# LM Studio or OpenAI-compatible  
curl http://localhost:1234/v1/models
```

---

### Slow Performance (All Servers)

**Cause:** Large model + no GPU acceleration

**Fix 1:** Use smaller/faster model
```bash
# Ollama
ollama pull phi3:mini  # Only 2.3 GB

# LM Studio: Download Phi-3-mini-4k-instruct (2.3 GB)
```

**Fix 2:** Enable GPU acceleration
- **macOS:** Works automatically on M1/M2/M3/M4 chips
- **Windows/Linux:** Install CUDA drivers for NVIDIA GPUs
- Check GPU usage:
  - macOS: Activity Monitor → GPU tab
  - Windows/Linux: `nvidia-smi`

**Fix 3:** Use quantized models (LM Studio)
- Look for models with `Q4_K_M` or `Q5_K_M` in name
- Example: `Llama-3-8B-Instruct-Q4_K_M.gguf`
- Much faster with minimal quality loss

**Fix 4 (Ollama):** Increase thread count
Edit `~/.ollama/config.json`:
```json
{
  "num_thread": 8
}
```

**Fix 5 (LM Studio):** Adjust settings
1. Local Server tab → Settings icon
2. Increase "n_threads" to CPU core count
3. Enable "Use GPU" if available
4. Restart server

---

### Out of Memory Errors

**Fix 1:** Use smaller model
- Try `phi3:mini` (2.3 GB) instead of `llama3:8b` (4.7 GB)

**Fix 2:** Use more aggressive quantization
- LM Studio: Look for `Q3_K_M` or `Q4_K_M` models
- Ollama: Try model variants with `-q4` suffix

**Fix 3:** Close other applications
- Free up RAM before starting local AI server
- Check Activity Monitor / Task Manager

**Fix 4 (Advanced):** Reduce context length
- LM Studio: Local Server → Settings → Reduce "n_ctx" from 4096 to 2048
- Trade-off: shorter context window, but less memory usage

---

## Privacy & Security

### What Data Stays Local?

✅ **All note contents** — Never sent to cloud  
✅ **All AI prompts** — Processed on your device  
✅ **All AI responses** — Generated locally  
✅ **Model weights** — Stored locally
- Ollama: `~/.ollama/models/`
- LM Studio: `~/.cache/lm-studio/models/`

### What Data Leaves Your Device?

❌ **Nothing** (when using `http://localhost:*` or `http://127.0.0.1:*`)

### Remote Servers (Warning)

⚠️ **Caution:** If you configure a remote server (e.g., `http://192.168.1.10:1234`), note contents **will be sent over your network**.

**Only use remote servers if:**
- You control the server (your own machine on LAN)
- You trust the network (home network, VPN)
- You understand privacy implications

**Jot will warn you** when configuring a remote (non-localhost) URL.

### Authentication

**Local servers (localhost):**
- API Key field can be left blank
- No authentication needed for `127.0.0.1` or `localhost`

**Remote servers:**
- Set API Key if your server requires authentication
- Check server documentation for key format

---

## Advanced Usage (Ollama)

### Running as a Service (macOS)

```bash
# Create launch agent
mkdir -p ~/Library/LaunchAgents
cat > ~/Library/LaunchAgents/com.ollama.server.plist << EOF
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
  <key>Label</key>
  <string>com.ollama.server</string>
  <key>ProgramArguments</key>
  <array>
    <string>/opt/homebrew/bin/ollama</string>
    <string>serve</string>
  </array>
  <key>RunAtLoad</key>
  <true/>
  <key>KeepAlive</key>
  <true/>
</dict>
</plist>
EOF

# Load service
launchctl load ~/Library/LaunchAgents/com.ollama.server.plist
```

Ollama now starts automatically on login.

---

### Custom Model Configuration

Create a `Modelfile`:
```
FROM llama3:8b
PARAMETER temperature 0.7
PARAMETER top_p 0.9
SYSTEM You are a helpful note-taking assistant.
```

Build custom model:
```bash
ollama create jot-assistant -f Modelfile
```

Use in Jot:
1. Settings → AI Dashboard → Model
2. Select "jot-assistant"

---

### Monitoring Performance

```bash
# Watch resource usage
ollama ps

# Check model details
ollama show phi3:mini

# View logs
tail -f ~/.ollama/logs/server.log
```

---

## System Requirements

### Minimum
- **CPU:** 4-core Intel/AMD or Apple M1
- **RAM:** 8 GB
- **Disk:** 5 GB free (for one model)
- **OS:** macOS 11+, Windows 10+, Linux (64-bit)

### Recommended
- **CPU:** 8-core or M1/M2/M3 chip
- **RAM:** 16 GB
- **GPU:** NVIDIA RTX 3060+ or Apple Silicon
- **Disk:** 20 GB free (for multiple models)

---

## Cost Comparison

### 1000 AI Requests (typical monthly usage)

| Provider | Cost per Request | Total Cost |
|----------|------------------|------------|
| **Ollama** | $0.00 | **$0.00** |
| OpenAI GPT-4 | $0.15 | $150.00 |
| Anthropic Claude | $0.10 | $100.00 |
| Google Gemini | $0.05 | $50.00 |

**Annual savings:** $600–$1,800 by using Local AI

---

## FAQ

### Can I use both Local and Cloud AI?

Yes! Switch providers in Settings → AI Dashboard.

### Which is better for me?

**Choose Local AI if:**
- Privacy is a priority
- You have a capable Mac/PC (M1+ or 16GB+ RAM)
- You use AI features frequently (dozens of times/day)
- You work offline occasionally

**Choose Cloud AI if:**
- You need best-in-class quality (GPT-4, Claude)
- Your hardware is limited (8GB RAM, older CPU)
- You rarely use AI (a few times/week)

### Can I switch models mid-session?

Yes! Change model in settings and it applies immediately.

### Do I need internet after setup?

No. Once models are downloaded, Ollama works 100% offline.

### How do I uninstall?

```bash
# macOS
brew uninstall ollama
rm -rf ~/.ollama

# Windows
# Uninstall via Add/Remove Programs
# Delete %USERPROFILE%\.ollama

# Linux
sudo rm /usr/local/bin/ollama
rm -rf ~/.ollama
```

---

## Getting Help

### Ollama Resources
- **Website:** [ollama.com](https://ollama.com)
- **Docs:** [github.com/ollama/ollama](https://github.com/ollama/ollama)
- **Discord:** [ollama.com/discord](https://ollama.com/discord)

### Jot Support
- **Settings → Feedback** — Report issues
- **Settings → Help → AI Features** — General AI guide

---

## Quick Reference Commands

```bash
# Installation
brew install ollama                  # macOS
curl -fsSL https://ollama.com/install.sh | sh  # Linux

# Server
ollama serve                         # Start server
ollama ps                            # Check running models

# Models
ollama list                          # List installed models
ollama pull phi3:mini                # Download model
ollama rm mistral:7b                 # Remove model
ollama show llama3:8b                # Model details

# Testing
ollama run phi3:mini "Hello!"        # Test model
curl http://localhost:11434/api/tags # Check server
```

---

**Last Updated:** 2026-01-12  
**Jot Version:** 1.0.10+
