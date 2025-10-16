# 🚀 Ollama WebUI with Docker Compose

[![GitHub Repo](https://img.shields.io/badge/GitHub-Repo-blue?logo=github)](https://github.com/amrmarey/ollama-webui)
[![Docker Compose](https://img.shields.io/badge/Docker-Compose-green?logo=docker)](https://docs.docker.com/compose/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Ollama](https://img.shields.io/badge/Ollama-AI%20Models-purple?logo=python)](https://ollama.com)
[![Open WebUI](https://img.shields.io/badge/Open%20WebUI-Chat%20Interface-orange?logo=react)](https://github.com/open-webui/open-webui)

> **Run Large Language Models (LLMs) locally with a beautiful, browser-based WebUI using Docker Compose — persistent, GPU-ready, and developer-friendly.**

---

## ✨ Overview

This project provides a **modern Docker Compose setup** for running [Ollama](https://ollama.com/) integrated with [Open WebUI](https://github.com/open-webui/open-webui) (formerly “Ollama WebUI”).  
Ollama runs open-source LLMs locally, while Open WebUI provides a fast, intuitive chat interface.

It’s perfect for:
- 🧠 AI developers & researchers  
- 💬 Self-hosted chatbot enthusiasts  
- 🔐 Privacy-focused AI environments  
- 💻 Local model testing  

---

## 🌟 Features

- 🛠️ **One-command deployment** with Docker Compose  
- 💾 **Persistent volumes** for models and data  
- ⚡ **Automatic NVIDIA GPU acceleration** (if available)  
- 🔐 **Optional HTTPS & Authentication**  
- 🧠 **Cross-platform:** Linux, macOS, Windows  
- 🔄 **API access** for integrations and automation  

---

## 🧱 Prerequisites

| Requirement | Version | Purpose |
|--------------|----------|----------|
| [Docker](https://docs.docker.com/get-docker/) | ≥ 20.10 | Container runtime |
| [Docker Compose](https://docs.docker.com/compose/install/) | ≥ 2.0 | Orchestration |
| (Optional) NVIDIA GPU | — | For accelerated inference |
| [NVIDIA Container Toolkit](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html) | — | GPU runtime |

💡 **Recommendation:** 8GB+ RAM for small models, 16GB+ for larger ones.

---

## ⚙️ Quick Start

### 1️⃣ Clone the Repository
```bash
git clone https://github.com/amrmarey/ollama-webui.git
cd ollama-webui
```

### 2️⃣ Start the Services
```bash
docker compose up -d
```

### 3️⃣ Access the WebUI
- Open [http://localhost:3000](http://localhost:3000)
- Create your admin account on first login

### 4️⃣ Pull a Model
```bash
docker compose exec ollama ollama pull llama3
```

### 5️⃣ Start Chatting 🎉  
Choose a model from the WebUI and start interacting.

### 6️⃣ Stop the Services
```bash
docker compose down
```

---

## ⚙️ Configuration

### Environment Variables
| Variable | Default | Description |
|-----------|----------|-------------|
| `OLLAMA_HOST` | `0.0.0.0:11434` | Ollama API endpoint |
| `WEBUI_PORT` | `3000` | WebUI exposed port |
| `OLLAMA_MODELS_PATH` | `./models` | Model storage path |
| `WEBUI_DATA_PATH` | `./webui-data` | WebUI persistent data |

Example `.env` file:
```bash
WEBUI_PORT=8080
OLLAMA_MODELS_PATH=/opt/ollama/models
```

---

## ⚡ GPU Acceleration

Enable GPU mode:
```bash
docker compose --profile gpu up -d
```
> ✅ Ensure `nvidia-smi` works and `nvidia-container-toolkit` is installed.

---

## 🔒 HTTPS & Authentication

For secure production use:
```bash
WEBUI_HTTPS_ENABLED=true
WEBUI_SSL_CERT_PATH=/path/to/cert.pem
WEBUI_SSL_KEY_PATH=/path/to/key.pem
```

For user authentication, see [Open WebUI Docs](https://github.com/open-webui/open-webui#readme).

---

## 🧩 Usage

### 🧠 Interacting with Models
#### Via WebUI
Chat, view model list, and manage conversations.

#### Via CLI
```bash
docker compose exec ollama ollama run llama3 "Hello, world!"
```

### 🔌 API Access
- Ollama API → [http://localhost:11434](http://localhost:11434)  
- WebUI API → [http://localhost:3000/api](http://localhost:3000/api)

---

## 🧰 Managing Models

| Action | Command |
|--------|----------|
| List models | `docker compose exec ollama ollama list` |
| Pull model | `docker compose exec ollama ollama pull llama3` |
| Remove model | `docker compose exec ollama ollama rm <model-name>` |

Models persist under `./models`.

---

## 🪶 Logs & Debugging

```bash
docker compose logs -f ollama   # Ollama logs
docker compose logs -f webui    # WebUI logs
```

### Common Issues
| Issue | Fix |
|-------|-----|
| Port conflict | Change ports in `.env` |
| GPU not detected | Verify NVIDIA drivers & toolkit |
| Out of memory | Use smaller models (7B or below) |
| Permission denied | `docker compose down -v && docker compose up -d` |

---

## 🧠 Supported Models

| Model | Developer | Description |
|--------|------------|-------------|
| **Llama 3** | Meta | General-purpose chat & code |
| **Mistral** | Mistral AI | Small and efficient |
| **Phi-3** | Microsoft | Lightweight and accurate |
| **Gemma** | Google | Excellent reasoning capabilities |

🔗 Explore more on [Ollama Library](https://ollama.com/library)

---

## 🤝 Contributing

Contributions are welcome!

1. Fork the repo  
2. Create a branch:  
   ```bash
   git checkout -b feature/amazing-feature
   ```
3. Commit changes:  
   ```bash
   git commit -m "Add amazing feature"
   ```
4. Push and open a Pull Request  

🧩 Please follow the [Code of Conduct](./CODE_OF_CONDUCT.md) and ensure all tests pass.

---

## 📄 License

Licensed under the **MIT License** — see [LICENSE](./LICENSE).

---

## 💬 Contact

Maintainer: **[Amr Marey](mailto:amr.marey@msn.com)**  
Built with ❤️ in Egypt 🇪🇬  
_Last updated: October 2025_

---

### 🧭 Keywords (SEO)
`ollama`, `ollama webui`, `docker compose`, `open webui`, `llama3`, `local llm`, `ai chat`, `self hosted ai`, `gpu inference`, `open source ai`, `ollama docker`, `open-webui docker compose`, `llm docker setup`
