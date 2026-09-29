# 🤖 Roblox Autonomous Game Agent (Desktop)

> **"Prompt in, playable Roblox game out."**  
> An experimental, OS-level autonomous desktop agent framework designed to turn natural language prompts into working Roblox games and Studio assets.

---

## ⚡ The Vision

The dream behind this project is complete, end-to-end automation for Roblox development. Instead of manually setting up scripts, configuring services, and tweaking properties in Studio, you simply feed the agent a prompt or game concept:

```
"Build a procedural obstacle course with dynamic moving platforms, 
a checkpoint saving system, and an arcade timer UI."
```

The agent takes the wheel:
1. **Plans** the game architecture and required assets.
2. **Generates** modular, clean Luau scripts into the local repository.
3. **Syncs** changes live into Roblox Studio via **Rojo**.
4. **Actuates** in-engine objects (parts, constraints, lighting, UI) using a custom Studio plugin.
5. **Verifies** and debugs runtime errors autonomously.

---

## 🏗️ Architecture & Tech Stack

Rather than relying purely on cloud REST APIs, this agent operates at the **native OS level** for maximum performance, real-time file access, and zero external API fees when paired with local/desktop AI agents.

```
       [ Prompt / Goal ]
               │
               ▼
      ┌─────────────────┐
      │   Java Layer    │  <-- General Purpose, Orchestration & UI
      └────────┬────────┘
               │ (Task IPC)
               ▼
      ┌─────────────────┐
      │    C++ Core     │  <-- OS-Level Hooks, Process Lifecycle, .bat/PS/Bash
      └────────┬────────┘
               │ (File IPC & Rojo)
               ▼
   ┌───────────────────────┐
   │ Roblox Studio + Plugin│  <-- In-Engine Actuation & Verification
   └───────────────────────┘
```

### ⚙️ Why C++ & Java?
- **C++ (The Core Engine)**:
  - Direct OS-level control: Spawns and manages processes (`RobloxStudioBeta.exe`, `rojo.exe`), executes `.bat` / PowerShell / Linux terminal scripts.
  - High-performance, low-latency filesystem watchers (`ReadDirectoryChangesW`) to track file updates instantly.
  - Atomic file-locking protocol to manage IPC between the host OS and the Studio plugin without race conditions.
- **Java (The Application Layer)**:
  - General application logic, CLI / GUI frontend, and configuration.
  - Manages the Kanban task queue, prompt processing pipeline, and workflow state machine.
  - Connects user intents to low-level C++ execution routines.

---

## 📦 Distribution Plans

- **Current Status**: Built primarily as a **personal research project and development tool** to explore the frontiers of agentic AI in game development.
- **Will it be public?**: I might consider releasing or distributing this for free down the line if it reaches a stable, usable state.
- **Expectation Check**: **Please don't have high hopes or expect a commercial release anytime soon!** This is an experimental prototype and a labor of curiosity.

---

## 🛑 The Reality Check (A Note on Development & Bandwidth)

Let's keep things 100% real:

> *"I am not entirely sure if this will make it all the way to the finish line without facing substantial delays."*

- **Academic Studies & Life**: Balancing university studies and coursework takes first priority.
- **Multiple Projects**: I maintain several ongoing software repositories and systems that require continuous attention.
- **Solo Maintenance**: Building a multi-language agent architecture (C++ + Java + Luau + OS scripting) is hard work. Even with the assistance of modern AI tools, architecting, debugging, and maintaining complex systems solo remains a real challenge.

Expect updates to come in bursts when time permits. Progress may pause, iterate slowly, or pivot as technical hurdles arise.

---

## 🗺️ Roadmap & Milestones

- [x] **Architecture Specification**: Define OS-level IPC, file structures (`agent_commands/`, `agent_results/`), and Rojo pipeline.
- [ ] **[Milestone #3](https://github.com/glzzjhn-byte/Secret-project-Roblox-agent/issues/3)**: Implement Agent-to-Studio Command Queue Protocol (JSON IPC + Atomic Locks).
- [ ] **C++ Process Supervisor**: Automated launch and health-monitoring for Roblox Studio and Rojo daemon.
- [ ] **Studio Actuator Plugin**: Custom Luau plugin to execute incoming commands and report receipts.
- [ ] **Verification & Log Scraper**: Automated log capture from `%LOCALAPPDATA%\Roblox\logs` for runtime feedback.
- [ ] **End-to-End Prompt Loop**: First autonomous prototype generating a playable mini-game from a single prompt.

---

## 📜 License & Acknowledgments
*Currently a private/personal experimental workspace. Subject to change.*
