# vLLMApp

A Windows desktop launcher for **vLLM**, **Hugging Face**, and **Open WebUI** — install, download, and serve large language models from a single window.

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Platform](https://img.shields.io/badge/platform-Windows%2010%2F11-lightgrey.svg)
![.NET](https://img.shields.io/badge/.NET-9.0-purple.svg)

---

## Overview

**vLLMApp** bundles three workflows that usually require separate tools, terminals, and configuration steps into one clean WinForms application:

1. **Install** vLLM inside WSL Ubuntu with a single click (automated Miniconda + conda env + pip setup).
2. **Download** Safetensors models directly from the Hugging Face Hub.
3. **Serve** any local model via vLLM and chat with it through Open WebUI.

Everything runs locally on your machine. No cloud account, no subscription, no data leaving your PC.

---

## Features

### 🌐 Browser tab
- Embedded **Microsoft WebView2** (Chromium) browser
- Address bar with Enter-to-navigate, back/forward/home/reload buttons
- Zoom in/out controls
- Page title synced to the window title
- Handles popups, downloads, and permission requests gracefully

### 🚀 vLLM tab
- **One-click install** of vLLM (GPU or CPU) inside WSL Ubuntu
- Fully automated: WSL setup → Miniconda → conda envs → pip install → Open WebUI
- **Uninstall** with one click (removes conda envs, Miniconda, and WSL distro)
- Start/stop the vLLM server with configurable options:
  - Optimization level (`-O0` to `-O3`)
  - Quantization (`awq`, `gptq`, `fp8`, `squeezellm`)
  - Max concurrent sequences, max batched tokens, log level
- **LAN access toggle** — exposes the API and chat UI to other devices on your network
- Live console output with color-coded log levels

### 🤗 Hugging Face tab
- Scans the Hugging Face Hub for **Safetensors-format** models (the format vLLM actually loads)
- Groups sharded models into a single row with total size + shard count
- **Downloads the entire model folder** — weights, config, tokenizer, chat template
- Resume support for interrupted downloads
- Filter by model family (llama, qwen, mistral, deepseek, etc.)

### ⓘ About tab
- Displays app version, .NET runtime, WebView2 runtime, and OS info
- **Copy system info** button — one click to grab a support-ready snapshot
- **Change font** — applies a new font to the entire app
- **Theme switcher** — cycles between Native (OS default), Dark, Light, and High Contrast

---

## Requirements

- **Windows 10** (version 2004+) or **Windows 11**
- **.NET 9.0 Desktop Runtime** (or run from source with the SDK)
- **WSL 2** with Ubuntu (the app can install it for you — a reboot may be required)
- **WebView2 Runtime** — pre-installed on Windows 11 and recent Windows 10 builds
- **NVIDIA GPU + driver** (optional — CPU-only mode works too, just slower)

---

## Installation

### Option A — Prebuilt binary
1. Download the latest release from the [Releases](../../releases) page.
2. Extract the ZIP anywhere.
3. Run `vLLMApp.exe`.
4. Go to the **vLLM** tab and click **Install vLLM** — the app handles everything.

### Option B — Build from source
```bash
git clone https://github.com/your-username/vLLMApp.git
cd vLLMApp
dotnet restore
dotnet build -c Release
dotnet run
