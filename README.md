# OntoLab Desktop

OntoLab turns manuals, specifications and other documents into a reviewed knowledge graph, where every fact points back to the sentence it came from. This repository hosts the **desktop installers**. The desktop app keeps your projects and documents on your own computer and needs no account.

**[Download the latest release](https://github.com/IndustriAgents/OntoLab-Desktop/releases)** · [Website](https://industriagents.com/context/ontolab) · [Documentation](https://docs.industriagents.com/ontolab/)

## Requirements

- A Mac with Apple silicon (M1 or later)
- macOS 13 Ventura or later
- Disk space for the app (a 280 MB download) and your projects

Intel Macs, Windows and Linux are not supported yet. The [web version](https://industriagents.com/ontolab) runs in any browser for invited users.

## Install

1. Download `OntoLab-<version>-arm64.dmg` and `SHA256SUMS.txt` from the [latest release](https://github.com/IndustriAgents/OntoLab-Desktop/releases).
2. Optional but recommended: check the download. In Terminal, in the folder that holds both files:

   ```bash
   shasum -a 256 -c SHA256SUMS.txt
   ```

3. Open the DMG and drag **OntoLab** into **Applications**.
4. Open OntoLab. This preview is not notarized by Apple yet, so macOS blocks the first launch. Go to **System Settings → Privacy & Security**, find the message about OntoLab and choose **Open Anyway**. ([Apple’s instructions](https://support.apple.com/en-us/102445))

## Choose a model

OntoLab uses a language model to build ontologies and extract facts. Pick one of these:

- **Claude Code or Codex.** If one of these command-line tools is installed and signed in on your Mac, OntoLab finds it and lists it in the model picker. Calls use that tool's account and quota.
- **Ollama.** Run models entirely on your Mac. Start Ollama, then add its address and models to `desktop.env` (below).
- **An API key** for Anthropic, OpenAI, Gemini or DeepSeek, added to `desktop.env`.

`desktop.env` lives in the app's data folder. Open it with **File → Open local data folder**, then restart OntoLab after editing:

```dotenv
OLLAMA_BASE_URL=http://127.0.0.1:11434
OLLAMA_MODELS=llama3.1,qwen2.5
# ANTHROPIC_API_KEY=...
# OPENAI_API_KEY=...
```

Keep this file private. Keys are used by the app's local backend and are never shown in the interface.

## Your data

Projects, uploaded documents, run checkpoints and model caches are stored in `~/Library/Application Support/OntoLab`. The app sends nothing to IndustriAgents. When you use a cloud model, the text being processed is sent to that model's provider; with Ollama it stays on your Mac. On first use the app downloads small local models for search and evidence checking, and some optional steps look up public registries such as Wikidata.

## Get started

Open the bundled sample project, a technical manual for a distributing station, and follow the [walkthrough](https://docs.industriagents.com/ontolab/start/quickstart/).

## Feedback and support

This is a preview. Back up important projects before updating. Questions, bugs and feature requests: [hi@industriagents.com](mailto:hi@industriagents.com).

The OntoLab source code is not published in this repository.
