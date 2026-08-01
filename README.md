<p align="center">
  <img src="docs/odysseus-wordmark.png" alt="Odysseus" width="238">
</p>

<p align="center">
  A self-hosted AI workspace for chat, agents, research, documents, email, notes, calendar, and local model workflows.
</p>

<p align="center">
  <a href="#quick-start">Quick Start</a> ·
  <a href="docs/setup.md">Setup Guide</a> ·
  <a href="CONTRIBUTING.md">Contributing</a> ·
  <a href="ROADMAP.md">Roadmap</a>
</p>

<p align="center">
  <a href="https://repology.org/project/odysseus-ai/versions"><img src="https://repology.org/badge/vertical-allrepos/odysseus-ai.svg" alt="Packaging status"></a>
</p>

<p align="center">
  <img src="docs/odysseus-browser.jpg" alt="Odysseus interface">
</p>

---

## Quick Start

> `dev` is the default branch and gets the newest changes first. Use [`main`](https://github.com/odysseus-dev/odysseus/tree/main) if you want the more curated branch.

```bash
git clone https://github.com/odysseus-dev/odysseus.git
cd odysseus
cp .env.example .env
docker compose up -d --build
```
<<<<<<< HEAD
Compose starts Odysseus, ChromaDB, SearXNG, and ntfy. First run does a full
image build. Open `http://localhost:7000` after the containers are healthy.
If port `7000` is already taken, set `APP_PORT=7001` (or another free port)
in `.env`, recreate the container, and open `http://localhost:7001`.

Cookbook remote servers use an Odysseus-owned SSH key from `./data/ssh`
inside Docker. In **Cookbook -> Settings -> Servers**, generate/copy the
public key and add it to the remote server's `~/.ssh/authorized_keys`.
After generating the key, you can also install it from the host with:
```bash
ssh-copy-id -i data/ssh/id_ed25519.pub user@server
```
Cookbook local downloads are stored in `./data/huggingface`, mounted as
`~/.cache/huggingface` inside the Odysseus container. Cookbook-installed
serve engines and Python CLIs are stored in `./data/local`, mounted as
`~/.local`, so vLLM/llama.cpp installs survive container recreation.

After downloading a model, open **Cookbook -> Serve**, pick the cached model,
and launch it. When the server answers `/v1/models`, Odysseus adds it to the
chat model picker automatically. For NVIDIA GPUs in Docker, install the NVIDIA
Container Toolkit and add `gpus: all` to the `odysseus` service if `nvidia-smi`
is not visible inside the container.

The default Docker image is intentionally slim. For Python-based serve engines,
use **Cookbook -> Dependencies** to install vLLM, SGLang, llama-cpp-python, or
diffusers into the persisted `./data/local` mount. Native CUDA builds inside the
container also require CUDA toolkit binaries such as `nvcc`; if those are not
installed in the container, use prebuilt Python wheels or serve from a remote
GPU host that already has the toolkit.
=======

Open `http://localhost:7000` when the containers are healthy. The first admin password is printed in `docker compose logs odysseus`.
>>>>>>> cf4e240ad1622da6a904f496b19d656a2b9c6393

Native installs, GPU notes, Windows/macOS instructions, HTTPS, and configuration live in the [setup guide](docs/setup.md).

## Features

- **Chat + Agents** — local/API models, tools, MCP, files, shell, skills, and memory.
- **Cookbook** — hardware-aware model recommendations, downloads, and serving.
- **Deep Research** — multi-step web research with source reading and report generation.
- **Compare** — blind side-by-side model testing and synthesis.
- **Documents** — writing-first editor with AI edits, suggestions, Markdown, HTML, CSV, and syntax highlighting.
- **Email** — IMAP/SMTP inbox with triage, tags, summaries, reminders, and reply drafts.
- **Notes, Tasks + Calendar** — reminders, todos, scheduled agent tasks, and CalDAV sync.
- **Extras** — gallery/image editor, themes, uploads, web search, presets, sessions, and 2FA.

## Demo

A full hover-to-play tour lives on the landing page: [`docs/index.html`](docs/index.html).

## Contributing

Help is welcome. The best entry points are fresh-install testing, provider setup bugs, mobile/editor polish, docs, and small focused refactors. See [CONTRIBUTING.md](CONTRIBUTING.md) and [ROADMAP.md](ROADMAP.md).

## Security

Odysseus is a self-hosted workspace with powerful local tools. Keep auth enabled, keep private data out of Git, and do not expose raw model/service ports publicly. Deployment details are in the [setup guide](docs/setup.md#security-notes).

## Star History

<a href="https://www.star-history.com/?repos=odysseus-dev%2Fodysseus&type=date&legend=top-left">
 <picture>
   <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/chart?repos=odysseus-dev/odysseus&type=date&theme=dark&legend=top-left" />
   <source media="(prefers-color-scheme: light)" srcset="https://api.star-history.com/chart?repos=odysseus-dev/odysseus&type=date&legend=top-left" />
   <img alt="Star History Chart" src="https://api.star-history.com/chart?repos=odysseus-dev/odysseus&type=date&legend=top-left" />
 </picture>
</a>

## License

AGPL-3.0-or-later -- see [LICENSE](LICENSE) and [ACKNOWLEDGMENTS.md](ACKNOWLEDGMENTS.md).
