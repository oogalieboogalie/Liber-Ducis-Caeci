# 🛠️ How to Set Up n8n

> A beginner-friendly guide to getting n8n installed and running on your machine.

---

## Visual Walkthrough

<img src="./assets/n8n_setup_visual_guide.png" alt="Visual step-by-step guide for setting up n8n" width="100%"/>

---

## Step-by-Step (Windows)

### 1. Install Node.js

n8n runs on Node.js. If you don't have it:

1. Go to [https://nodejs.org](https://nodejs.org)
2. Download the **LTS** version (recommended)
3. Run the installer — click **Next** through the prompts
4. ✅ Make sure "Add to PATH" is checked

### 2. Install n8n

Open a terminal (PowerShell or Command Prompt) and run:

```bash
npm install -g n8n
```

> 💡 **Alternative (Chocolatey):** If you use Chocolatey, you can also install via:
> ```bash
> choco install n8n
> ```

### 3. Start n8n

```bash
n8n start
```

This will launch n8n and give you a local URL (usually `http://localhost:5678`).

### 4. Open in Browser

Navigate to the URL in your browser. You'll be prompted to:
- Create an account (local, stays on your machine)
- Set a password

### 5. You're In! 🎉

You now have one of the best automation tools available — completely free.

---

## What's Next?

- **Import workflows** from this repo → `Add Workflow` → `Import from File`
- Check out the [QB Autopilot Suite](../QB_Autopilot_Suite/) for a full automation system
- Explore the [n8n docs](https://docs.n8n.io/) for more

---

## Other Install Methods

| Method | Command / Link |
|:-------|:---------------|
| **npm** (recommended) | `npm install -g n8n` |
| **Docker** | `docker run -it --rm -p 5678:5678 n8nio/n8n` |
| **Chocolatey** | `choco install n8n` |
| **n8n Cloud** | [n8n.io/cloud](https://n8n.io/cloud) (hosted, no install needed) |

---

*Part of the [Liber Ducis Caeci](../) workflow library.*
