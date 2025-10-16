# Ollama WebUI with Docker Compose

[![GitHub Repo](https://img.shields.io/badge/GitHub-Repo-blue?logo=github)](https://github.com/amrmarey/ollama-webui)
[![Docker](https://img.shields.io/badge/Docker-Compose-green?logo=docker)](https://docs.docker.com/compose/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

This repository provides an enhanced Docker Compose setup for running [Ollama](https://ollama.com/) integrated with [Open WebUI](https://github.com/open-webui/open-webui) (formerly Ollama WebUI). Ollama is a lightweight tool for running large language models (LLMs) locally, and Open WebUI offers a user-friendly chat interface to interact with those models.

This setup simplifies deployment, making it easy to spin up a local AI chat environment with persistent data storage, GPU acceleration support (if available), and easy model management. It's ideal for developers, researchers, and enthusiasts wanting to experiment with LLMs without complex configurations.

## Features

- **Easy Deployment**: One-command setup using Docker Compose.
- **Persistent Storage**: Volumes for Ollama models and Open WebUI data to avoid re-downloading on restarts.
- **GPU Support**: Automatic NVIDIA GPU detection for accelerated inference.
- **Model Management**: Pull, run, and manage LLMs directly via the WebUI.
- **Secure Access**: Optional authentication and HTTPS support (configurable).
- **Scalable**: Easily extend with additional services like databases or monitoring.
- **Cross-Platform**: Works on Linux, macOS, and Windows with Docker Desktop.

## Prerequisites

- [Docker](https://docs.docker.com/get-docker/) installed and running (version 20.10+).
- [Docker Compose](https://docs.docker.com/compose/install/) (version 2.0+).
- For GPU support: NVIDIA GPU with [NVIDIA Container Toolkit](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html) installed.
- At least 8GB RAM recommended for running small models; more for larger ones.

## Quick Start

1. Clone this repository (or copy the `docker-compose.yml` file):
   ```bash
   git clone https://github.com/amrmarey/ollama-webui.git
   cd ollama-webui


Start the services:
docker compose up -d


Access the WebUI:

Open your browser and go to http://localhost:3000.
On first login, create an admin account.


Pull a model in the WebUI (e.g., Llama 3) or via CLI:
docker compose exec ollama ollama pull llama3


Start chatting! Select the model and interact in the interface.


To stop the services:
docker compose down

Configuration
The docker-compose.yml file is pre-configured for basic use. Customize it as needed:
Environment Variables

OLLAMA_HOST: Set to 0.0.0.0:11434 for WebUI access (default).
WEBUI_PORT: Change the exposed port (default: 3000).
OLLAMA_MODELS_PATH: Path for model storage (default: ./models).
WEBUI_DATA_PATH: Path for WebUI data (default: ./webui-data).

Example override in a .env file:
WEBUI_PORT=8080
OLLAMA_MODELS_PATH=/path/to/your/models

GPU Acceleration
If you have an NVIDIA GPU, ensure the toolkit is installed and run:
docker compose --profile gpu up -d

This uses the nvidia runtime automatically.
HTTPS and Authentication
For production:

Set WEBUI_HTTPS_ENABLED=true and provide cert/key paths.
Configure user auth via environment vars (see Open WebUI docs).

Usage
Interacting with Models

Via WebUI: Browse models, start chats, manage history, and fine-tune prompts.
Via Ollama CLI: Exec into the container:docker compose exec ollama ollama run llama3 "Hello, world!"


API Access: Ollama API at http://localhost:11434, WebUI API at http://localhost:3000/api.

Managing Models

List models: docker compose exec ollama ollama list
Remove model: docker compose exec ollama ollama rm <model-name>
Models are stored in the ./models volume for persistence.

Logs and Debugging
View logs:
docker compose logs -f ollama  # Ollama service
docker compose logs -f webui   # WebUI service

Supported Models
Ollama supports hundreds of open-source models. Popular ones include:

Llama 3 (Meta): Versatile for chat and code.
Mistral: Efficient for general tasks.
Phi-3 (Microsoft): Lightweight and fast.
Gemma (Google): Strong in reasoning.

Browse more at Ollama Library.
Troubleshooting

Port Conflicts: Change ports in docker-compose.yml.
GPU Issues: Verify nvidia-smi works and toolkit is installed.
Out of Memory: Increase Docker resource limits or use smaller models (e.g., 7B parameters).
Slow Downloads: Models can be large (4-50GB); ensure stable internet.
Permission Errors: Run docker compose down -v to reset volumes if needed.

If issues persist, check Docker logs or open an issue on GitHub.
Contributing
Contributions are welcome! This project builds on the open-source spirit of Ollama and Open WebUI.

Fork the repository.
Create a feature branch (git checkout -b feature/amazing-feature).
Commit changes (git commit -m 'Add amazing feature').
Push to the branch (git push origin feature/amazing-feature).
Open a Pull Request.

For questions, suggestions, or collaboration, contact the maintainer at amr.marey@msn.com.
Please adhere to the Code of Conduct and ensure tests pass.
License
This project is licensed under the MIT License - see the LICENSE file for details.
Acknowledgments

Ollama for the core LLM runtime.
Open WebUI for the intuitive interface.
Docker and community for containerization magic.


Built with ❤️ by Amr Marey. Last updated: October 2025.```