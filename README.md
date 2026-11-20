# GitHub Tabs Roundup — 104 repos + 2 notes (five batches, read 2026-11-13 → 2026-11-14)

A consolidated summary of the GitHub tabs open in your browser, in five batches (45 + 21 + 3 + 12 + 29 tabs), grouped by theme. Each entry states what the project is (from its README) and how it fits your stack: a single RTX 3090 for local LLM serving (MTP, vLLM, llama.cpp, Prism ternary, Qwen-3.8/3-Next), the Arabic-streaming Kodi addon with automatic Arabic/English subtitles, local video generation (ComfyUI), TTS, and agent/skill/MCP building (Zen + BiDi). Raw READMEs of **all** repos are downloaded to `repo-readmes/` (linked from every entry) with referenced images in `repo-readmes/img/<repo>/`, so each README renders offline. "Fit" is your relevance: high = directly usable on your 3090/workflow, low = off-domain.

## Quick index

| Repo | Theme | One-line summary | Fit |
|---|---|---|---|
| m1guelpf/auto-subtitle | Subtitles | ffmpeg + Whisper CLI that transcribes, translates and burns subtitles | High |
| absadiki/subsai | Subtitles | Whisper subtitle engine: Web-UI + CLI + Python, whisperX diarization, faster-whisper | High |
| InboraStudio/Subtitle-Generator-AI | Subtitles | Offline Qt/C++ Whisper subtitle generator with CUDA/Vulkan/HIP acceleration | Med |
| midudev/subvid.app | Subtitles | Browser-based subtitle generation/edit/translate (Whisper + NLLB) | Med |
| (topic) subtitles-generator | Subtitles | GitHub topic page indexing 211 subtitle repos | Low |
| noonghunna/club-3090 | LLM serving | Community serving recipes for RTX 3090/4090/5090: vLLM, SGLang, llama.cpp, ternary/MTP builds | High |
| Niko1221/Strata | LLM serving | One-click local serving of Qwen3.8-Flash-Next + DeepSeek-Flash MoE (RTX 30/40/50) | High |
| (gist) komikndr llama.cpp+vLLM | LLM serving | Single-3090 MTP/vLLM config for Qwen 3.8-27B/35B with measured tok/s | High |
| NVIDIA/SkillEvaluator | Skills | Multi-tier evaluation of agent skills: quality gates, overlap detection, A/B agent runs | Med |
| addyosmani/agent-skills | Skills | 25 production engineering skills + lifecycle slash commands for 70+ agents | Med |
| ifixai-ai/ifixai | Skills/agents | Audits AI agents from traces in <120s; local MCP server + Claude plugin | Med |
| prabanta-dev/janas | LLM serving | Pure-C MoE engine streaming experts from NVMe; runs >RAM models on laptops | Low |
| volcengine/OpenViking | Skills/agents | "Context database" for agents: knowledge, memory and skills as a viking:// filesystem | Med |
| sh6drack/zen-mcp | Browser | First MCP server for Zen Browser: 20 tools over BiDi WebSocket | High |
| webbrain-one/webbrain | Browser | Open-source AI browser agent for Chrome/Firefox (autonomous actions + embeds) | Med |
| morluto/rea | Browser/RE | One MCP for reverse engineering binaries, apps, APKs, model files, websites | Med |
| tangerineturtle1/NX2navi | Browser | Native Vulkan port of Ocarina of Time to Switch 2 (fan project, Windows) | Low |
| meituan-longcat/longcat-video | Video | 13.6B unified T2V/I2V/video-continuation model + avatar line (Meituan) | Low |
| FlashML-org/FreeVideo | Video | MiniMax H3 on 8 GB VRAM/16 GB RAM (ComfyUI plugin); int8 for RTX 30 series | High |
| edenfunf/reelmimic | Video | Local multi-agent (Claude Code/Codex) video style-mimic from a reference clip | High |
| workingprototype/fuobe | Video | Open creative studio on ComfyUI: image/video/3D/audio, local GPU or cloud | Med |
| JuneYaooo/rea-video | Video | Reverse-engineers videos shot by shot (live/AI/coded) with remake guidance | Med |
| bitti-ai/slopus | Video | Desktop AI media workspace (timeline, agent, local generation); 24 GB VRAM+ | Low |
| mohamedelaassal/youtubevideogenerator | Video | Cloud SaaS that scripts→uploads YouTube videos (Laravel/Vue/n8n) | Low |
| code-video-model/codevideomodel | Video | Research: Code Video Model report + CodeVideoBench (minimal README) | Low |
| ant-research/4DAnyone | Video | SIGGRAPH Asia 2026: 4D from casual monocular video for 4DGS | Low |
| microsoft/VibeVoice | Voice | Open voice AI: TTS family + long-form 50-language ASR (now in HF Transformers) | Med |
| debpalash/VoiceStudio | Voice | Fully local ElevenLabs alternative: clone, design, dub, transcribe, audiobooks (646 lang) | Med |
| umlx5h/LLPlayer | Voice | Language-learning player: real-time AI subtitles + live translation (local LLMs) | Med |
| youmind-openlab/awesome-nano-banana-pro-prompts | Image | 10k+ Nano Banana Pro prompts with preview images, 16 languages | Med |
| xiaoyecodes/code-animation-prompts | Image | 341 code-animation style prompts + 196 stills, as a Claude/Codex skill | Med |
| cth9191/animate | Image | Claude Code skill: procedural canvas videos, 7 styles, beat-mapped audio | Med |
| dozentwelve/papermorph | Image | Claude Code skill: books → narrated web lessons / paper-puppet films | Low |
| alexgreensh/anidoodle | Image | Art + animation written as deterministic code; 32 styles, music in code | Med |
| tejashmakwana/motionmaxxing | Image | Agent skill polishing AI video into motion-design quality (GSAP/HyperFrames) | Med |
| faviovazquez/showtime | Image | Local video studio for coding agents: one-line brief → rendered video | Med |
| jastfan/explainroo-ui | Image | Web studio for Explainroo: local Kokoro voice + Whisper timing → MP4 | Low |
| enesozturk/dimensional-drawing | Image | Skills drawing Apple-style dimensional spec sheets of UI components | Low |
| esengine/estella | Image | Fast 2D/3D game engine (TS SDK, C++/WASM core, visual editor) | Low |
| egmalt/house-planner | Image | Self-hosted true-scale house planner (2D/3D, MEP, priced BOM) | Low |
| facefusion/facefusion | Image | Face-swap + lip-sync platform (Python, Gradio, CUDA, 24+ models) | Med |
| anomalyco/rune | Image | Native GPU-rendered Rust UI framework; headless mode for agents | Low |
| scenario-labs/skills | Image | Scenario MCP skills for cloud image/video/3D gen + DCC expert tools | Low |
| ppmpreetham/BUI | Image | Blender's UI as a standalone library (C core; Python/Rust/JS/ImGui bindings) | Low |
| HQarroum/docker-android | Mobile | Minimal Docker image running a headless Android emulator with KVM + ADB | Low |
| justvugg/colibri | LLM serving | 744B MoE runtime for your hardware (CUDA/Vulkan/CPU) | High |
| brandon-collins7/sketchvlm | Image | VLM annotates images to explain thoughts (EMNLP 2026) | Med |
| neuregex/freefield | Video | Open-source Higgsfield on ComfyUI, every app is one folder | High |
| jub0t/Concat | Video | Free open-source cross-platform video editor | Med |
| k2-fsa/OmniVoice | Voice | Zero-shot multilingual TTS + voice cloning (Apache 2.0) | High |
| OpenBitSys/BitDecoding-FP4 | LLM serving | FP4 KV cache + native FP4 attention as a vLLM backend | Med |
| OpenBitSys/BitDecoding | LLM serving | Low-bit KV cache, 3-9x over Flash-Decoding-v2 (HPCA 2026) | Med |
| rxjfighting/SceneMosaic | Image | Indoor image to 3D scene (.glb), SAM3 + agentic layout | Low |
| KeygraphHQ/shannon | Skills | Autonomous AI pentester for web apps & APIs (AGPL 3.0) | Low |
| Yuan-ManX/open-motion | Image | AI-native motion runtime: web canvas + motion engine (MIT) | Med |
| nexu-io/openmotion | Video | Agentic video generation: remake/recut any video (Apache 2.0) | Med |
| nexu-io/motion-anything | Image | Local chat-native motion engine, 403 recipes, 0 npm deps | Med |
| nexu-io/open-design | Image | Collaborative AI design agent workspace (Apache 2.0) | Med |
| herdrdev/herdr | Skills | Terminal runtime for coding agents: detach, restore, blocked state | Med |
| nota-daw/nota | Voice | Free cross-platform music studio DAW (AGPL 3.0) | Low |
| lightpanda-io/browser | Browser | Headless browser written in Zig for AI agents (AGPL 3.0) | High |
| openai/whisper | LLM serving | General-purpose multilingual ASR/translation (MIT) | High |
| Indras-Mirror/Xolotl | LLM serving | DeepSeek-V4.1-Flash 552B + GLM-5.3/Qwen3.8/LFM3-Omni on one GPU, OpenAI+Anthropic API; 32.6-41 tok/s measured | High |
| brcly/legion-kvm | Windows on Linux (KVM) | KVM runtime: Windows apps via Proton in a Linux guest, shared NVIDIA/AMD GPU, Wayland desktop | Low |
| brcly/linuwux-runtime | Windows on Linux (Wine) | Rust LD_PRELOAD shim keeping CPU/signal/env consistent for Wine/Proton Windows games | Low |
| microsoft/TokenEconomizer | Agent skills | Research: experience-driven black-box cost control for coding agents; 18–31% cheaper on SWE-Bench | Med |
| ag-ui-protocol/ag-ui | Browser | Open event-based protocol connecting any agent to any app (web/mobile/terminal/Slack); 1.0 spec + SDKs | Med |
| talsiach/take-one | Image | Claude Code skill: one line → finished short film/launch video with storyboard, voice and a review room | Med |
| mankidev/antialgorithm | Image | Claude Code skill steering creative work away from the model's average pick; seeds, moves, SVG checks | Med |
| ersinkoc/phonebox | Mobile | Turns an old Android phone into a desk panel: PC stats, AI coding quotas, touch controls over USB/Wi-Fi | Med |
| Ciao1019/ArcMD | Image | Native Go+MyGo Markdown/rich-text editor inspired by Arc; 120 Hz, standard .md files; macOS/Win/Linux | Low |
| workingprototype/ComfyUI-Fuobe-Connect | Video | ComfyUI node pack letting the Fuobe studio drive your local ComfyUI (direct or HTTPS pairing) | High |
| 0x0funky/audioghost-ai | Voice | Local SAM-Audio sound separation by text prompt; per-track mixer, export WAV/FLAC/MP3 or remixed video | High |
| erkamyaman/rust-anything | Dev tools | Rewrite an app in Rust piece-by-piece, verified against the original's recorded behavior (CLI, HTTP, libs) | Med |
| edge0-ai/audio8_tts | Voice | Compact zero-shot voice-cloning TTS (23 langs incl. Arabic) with llama.cpp/GGUF local inference | High |
| klippa-app/go-pdfium | Dev tools | Fast multi-threaded Go PDF library on PDFium: render, extract, create, edit, form fill | Med |
| martin-olivier/airgorah | Security | Rust+GTK4 WiFi security auditor: capture traffic, deauth, handshakes/PMKIDs, crack WPA passwords (Linux) | Low |
| cheaper-inference/OmniRoute | LLM serving | Free MIT AI gateway: one endpoint, 375 providers (150+ free), 1,400+ models, per-token cost tracking | High
| eagle-hq/eagle-4 | LLM serving | Official EAGLE-4 inference code: efficient attention/tokenizer for cheaper long-context decoding | Med
| google/skills | Skills | Agent skills for Google products/tech (Apache 2.0) | Med
| HKUDS/CLI-Anything | Browser/agents | 'Making ALL Software Agent-Native': CLI hub turning apps into agent-accessible CLIs | Med
| backnotprop/plannotator | Browser/agents | Workspace to shape, decide, plan and annotate agent runs with human-in-the-loop review | Med
| trycua/cua | Browser/agents | Computer-use 2.0: open drivers, cross-OS sandboxes + benchmarks for screen agents | High
| milind-soni/OpenMausBot | Browser/agents | Open 'Grok Bot' alt with a VM bots can use (26k★) | Low
| OpenMausBot/OpenMausBot | Browser/agents | Smaller upstream fork of the bot-VM concept (15★) | Low
| staryone/motlab | Video | Video-as-code: canvas scenes via WebCodecs in headless Chrome + review viewer | Low
| openfilm/openfilm | Video | Open-source AI video agent: turns coding agents into video agents with editors | Med
| zhouxiaoka/autoclip | Video | AutoClip: one link → short clips with captions, covers + posting copy (CN) | Med
| jamesondh/chimera-vocal-synth | Voice | Ultimate vocal synthesizer: sing, speak, beatbox (MIT) | Med
| Remocn/remocn | Image/animation | Production animations/transitions/backgrounds/scenes for Remotion | Med
| gabrielelozupone/kokon | Image | Edit photos by describing the change on your own GPU (local, AGPL 3.0) | High
| nilbuild/driver.js | Image/UI | Lightweight dependency-free JS lib for guiding user focus across a page | Low
| DuarteSantos8/openGym | Mobile | Open-source gym & body-weight tracker in the iOS App Store | Low
| Gathin23/cleanyourtv | Mobile | Debloat Android/Google TV over Wi-Fi to an Apple-TV-style home (Low) | Low
| OpenBMB/MiniCPM-OCR | Dev/sec | Fast accurate OCR with correctness assessment (Apache 2.0) | Low
| tt-a1i/archify | Dev/sec | Agent skill: idea/plan/codebase → beautiful interactive diagram | Med
| awesome-selfhosted/awesome-selfhosted | Dev/sec | Canonical list of self-hostable free software services/web apps | Low
| dream-num/univer | Dev/sec | Univer Office SDK: build your own AI office (edit/calc/collab) | Low
| shadcn-labs/pdfcn | Dev/sec | Beautiful PDF React components on Takumi + Forme, zero-config | Low
| refinedev/refine | Dev/sec | React framework for internal tools, admin panels, dashboards, B2B apps | Low
| storytold/pdfcraft | Dev/sec | PdfCraft: open-source pure-Rust PDF reader/editor (ArtCraft, Apache 2.0) | Low
| oomol-lab/pdf-craft | Dev/sec | Convert PDF files into various other formats | Low
| blacklanternsecurity/bbot | Dev/sec | Recursive internet scanner for hackers (AGPL 3.0) | Low
| c4illin/ConvertX | Dev/sec | Self-hosted online file converter, 1000+ formats (AGPL 3.0) | Low
| babygoton/WorkDaddy | Dev/sec | Desktop enhancement for WorkBuddy/CodeBuddy: multi-account, unattended long tasks | Low
| huggingface/open-tts-leaderboard | Voice/TTS | Eval scripts for the Open TTS Leaderboard (HF Space) | Med

## 1. Subtitles & transcription

### m1guelpf/auto-subtitle
https://github.com/m1guelpf/auto-subtitle
- **Local README:** [repo-readmes/m1guelpf-auto-subtitle.md](repo-readmes/m1guelpf-auto-subtitle.md)
- **What it is:** A small Python CLI that uses `ffmpeg` and OpenAI Whisper to transcribe a video, optionally translate (`--task translate`) to English, and write back an overlaid/subtitled copy. Supports `tiny`→`large` models; installed via `pip install git+…`.
- **How it helps you:** The most drop-in option for the addon pipeline: one command per episode, translation built in, easy to wrap in your build/tests. Pair it with a `medium`/`large` model for Arabic audio.

### absadiki/subsai
https://github.com/absadiki/subsai
- **Local README:** [repo-readmes/absadiki-subsai.md](repo-readmes/absadiki-subsai.md)
- **What it is:** A Whisper-based subtitle-generation tool with a Web-UI, a CLI, and a Python package. Backends include `whisper.cpp`, `faster-whisper` (CTranslate2, ~4× faster with 8-bit quant), `whisperX` (70× realtime with large-v2, word-level timestamps, speaker diarization), `stable-ts`, and Hugging Face Transformers models. GPL-3.0.
- **How it helps you:** The Python/CLI side slots into a headless build script; whisperX's speaker diarization and word timestamps are exactly what a multi-speaker or dual-language track needs.

### InboraStudio/Subtitle-Generator-AI
https://github.com/InboraStudio/Subtitle-Generator-AI
- **Local README:** [repo-readmes/inborastudio-subtitle-generator-ai.md](repo-readmes/inborastudio-subtitle-generator-ai.md)
- **What it is:** An offline, local Whisper subtitle generator written in C++/Qt6 with GPU acceleration selectable at build time (NVIDIA CUDA, AMD HIP/ROCm, or Vulkan — which covers NVIDIA too). No length limit, no cloud, SRT/VTT output.
- **How it helps you:** Runs locally on your 3090 with no API keys, but it ships as a desktop (Inno-installed) app rather than a CLI — good for manual spot-checks, not headless batch generation for the addon.

### midudev/subvid.app
https://github.com/midudev/subvid.app
- **Local README:** [repo-readmes/midudev-subvid-app.md](repo-readmes/midudev-subvid-app.md)
- **What it is:** A browser-only subtitle workspace (Astro + Tailwind + transformers.js): upload video/audio, Whisper transcribes (WebGPU optional), NLLB-200 translates, a timeline editor fixes text/timing/styling, and you export `.srt` or an MP4 with burned captions. All client-side, models cached in IndexedDB.
- **How it helps you:** Handy in Zen for a quick generate-edit-translate of individual clips with no installs; not headless, so it can't replace a batch pipeline.

### (topic) subtitles-generator
https://github.com/topics/subtitles-generator
- **What it is:** Not a repo — a GitHub topic page indexing 211 subtitle repos (MioSub, haoone-app, Transub, hear, whisper-website, etc.).
- **How it helps you:** A good index for deeper scouting if you want speaker-diarization or forced-alignment tools beyond the four above.

## 2. LLM serving on one 3090 & agent skills

### noonghunna/club-3090
https://github.com/noonghunna/club-3090
- **Local README:** [repo-readmes/noonghunna-club-3090.md](repo-readmes/noonghunna-club-3090.md)
- **What it is:** Community recipes for serving LLMs on RTX 3090/4090/5090: working compose configs, patches and measured numbers across vLLM, SGLang, llama.cpp (mainline, a moe-cache fork, and PrismML's ternary build), ExLlamaV3, and one-model engines (Strata, Project Maya, bucko-vllm, HyperQwen). Ships single/double/quad/octo configs for Qwen3.8-27B, Qwen3.6-35B and Gemma 4 (26B/31B), plus "Club 3090 AI Studio" that adds open-weight image/video/audio gen to a chat model behind Open WebUI.
- **How it helps you:** This is literally a catalog for your hardware. Start with the 1×3090 single-card recipes (incl. MTP/ternary ones) and the measured TPS numbers; the AI Studio is a shortcut if you want image/video gen next to the LLM.

### Niko1221/Strata
https://github.com/Niko1221/Strata
- **Local README:** [repo-readmes/niko1221-strata.md](repo-readmes/niko1221-strata.md)
- **What it is:** A one-click desktop app + terminal for running Qwen3.8-Flash-Next locally — ISTA-DASLab GGUFs recommended (IQ2_XS/IQ3_XXS/IQ3_S; a Coder for code), with Unsloth UD packs as fallbacks. Also serves DeepSeek V4.1-Flash-1017 in SSD-streaming MoE mode (2.0 bpw ≈ 257 GB download, RTX 30/40/50, AMD R9700, Strix Halo, 64 GB+ Macs). MIT.
- **How it helps you:** A ready-made single-card serving path for exactly the Qwen-3.8/3.6 models you already run, including a documented DeepSeek-Flash MoE mode — compare its measured speeds against your own vLLM/llama.cpp/MTP setups.

### (gist) komikndr: llama.cpp + vLLM on a 3090
https://gist.github.com/komikndr/b17955e1a80ce6ede9a3115f16216bc5
- **Local README:** [repo-readmes/komikndr-gist.md](repo-readmes/komikndr-gist.md)
- **What it is:** Not a repo — a setup note + configs: llama.cpp server for Qwen3.8-27B int4 with `--spec-type draft-mtp` (MTP), KV cache q8_0, 81920 ctx, flash-attention on; a vLLM serve for the same model (bfloat16, fp8_e4m3 KV cache, prefix caching, chunked prefill, mamba-cache align); OpenCode config with reasoning variants (none/low/medium/xhigh and `xhigh-no-preserve`). Measured on a 3090 + WSL2: 27B ≈ 30 tok/s, Qwen3.6-35B-A3B ≈ 75 tok/s, DSv4-Flash ≈ 6 tok/s.
- **How it helps you:** The most directly portable content of all your tabs: MTP spec flags, q8 KV caching, and reasoning-budget patterns to steal into your own llama.cpp/vLLM configs for Qwen-3.8-Flash/Next on the same card.

### prabanta-dev/janas
https://github.com/prabanta-dev/janas
- **Local README:** [repo-readmes/prabanta-dev-janas.md](repo-readmes/prabanta-dev-janas.md)
- **What it is:** A pure-C, dependency-free MoE inference engine (Janas-LLM) that streams experts from an NVMe SSD so models larger than RAM run on a laptop (their headline: Qwen3-Next-80B on 32 GB RAM, tens of tok/s). Includes `janas-mcp` and a `janas-server` exposing OpenAI-compatible HTTP APIs. GPL-3.
- **How it helps you:** CPU+SSD-offloading territory rather than your single-GPU lane — an interesting experiment if you ever want to push a model past 24 GB.

### NVIDIA/SkillEvaluator
https://github.com/NVIDIA/SkillEvaluator
- **Local README:** [repo-readmes/nvidia-skillevaluator.md](repo-readmes/nvidia-skillevaluator.md)
- **What it is:** A multi-tier framework for evaluating AI agent skills: quality gates, semantic-overlap detection between skills, synthetic evaluation dataset generation, and live sandboxed agent runs that A/B test task success with/without a skill. Ships GitHub/GitLab CI templates. Apache-2.
- **How it helps you:** If you package your Hermes/Claude Code skills (like the addyosmani pack), this is the harness for proving they actually move task success.

### addyosmani/agent-skills
https://github.com/addyosmani/agent-skills
- **Local README:** [repo-readmes/addyosmani-agent-skills.md](repo-readmes/addyosmani-agent-skills.md)
- **What it is:** 25 production-grade engineering skills + 9 lifecycle slash commands (/spec → /ship), with verification gates and anti-rationalization tables, installable via `npx skills` into 70+ agents (Claude Code, Cursor, Codex, Copilot, Kiro, Gemini CLI, …). 116k stars, MIT.
- **How it helps you:** The strongest public example of how to structure a skills pack; the `/build auto` approval model and per-skill verification gates are worth copying into your own Hermes skills.

### ifixai-ai/ifixai
https://github.com/ifixai-ai/ifixai
- **Local README:** [repo-readmes/ifixai-ai-ifixai.md](repo-readmes/ifixai-ai-ifixai.md)
- **What it is:** Independent auditing of AI agents: from traces/SARIF, it judges "is the agent doing what it's supposed to do?" in under ~120 seconds, runnable by a human or the agent itself; local MCP server, Claude plugin, and one-command self-check. (You tabbed it under voice; it's actually an agent-auditing tool — placed here.) Apache-2.
- **How it helps you:** A useful QA layer for the agent workflows you build — catch drift in your own skills and pipelines cheaply.

### volcengine/OpenViking
https://github.com/volcengine/OpenViking
- **Local README:** [repo-readmes/volcengine-openviking.md](repo-readmes/volcengine-openviking.md)
- **What it is:** A self-evolving "context database" for AI agents: knowledge, memory, and skills stored as a virtual filesystem (`viking://`) with ls/tree/read/write/grep, per-directory summaries, and event-driven memory consolidation (from the VikingMem paper). Reported LoCoMo memory accuracy of 80–83% vs 24–57% for native agent memory. AGPL-3.
- **How it helps you:** A candidate long-term memory/RAG layer for your agent skills and the addon workflow — heavy and AGPL, so evaluate before adopting.

### JustVugg/colibri
https://github.com/JustVugg/colibri
- **Local README:** [repo-readmes/justvugg-colibri.md](repo-readmes/justvugg-colibri.md)
- **What it is:** A runtime for running huge open-weight mixture-of-experts models on the hardware you already have — dense layers in RAM, routed experts on disk, the hottest experts on GPU (README cites GLM-5.2, 744B, ~40B parameters per token active). Three backends on one machine (CUDA, Vulkan, CPU) plus Apple Silicon support; README benchmarks include ~235.1 tok/s on CUDA and ~214.1 tok/s on Vulkan (Q4_K_M). Code is Apache-2.0, models keep their own license.
- **How it helps you:** Direct match for your single 3090: the CUDA path runs multi-hundred-B MoEs on 24 GB with disk offload, and it complements your llama.cpp/vLLM/MTP stack when you want a model that won't fit in RAM.

### OpenBitSys/BitDecoding-FP4
https://github.com/OpenBitSys/BitDecoding-FP4
- **Local README:** [repo-readmes/openbitsys-bitdecoding-fp4.md](repo-readmes/openbitsys-bitdecoding-fp4.md)
- **What it is:** LLM decoding system combining FP4 KV-cache quantization with native FP4 attention kernels (arXiv 2611.09825), integrating into vLLM as an out-of-tree CUSTOM backend: paged FP4 KV storage plus separate BF16 sink and recent-token buffers; README claims near-lossless accuracy across seven benchmarks. MIT.
- **How it helps you:** Partial fit — it's a vLLM backend for your 3090, but the FP4 kernels target Blackwell-class GPUs, so check the FP8/BF16 path or treat the co-design as reference.

### OpenBitSys/BitDecoding
https://github.com/OpenBitSys/BitDecoding
- **Local README:** [repo-readmes/openbitsys-bitdecoding.md](repo-readmes/openbitsys-bitdecoding.md)
- **What it is:** High-performance, GPU-optimized long-context LLM decoding with a low-bit KV cache (accepted to HPCA 2026); claims 3-9x speedup over Flash-Decoding-v2 and ships conda+pip install plus KV-caching and decoding examples. MIT.
- **How it helps you:** Directly relevant to long-context serving on your single 24 GB 3090, though the README benchmarks are on Blackwell — verify Ampere throughput before adopting.

### KeygraphHQ/shannon
https://github.com/KeygraphHQ/shannon
- **Local README:** [repo-readmes/keygraphhq-shannon.md](repo-readmes/keygraphhq-shannon.md)
- **What it is:** Autonomous AI pentester for web applications and APIs: analyzes source, identifies attack paths and executes real exploits to prove vulnerabilities ("no exploit, no report"); CLI with interactive credential config and GitHub Actions CI/CD integration; built on Pi, Playwright CLI and Mantis. AGPL-3.0.
- **How it helps you:** Off-domain for your stack (security, not subtitles/video/LLM serving); the agent-orchestration patterns (Playwright + Pi) are the only part worth borrowing.

### herdrdev/herdr
https://github.com/herdrdev/herdr
- **Local README:** [repo-readmes/herdrdev-herdr.md](repo-readmes/herdrdev-herdr.md)
- **What it is:** "The runtime your coding agents live on": a background server keeps terminals running when you close the client or lose SSH and restores the saved layout after a restart; panes marked working/blocked/idle, several machines in one window with a combined agent list, agents drive it via CLI + socket API. Apache-2.0.
- **How it helps you:** Fits your multi-agent SSH workflow (agents building on the 3090) by keeping several coding agents running with visible blocked/working state — complements rather than replaces model serving.

### openai/whisper
https://github.com/openai/whisper
- **Local README:** [repo-readmes/openai-whisper.md](repo-readmes/openai-whisper.md)
- **What it is:** General-purpose multilingual speech recognition: a Transformer sequence-to-sequence model trained on diverse audio, doing speech recognition, translation and language ID in one model; CLI + Python API (load audio, log-Mel spectrogram, detect language, decode) with model/language tables and per-OS install docs. MIT.
- **How it helps you:** A direct match: your subtitle pipeline is already Whisper-based — this is the engine for per-3090 inference and Arabic/English transcription in the Kodi addon.

### Indras-Mirror/Xolotl
https://github.com/Indras-Mirror/Xolotl
- **Local README:** [repo-readmes/indras-mirror-xolotl.md](repo-readmes/indras-mirror-xolotl.md)
- **What it is:** Xolotl runs DeepSeek-V4.1-Flash (all 552B, MoE) on a single GPU as a local coding agent behind one OpenAI- and Anthropic-compatible server, alongside GLM-5.3-Flash, Qwen3.8-Flash-Next, Qwen3.8-27B, LFM3-Omni and Muse Glimmer 30B. It is built on [Strata](https://github.com/Niko1221/Strata) — the engine you already track — plus ggml/llama.cpp, with 70,000+ added lines: its own per-model engines, expert-tiering across VRAM / pinned RAM / NVMe, "Xolotl Direct" that writes NVMe experts straight into VRAM (3.1 ms/expert vs 11), an opt-in fast mode that keeps a 2-bit copy of the two biggest expert formats, and measured 32.6 tok/s decode (41.1 in fast mode, +26%) on a single RTX 4090 + 110 GB DDR4 with 512K context. MIT.
- **How it helps you:** The single most complete single-GPU MoE serving path for your exact lane (local 3090, OpenAI-compatible models, MTP/ternary). It is a superset of the Strata setup you already track, so the config patterns (q8 KV caching, MTP spec, 110 GB expert tiering) transfer directly to your own llama.cpp/vLLM/MTP configs. Caveat: its measured tok/s are on a RTX 4090, and "552B on one card" assumes ~110 GB RAM — your 3090 has the same 24 GB VRAM class, so treat the tok/s as a ceiling and verify the RAM tier; the "Smaller cards" section confirms it adapts to the card (RAM matters as much as VRAM), so the Qwen/DeepSeek configs should port.

### microsoft/TokenEconomizer
https://github.com/microsoft/TokenEconomizer
- **Local README:** [repo-readmes/microsoft-tokeneconomizer.md](repo-readmes/microsoft-tokeneconomizer.md)
- **What it is:** A research tool from UC Berkeley + Microsoft Research that does experience-driven black-box cost control for coding agents: it watches how an agent works and cuts waste (re-learning the repo, unused tools, failure loops) via micro-skills, tool pruning and failure-loop intervention. Measured 18.4–30.9% lower mean cost on SWE-Bench across five agent-model combos — cheaper in all 30 cells, Pass@1 up in 4 of 5 — and works with Claude Code, Codex, GitHub Copilot CLI and Pi. MIT, Python 3.10+.
- **How it helps you:** Relevant to the agent side of your workflow: if you ever run API-based agents alongside your local models, this is a concrete way to cut per-token waste and make short turns cheaper. Caveat: since you already serve locally (free), the payoff shows up mainly when an agent calls cloud APIs.

### cheaper-inference/OmniRoute
https://github.com/cheaper-inference/OmniRoute
- **Local README:** [repo-readmes/cheaper-inference-omniroute.md](repo-readmes/cheaper-inference-omniroute.md)
- **What it is:** A free MIT-licensed AI gateway that front-ends 375 providers (150+ free) and 1,400+ models behind a single OpenAI-compatible endpoint, with per-token cost tracking and provider routing. Built to keep an agent's coding loop running across many LLM backends.
- **How it helps you:** A handy layer for your agent/skill/MCP work: point Zen plus your local 3090 serving (llama.cpp/vLLM) and free cloud models at one endpoint, and watch token spend per call.

### eagle-hq/eagle-4
https://github.com/eagle-hq/eagle-4
- **Local README:** [repo-readmes/eagle-hq-eagle-4.md](repo-readmes/eagle-hq-eagle-4.md)
- **What it is:** The official inference code for EAGLE-4, an efficient attention/tokenizer design that cuts the cost of long-context serving by using a small draft model to predict future tokens. Ships runnable inference for the model.
- **How it helps you:** If you want lower-latency or cheaper long-context decoding on your 3090, this is a reference implementation to benchmark against your current vLLM/llama.cpp/ternary setups.

### google/skills
https://github.com/google/skills
- **Local README:** [repo-readmes/google-skills.md](repo-readmes/google-skills.md)
- **What it is:** A collection of 'Agent Skills' for Google products and technologies — reusable skill definitions agents can load to operate Google's tools and data (Apache 2.0).
- **How it helps you:** A template for structuring skills in your own agent stack, and a source of patterns if any of your workflows touch Google services.

## 3. Browser & agent automation

### sh6drack/zen-mcp
https://github.com/sh6drack/zen-mcp
- **Local README:** [repo-readmes/sh6drack-zen-mcp.md](repo-readmes/sh6drack-zen-mcp.md)
- **What it is:** The first MCP server for Zen Browser: 20 tools (navigate, list/select/close tabs, snapshot with selectors, screenshot, page text, form fields, click, fill, select, check, press key, JS eval, scroll, wait) speaking WebDriver BiDi directly over WebSocket — no Selenium, no Playwright, no browser driver. Known limits per README: Firefox BiDi is still maturing, zombie sessions need a Zen restart, no file upload.
- **How it helps you:** This is the BiDi-based Zen MCP you were looking for — install it, point it at `zen --remote-debugging-port 9222`, and you get real browser control from Hermes/Claude Code on the browser you actually use.

### webbrain-one/webbrain
https://github.com/webbrain-one/webbrain
- **Local README:** [repo-readmes/webbrain-one-webbrain.md](repo-readmes/webbrain-one-webbrain.md)
- **What it is:** An open-source AI browser agent for Chrome and Firefox (large monorepo, v47.1.1): extensions, embeddable widgets, a cloud bridge, and a hardened tool loop with "hard guard" cards for risky actions (deletes, submissions, payments) in 23 locales.
- **How it helps you:** The full-agency end of your spectrum: it acts autonomously rather than exposing raw tools. Worth a look as a contrast to zen-mcp, or as inspiration for guardrail patterns.

### morluto/rea
https://github.com/morluto/rea
- **Local README:** [repo-readmes/morluto-rea.md](repo-readmes/morluto-rea.md)
- **What it is:** "REA: Reverse Engineer Anything" — one MCP server for reverse engineering binaries, applications, and runtime behavior. Agents can inspect Android APKs (JADX-based), model artifacts (GGUF/safetensors metadata), IL2CPP/Godot PCK files, websites (browser observation), and more, then explain, implement and test from the returned code/references. MIT; very large and very active.
- **How it helps you:** Your tool when you need to see how a streamer/copyright pipeline works at the binary level — e.g. reverse-engineering a DRM-protected stream source for the addon.

### tangerineturtle1/NX2navi
https://github.com/tangerineturtle1/NX2navi
- **Local README:** [repo-readmes/tangerineturtle1-nx2navi.md](repo-readmes/tangerineturtle1-nx2navi.md)
- **What it is:** A native x86-64 recompilation of The Legend of Zelda: Ocarina of Time (Switch 2, v1.1.1) for Windows with a Vulkan renderer: native widescreen/4K, DLSS/FSR3 with frame gen, HDR, 60 fps default, in-game settings. Independent non-commercial fan project; you must supply your own legally obtained game files.
- **How it helps you:** Limited fit — off your domain (and Windows-only), though it's a fine example of a native-port project architecture.

### lightpanda-io/browser
https://github.com/lightpanda-io/browser
- **Local README:** [repo-readmes/lightpanda-io-browser.md](repo-readmes/lightpanda-io-browser.md)
- **What it is:** A headless browser written from scratch in Zig (not a Chromium fork or WebKit patch) for AI agents and automation: CDP server, agent mode, native MCP and skills, shell completion, and a CLI that can dump a URL; README claims 16x lighter and 9x faster than Chromium (execution benchmarks). AGPL-3.0.
- **How it helps you:** Directly relevant to your browser/agent automation (Hermes, zen-mcp): a lighter CDP-compatible target for scrape/login flows — just check AGPL terms if you plan to bundle it.

### ag-ui-protocol/ag-ui
https://github.com/ag-ui-protocol/ag-ui
- **Local README:** [repo-readmes/ag-ui-protocol-ag-ui.md](repo-readmes/ag-ui-protocol-ag-ui.md)
- **What it is:** An open, lightweight, event-based protocol that standardizes how AI agents connect to user-facing apps: one bi-directional event stream where the agent emits typed events (streaming tokens, tool calls mid-response, shared state, human-in-the-loop, subagents) and any client renders them. 1.0 has a frozen spec + JSON Schema with generated TypeScript, Python and .NET SDKs; it works with LangChain, CrewAI, Mastra, Google ADK, Microsoft Agent Framework, Pydantic AI and others, across web, mobile, terminal and Slack clients. MIT.
- **How it helps you:** The protocol layer for your agent/skill/MCP work when you want an agent to drive a real UI (web, terminal, mobile) instead of just a CLI — worth tracking as you build the Zen/BiDi + agent flows. It's infrastructure, not a 3090-serving tool, so it doesn't change your local serving setup.

### HKUDS/CLI-Anything
https://github.com/HKUDS/CLI-Anything
- **Local README:** [repo-readmes/hkuds-cli-anything.md](repo-readmes/hkuds-cli-anything.md)
- **What it is:** 'CLI-Anything: Making ALL Software Agent-Native' — a hub (clianything.cc) that turns apps into CLI-accessible tools, so agents can drive software through command lines rather than only screens.
- **How it helps you:** A complement to your BiDi/Zen browser automation: an alternate path for letting agents operate desktop/web apps via CLI instead of pixel-level control.

### backnotprop/plannotator
https://github.com/backnotprop/plannotator
- **Local README:** [repo-readmes/backnotprop-plannotator.md](repo-readmes/backnotprop-plannotator.md)
- **What it is:** A workspace for staying in the loop with agents — shape, decide, plan, annotate and review agent runs, with a collaborative annotation layer over traces (Apache 2.0).
- **How it helps you:** A way to supervise and label the agent/skill runs you build (Zen, MCP) instead of only firing them off — useful if you want a human-in-the-loop review surface.

### trycua/cua
https://github.com/trycua/cua
- **Local README:** [repo-readmes/trycua-cua.md](repo-readmes/trycua-cua.md)
- **What it is:** 'Computer-use 2.0' — open-source drivers, cross-OS sandboxes and benchmarks for training and evaluating computer-use agents that act on a screen via mouse, keyboard and accessibility APIs (MIT).
- **How it helps you:** A reference plus eval harness if you want to push your agent automation beyond the browser into full desktop control, with portable driver code.

### milind-soni/OpenMausBot
https://github.com/milind-soni/OpenMausBot
- **Local README:** [repo-readmes/milind-soni-openmausbot.md](repo-readmes/milind-soni-openmausbot.md)
- **What it is:** An open-source 'Grok Bot' alternative that spins up a virtual machine bots can use — a self-hosted bot runtime with an isolated environment (Apache 2.0, 26k★).
- **How it helps you:** A pattern for giving agents their own sandboxed VM environment; useful conceptually for isolated agent runs, though off your main 3090 workflow.

### OpenMausBot/OpenMausBot
https://github.com/OpenMausBot/OpenMausBot
- **Local README:** [repo-readmes/openmausbot-openmausbot.md](repo-readmes/openmausbot-openmausbot.md)
- **What it is:** The upstream OpenMausBot repo (15★) — the same 'Grok Bot alternative with a virtual machine that bots can use' idea, a smaller fork of the concept behind milind-soni's more-starred version.
- **How it helps you:** Mostly a reference for the bot-VM concept; the milind-soni fork is the one to look at if anything here interests you.

## 4. Video generation

### meituan-longcat/longcat-video
https://github.com/meituan-longcat/LongCat-Video
- **Local README:** [repo-readmes/meituan-longcat-longcat-video.md](repo-readmes/meituan-longcat-longcat-video.md)
- **What it is:** LongCat-Video: a 13.6B-parameter foundational video model unifying text-to-video, image-to-video, and video-continuation, natively pretrained for minutes-long generation with Block Sparse Attention and multi-reward RLHF. Follow-on Avatar/Avatar-1.5 lines do audio-driven character video (Whisper-Large encoder, 8-step distilled inference). MIT.
- **How it helps you:** A research benchmark to watch; 13.6B won't comfortably fit a single 3090 at full precision — useful to track community quantizations and its avatar line (8-step inference is the kind of thing that would land on your card).

### FlashML-org/FreeVideo
https://github.com/FlashML-org/FreeVideo
- **Local README:** [repo-readmes/flashml-org-freevideo.md](repo-readmes/flashml-org-freevideo.md)
- **What it is:** A local inference engine for MiniMax H3 on consumer GPUs, built on OpenVDN's 8-step VDN-H3 model. Runs in as little as 8 GB VRAM + 16 GB RAM, ships as a ComfyUI plugin with launchers; an int8 path targets RTX 30 series (README: ~2.3× faster 5-second clips on a 3090). Four quality levels, minute-long videos, AI-agent integration and a timeline editor (v0.4+). Apache-2.
- **How it helps you:** The most immediately usable local video option for your 3090, and it plugs into your existing ComfyUI — check the int8 path first.

### edenfunf/reelmimic
https://github.com/edenfunf/reelmimic
- **Local README:** [repo-readmes/edenfunf-reelmimic.md](repo-readmes/edenfunf-reelmimic.md)
- **What it is:** "Show it a video you love. Get a new video in the same style." A local, multi-agent system: it decomposes a reference video (shot lengths, BPM, transitions, colors, camera moves), shows you a storyboard/plan to approve, then up to 6 Claude Code/Codex agents produce the shots in parallel with each shot reviewed by a different agent. Runs on your machine with your Claude Code/Codex. MIT.
- **How it helps you:** Local and agent-native, matching your Claude Code/MCP workflow — a strong candidate for stylized short-form video production.

### workingprototype/fuobe
https://github.com/workingprototype/Fuobe
- **Local README:** [repo-readmes/workingprototype-fuobe.md](repo-readmes/workingprototype-fuobe.md)
- **What it is:** "The open creative studio on ComfyUI": images, video, 3D and audio on open weights on your own GPU or via fal.ai/Replicate. Camera motions, effects, a Cinema studio (fly-through 3D + World mode), Layers, Image-to-3D (Pixal3D/TRELLIS.2), an AI agent, and an MCP/CLI interface. GPU-memory requirements per tool are documented (8 GB to 80 GB depending on model).
- **How it helps you:** Likely overlaps your existing ComfyUI setup; its feature catalog (camera motions, image-to-3D, the MCP interface) is worth mining even if you don't adopt it wholesale.

### JuneYaooo/rea-video
https://github.com/JuneYaooo/rea-video
- **Local README:** [repo-readmes/juneyaooo-rea-video.md](repo-readmes/juneyaooo-rea-video.md)
- **What it is:** Reverse-engineers any video shot by shot: was it filmed, AI-generated, or coded, and how to remake it. Agent-driven CLI (Python + ffmpeg), outputs a human-readable report (HTML/PDF) plus a layered `VIDEO.md` format your AI reads cheaply; optional vision-model hookup for more accurate live/AI/3D calls and per-shot reverse prompts. Apache-2.
- **How it helps you:** Useful for analyzing your Arabic streaming content (what's live vs. repackaged) and for planning remakes — fits your agent-skill building well.

### bitti-ai/slopus
https://github.com/bitti-ai/slopus
- **Local README:** [repo-readmes/bitti-ai-slopus.md](repo-readmes/bitti-ai-slopus.md)
- **What it is:** An AI media workspace: one project with Timeline, Video, Image, References and Export tabs; an agent pane (Claude Code, Codex, OpenRouter, or a local model); scene generation with work queue; references/LoRAs; LAN workers for multi-machine rendering; local generation via SlopFab (no Python, no FFmpeg). Alpha; recommends 24 GB+ VRAM.
- **How it helps you:** Borderline on your 24 GB card and still alpha — a candidate to trial if you want a higher-level wrapper around your local generation.

### mohamedelaassal/youtubevideogenerator
https://github.com/mohamedelaassal/youtubevideogenerator
- **Local README:** [repo-readmes/mohamedelaassal-youtubevideogenerator.md](repo-readmes/mohamedelaassal-youtubevideogenerator.md)
- **What it is:** "VideoGenius AI": a cloud SaaS (Laravel 12 + Vue 3 + Inertia, Docker, n8n) that automates YouTube video production end-to-end — AI script (GPT-4/Gemini), stock media selection, TTS voiceover, SEO metadata, direct channel upload, and autopilot scheduling.
- **How it helps you:** Limited fit — cloud + API keys, the opposite of your local-first stack; a reference for the product shape only.

### code-video-model/codevideomodel
https://github.com/code-video-model/CodeVideoModel
- **Local README:** [repo-readmes/code-video-model-codevideomodel.md](repo-readmes/code-video-model-codevideomodel.md)
- **What it is:** The official research repo for Code Video Model — a tech report, project page, and the CodeVideoBench dataset. The README is minimal (citation + links); only ~6 commits. Apache-2.
- **How it helps you:** Research only; nothing runnable on the 3090 from the README. (README barely populated — nothing beyond the report/dataset to claim.)

### ant-research/4DAnyone
https://github.com/ant-research/4DAnyone
- **Local README:** [repo-readmes/ant-research-4danyone.md](repo-readmes/ant-research-4danyone.md)
- **What it is:** SIGGRAPH Asia 2026: 4DAnyone turns a casual monocular video into consistent multiview video enabling 4D Gaussian Splatting reconstruction — no input camera parameters or static camera required, with flexible output views. Apache-2.
- **How it helps you:** Early research; not a practical 3090 production tool for your use case.

### neuregex/freefield
https://github.com/neuregex/freefield
- **Local README:** [repo-readmes/neuregex-freefield.md](repo-readmes/neuregex-freefield.md)
- **What it is:** Open-source Higgsfield-style studio where every app is one folder of ComfyUI workflows on open weights, covering image, video, VFX and audio; runs on Modal or your own ComfyUI. Every model ships its HF repo, size and license (app.json) plus per-phase VRAM numbers from real GPU runs; code is MIT, weights keep their own licenses. Any ComfyUI workflow can be added as an app.
- **How it helps you:** You already run ComfyUI on your 3090, so the own-GPU path is directly usable, and the recorded runs (including MiniMax H3 / FreeVideo models) are a useful VRAM reference for your generation work.

### jub0t/Concat
https://github.com/jub0t/Concat
- **Local README:** [repo-readmes/jub0t-concat.md](repo-readmes/jub0t-concat.md)
- **What it is:** Free, open-source, cross-platform video editor (0.2.11 per the README release badge), with editor overview, download page and build-from-source sections. AGPL-v3.
- **How it helps you:** A self-contained editing front-end for your video pipeline (subtitled/translated clips); AGPL applies if you redistribute or modify the source, so treat it as a tool, not something to embed.

### nexu-io/openmotion
https://github.com/nexu-io/openmotion
- **Local README:** [repo-readmes/nexu-io-openmotion.md](repo-readmes/nexu-io-openmotion.md)
- **What it is:** Full-stack agentic video generation for video recreation ("reverse engineering for any video"): AI recuts and revisions, product launches and demos, brand films, explainers, data stories, music and art visuals, talking-head edits. Runs with your local agent (Node.js 22.18+), ships 100+ Motion.md recreation guides, supports multimodal generation (images, video, music). Apache-2.0.
- **How it helps you:** Fits your agent-plus-video workflow as a recut/edit layer — local-agent driven and open source; check which model calls go to cloud vs. your 3090 before adopting.

### workingprototype/ComfyUI-Fuobe-Connect
https://github.com/workingprototype/ComfyUI-Fuobe-Connect
- **Local README:** [repo-readmes/workingprototype-comfyui-fuobe-connect.md](repo-readmes/workingprototype-comfyui-fuobe-connect.md)
- **What it is:** A ComfyUI custom node pack that lets the Fuobe studio drive a local ComfyUI (the way ComfyUI's own page does, at 127.0.0.1). Two modes: direct (an open Fuobe page sends runs to your local ComfyUI, which still rejects every other website) and pairing (approve a short code; Fuobe jobs reach ComfyUI over HTTPS with no tab open and no open port — for Safari/phones). Installs via ComfyUI-Manager or git, adds no nodes, uses ComfyUI's bundled aiohttp. MIT.
- **How it helps you:** Extends the Fuobe setup you already catalogued: it's the piece that lets a Fuobe tab control your local 3090 ComfyUI with origin checks, so the studio and your GPU share one workflow. Optional (Fuobe runs fine without it), so low-risk to try.

### staryone/motlab
https://github.com/staryone/motlab
- **Local README:** [repo-readmes/staryone-motlab.md](repo-readmes/staryone-motlab.md)
- **What it is:** 'Video as code' — canvas scenes rendered with WebCodecs in headless Chrome, plus a review viewer for iterating on video as editable code rather than a binary clip (MIT).
- **How it helps you:** An alternative mental model for your ComfyUI video work: generating and previewing video programmatically (headless) instead of through a node graph.

### openfilm/openfilm
https://github.com/openfilm/openfilm
- **Local README:** [repo-readmes/openfilm-openfilm.md](repo-readmes/openfilm-openfilm.md)
- **What it is:** An open-source AI video agent that turns any coding agent into a video agent, with editors for producing video from code and briefs (MIT).
- **How it helps you:** If you want your coding agents (Claude Code/Codex-style) to emit finished video, this is a direct fit alongside your local ComfyUI generation pipeline.

### zhouxiaoka/autoclip
https://github.com/zhouxiaoka/autoclip
- **Local README:** [repo-readmes/zhouxiaoka-autoclip.md](repo-readmes/zhouxiaoka-autoclip.md)
- **What it is:** AutoClip — an open-source AI video-clipping desktop tool (Chinese) that takes one link and auto-cuts long videos (podcasts, interviews, courses) into short clips with captions, covers and posting copy for TikTok/Douyin/Reels.
- **How it helps you:** Handy if you want to repurpose long content into short social clips; not tied to your 3090 generation stack but complements it for distribution.

## 5. Voice, TTS & audio

### microsoft/VibeVoice
https://github.com/microsoft/VibeVoice
- **Local README:** [repo-readmes/microsoft-vibevoice.md](repo-readmes/microsoft-vibevoice.md)
- **What it is:** Microsoft's open-source frontier voice AI: a TTS family (7.5 Hz continuous tokenizers, next-token diffusion with an LLM context head) and VibeVoice-ASR, a unified speech-to-text model for 60-minute long-form audio in one pass with Who/When/What structure, 50+ languages, and hotword customization; ASR is now in Hugging Face Transformers. Note: the TTS code was removed from the repo in 2025. MIT.
- **How it helps you:** The ASR side is directly useful: long-form, multilingual (Arabic included) transcription with timestamps and speaker labels is exactly the substrate for your subtitle pipeline.

### debpalash/VoiceStudio
https://github.com/debpalash/VoiceStudio
- **Local README:** [repo-readmes/debpalash-voicestudio.md](repo-readmes/debpalash-voicestudio.md)
- **What it is:** An open-source, fully local ElevenLabs alternative: voice cloning, voice design (describe a voice in words), video dubbing timed to the original, dictation, transcription, and audiobook creation, in 646 languages. Desktop app (AppImage/Electron), GGUF engines with Vulkan acceleration; AGPL-3.
- **How it helps you:** Local dubbing/translation for video is a natural complement to your subtitle work — e.g. Arabic→English dubbing on the 3090 without a cloud API.

### umlx5h/LLPlayer
https://github.com/umlx5h/LLPlayer
- **Local README:** [repo-readmes/umlx5h-llplayer.md](repo-readmes/umlx5h-llplayer.md)
- **What it is:** A language-learning media player with real-time AI subtitles (whisper.cpp or faster-whisper), real-time translation (local Ollama/LM Studio or Google/DeepL/OpenAI LLMs), dual subtitles, word-level search, a subtitle sidebar and subtitle seeking. C#/Flyleaf; GPL-3.
- **How it helps you:** A ready-made reference for the dual Arabic/English display experience you want in the addon; its "local LLM does context-aware translation" pattern is worth borrowing.

### k2-fsa/OmniVoice
https://github.com/k2-fsa/OmniVoice
- **Local README:** [repo-readmes/k2-fsa-omnivoice.md](repo-readmes/k2-fsa-omnivoice.md)
- **What it is:** Massively multilingual zero-shot TTS with a Python API and Colab example; voice cloning from reference audio/text, automatic fallback to Whisper ASR when no ref text is given, device options for Apple Silicon (mps) and Intel Arc (xpu); pip install (stable or latest). Apache-2.0.
- **How it helps you:** A drop-in local TTS option on your 3090 (CUDA) — zero-shot multilingual plus cloning fits both your TTS work and your Arabic/English content.

### nota-daw/nota
https://github.com/nota-daw/nota
- **Local README:** [repo-readmes/nota-daw-nota.md](repo-readmes/nota-daw-nota.md)
- **What it is:** Free music studio (DAW) for macOS/Windows/Linux with no subscription, account or feature tiers; README has demo, screenshots, features, install, plugin-developer and build-from-source sections. AGPL-3.0.
- **How it helps you:** Off-domain for your TTS/subtitle work — it's a music production studio, not audio tooling for video or speech; it would only pay off if you started making music.

### 0x0funky/audioghost-ai
https://github.com/0x0funky/audioghost-ai
- **Local README:** [repo-readmes/0x0funky-audioghost-ai.md](repo-readmes/0x0funky-audioghost-ai.md)
- **What it is:** A local sound-separation tool that pulls any sound out of audio/video using text prompts ("vocals", "a dog barking", "traffic"), putting each on its own track, powered by Meta's SAM-Audio running locally on your GPU with no account. v1.3: no Hugging Face account needed (models download from AudioGhost's own copies, bit-for-bit), smaller downloads (1.4/6.3 GB vs 5.1/14.9 GB), a per-track mixer with volume/mute/solo, and export as mixed WAV/FLAC/MP3 or your video with the new soundtrack; a Windows desktop app is in beta. MIT.
- **How it helps you:** A local sound-separation tool for your video pipeline on the 3090 — e.g. pulling vocals out of your Arabic streaming content or isolating music/SFX from a clip, all on-GPU with no API. Pairs naturally with your TTS/subtitle work for localized clips.

### edge0-ai/audio8_tts
https://github.com/edge0-ai/audio8_tts
- **Local README:** [repo-readmes/edge0-ai-audio8_tts.md](repo-readmes/edge0-ai-audio8_tts.md)
- **What it is:** A family of compact text-to-speech models for zero-shot voice cloning: a 0.6B "Realistic Air" line (23 languages, including Arabic, +12 over Preview) and a 0.1B line, with native local inference via llama.cpp/GGUF (streaming, one shared F32 bundle) plus PyTorch/CUDA paths. Apache-2.0.
- **How it helps you:** A direct fit for your TTS lane on the 3090 — llama.cpp GGUF means it runs on your existing stack, and Realistic Air's Arabic support (plus 23 languages) matches your Arabic/English content. Compare its VRAM footprint against your current Kokoro/OmniVoice setup before adopting.

### jamesondh/chimera-vocal-synth
https://github.com/jamesondh/chimera-vocal-synth
- **Local README:** [repo-readmes/jamesondh-chimera-vocal-synth.md](repo-readmes/jamesondh-chimera-vocal-synth.md)
- **What it is:** 'The ultimate vocal synthesizer' — sing, speak, beatbox and more; a vocal synthesis tool that goes beyond plain TTS (MIT).
- **How it helps you:** If you want expressive singing/beatbox audio for your content (rather than just spoken TTS), this is a candidate to try on the 3090.

### huggingface/open-tts-leaderboard
https://github.com/huggingface/open-tts-leaderboard
- **Local README:** [repo-readmes/huggingface-open-tts-leaderboard.md](repo-readmes/huggingface-open-tts-leaderboard.md)
- **What it is:** The evaluation scripts behind the Open TTS Leaderboard (the Hugging Face Space at hf-audio/open_tts_leaderboard) — benchmark code to score text-to-speech models on quality, speed and cost so results are reproducible across systems. Apache 2.0.
- **How it helps you:** A reference for measuring the TTS voices you generate locally (Kokoro, OmniVoice, audio8, etc.) against a common leaderboard; useful if you want to benchmark or compare your own 3090 TTS output rather than eyeball it.

## 6. Image, animation & UI

### youmind-openlab/awesome-nano-banana-pro-prompts
https://github.com/YouMind-OpenLab/awesome-nano-banana-pro-prompts
- **Local README:** [repo-readmes/youmind-openlab-awesome-nano-banana-pro-prompts.md](repo-readmes/youmind-openlab-awesome-nano-banana-pro-prompts.md)
- **What it is:** 10,000+ curated Nano Banana Pro prompts with preview images, organized and available in 16 languages, plus a web gallery and prompt-submission flow.
- **How it helps you:** A large prompt corpus to mine for structure/style vocabulary while you iterate your Qwen-Image-Edit LoRA workflow.

### xiaoyecodes/code-animation-prompts
https://github.com/XiaoyeCodes/code-animation-prompts
- **Local README:** [repo-readmes/xiaoyecodes-code-animation-prompts.md](repo-readmes/xiaoyecodes-code-animation-prompts.md)
- **What it is:** 341 code-animation style prompts (10 series) + 196 reference stills, packaged as a Claude Code/Codex skill with an offline style picker, a lightweight search script, and an HTML→MP4 frame exporter.
- **How it helps you:** A ready style vocabulary for code-generated animation; install as a skill and pair with your own render setup.

### cth9191/animate
https://github.com/cth9191/animate
- **Local README:** [repo-readmes/cth9191-animate.md](repo-readmes/cth9191-animate.md)
- **What it is:** A Claude Code skill that makes short procedural canvas videos: 7 built-in art styles (or a new one matched from your references), deterministic frame-by-frame rendering to MP4 via headless browser + ffmpeg, beat-mapped audio (your own music or a composed score), ElevenLabs voice with faster-whisper word timing, and exports in 9:16/1:1/4:5/16:9 from one piece.
- **How it helps you:** Local and agent-native; a solid option for stylized short-form clips on your machine — the storyboard check-ins match your own verification-first style.

### dozentwelve/papermorph
https://github.com/DozenTwelve/Papermorph
- **Local README:** [repo-readmes/dozentwelve-papermorph.md](repo-readmes/dozentwelve-papermorph.md)
- **What it is:** A Claude Code skill that turns books/PDFs into narrated interactive web lessons, paper-puppet films from stories, or narrated documentaries of public-domain images — all static sites, with quizzes, SCORM export, and subagent teaming for large chapters.
- **How it helps you:** A different genre from streaming, but a strong example of multi-agent skill architecture (subagents, model routing, review passes).

### alexgreensh/anidoodle
https://github.com/alexgreensh/anidoodle
- **Local README:** [repo-readmes/alexgreensh-anidoodle.md](repo-readmes/alexgreensh-anidoodle.md)
- **What it is:** "Hand-drawn art, written as code": 32 illustration styles, deterministic re-rendering, music composed in code (21 sound vocabularies, optional recorded-instrument pack), interactive web art, and a launch-film pipeline; installable in Claude Code, Codex, Grok Build. Apache-2.
- **How it helps you:** A high-quality local asset generator for motion graphics; determinism (same source, byte-identical renders) is great for versioning your creative assets.

### tejashmakwana/motionmaxxing
https://github.com/Tejashmakwana/motionmaxxing
- **Local README:** [repo-readmes/tejashmakwana-motionmaxxing.md](repo-readmes/tejashmakwana-motionmaxxing.md)
- **What it is:** "Looksmaxxing for motion graphics": an agent skill that takes AI-slop video and lifts it to motion-design quality, using GSAP/HyperFrames, a lint for motion checks, and taste/known-limits docs. Early release; limitations are spelled out (WebGL ~7–11 fps, music timing, etc.).
- **How it helps you:** A post-production pass for your AI-generated video; trial on a real clip before trusting it.

### faviovazquez/showtime
https://github.com/FavioVazquez/showtime
- **Local README:** [repo-readmes/faviovazquez-showtime.md](repo-readmes/faviovazquez-showtime.md)
- **What it is:** A local video studio for coding agents: describe a video in one sentence and the agent directs while your machine renders — ffmpeg, local Kokoro TTS, Manim, headless Chrome, plus an MCP server. No API keys, no uploads. v0.4.6, MIT, active.
- **How it helps you:** A local-first explainer pipeline you could wire into your own agent/skill workflows (and a useful reference architecture for a local "brief → video" loop).

### jastfan/explainroo-ui
https://github.com/jastfan/explainroo-ui
- **Local README:** [repo-readmes/jastfan-explainroo-ui.md](repo-readmes/jastfan-explainroo-ui.md)
- **What it is:** A no-code web studio for the Explainroo engine: write or prompt a narration, anchor visuals to spoken words, and export WebM/MP4 or a zero-dependency offline HTML player. Local voice (Kokoro), word timing (Whisper), Rough.js hand-drawn canvas, 4 themes, PWA.
- **How it helps you:** Overlaps showtime in territory; smaller and younger — a design reference more than a must-have.

### enesozturk/dimensional-drawing
https://github.com/enesozturk/dimensional-drawing
- **Local README:** [repo-readmes/enesozturk-dimensional-drawing.md](repo-readmes/enesozturk-dimensional-drawing.md)
- **What it is:** Agent skills that draw Apple-style dimensional spec sheets of your UI components — paddings, gaps, radii, layers, viewport placement — with a motion skill that animates the sheet. MIT.
- **How it helps you:** Useful only if you want formal spec sheets for the addon's UI; otherwise a nice-to-know.

### esengine/estella
https://github.com/esengine/estella
- **Local README:** [repo-readmes/esengine-estella.md](repo-readmes/esengine-estella.md)
- **What it is:** A fast 2D/3D game engine: TypeScript SDK, C++/WebAssembly core, visual editor, ECS; ships one project to web, desktop, WeChat MiniGames, playable ads, and native Android/iOS. Apache-2, very active.
- **How it helps you:** Game-engine territory; limited fit for your current projects.

### egmalt/house-planner
https://github.com/egmalt/house-planner
- **Local README:** [repo-readmes/egmalt-house-planner.md](repo-readmes/egmalt-house-planner.md)
- **What it is:** A self-hosted true-scale house planner: 2D floor plan + 3D, satellite map overlay, sewer/electrical/water/underfloor-heating layers with calculations, and a priced bill of materials. React + PHP, no database, MIT, v0.1.0.
- **How it helps you:** Off-domain for your stack — nothing here applies.

### facefusion/facefusion
https://github.com/facefusion/facefusion
- **Local README:** [repo-readmes/facefusion-facefusion.md](repo-readmes/facefusion-facefusion.md)
- **What it is:** An industry-standard face manipulation platform: face swap and lip-sync via Python, Gradio UI, job queue, 24+ models and CUDA acceleration. 30k stars, very active.
- **How it helps you:** Runs comfortably on a 3090; useful for lip-syncing dubs or face-swapped content — but mind the ethical/ToS line for streaming content.

### anomalyco/rune
https://github.com/anomalyco/rune
- **Local README:** [repo-readmes/anomalyco-rune.md](repo-readmes/anomalyco-rune.md)
- **What it is:** A native GPU-rendered Rust UI framework (own renderer, text, layout, springs) for macOS/Windows/Linux/web; every app runs headless so an agent can render to PNG, dump the element tree, and drive it with scripted input. Pre-release; MIT.
- **How it helps you:** Interesting if you later build agent-driven desktop apps; not relevant to your current toolchain.

### scenario-labs/skills
https://github.com/scenario-labs/skills
- **Local README:** [repo-readmes/scenario-labs-skills.md](repo-readmes/scenario-labs-skills.md)
- **What it is:** Agent skills that drive Scenario's cloud MCP for image/video/audio/3D/textures generation (model picking, pricing-before-spending, consistency), plus "expert tool" skill families that drive local DCCs — Blender, Maya, ZBrush, Unreal, Unity, Godot, Roblox.
- **How it helps you:** A good map of what agent skills for media generation look like, but cloud/API-key based — your local-first stack would prefer the local alternatives above.

### ppmpreetham/BUI
https://github.com/ppmpreetham/BUI
- **Local README:** [repo-readmes/ppmpreetham-bui.md](repo-readmes/ppmpreetham-bui.md)
- **What it is:** Blender's user interface, decoupled into a standalone UI library with a C core; bindings for Python (including running tkinter unchanged), Rust, JavaScript/React, Dear ImGui and C. GPU or CPU rendering with dirty-region "damage" redraw. GPL-2.
- **How it helps you:** A UI-library curiosity; limited fit for your work.

### Brandon-Collins7/sketchvlm
https://github.com/Brandon-Collins7/sketchvlm
- **Local README:** [repo-readmes/brandon-collins7-sketchvlm.md](repo-readmes/brandon-collins7-sketchvlm.md)
- **What it is:** Research code (EMNLP 2026 Main, arXiv 2604.22875) for vision-language models that annotate images to explain their thoughts and guide users; README includes an interactive demo, setup, and inference examples (multi-turn/stepwise) with grid/inference/task/output parameters. No license is stated in the README or the main/master tree.
- **How it helps you:** Useful as a reference for VLM-driven image annotation pipelines; it's a research-grade demo rather than a production 3090 workload, so fit is limited.

### rxjfighting/SceneMosaic
https://github.com/rxjfighting/SceneMosaic
- **Local README:** [repo-readmes/rxjfighting-scene-mosaic.md](repo-readmes/rxjfighting-scene-mosaic.md)
- **What it is:** Turns a single indoor image into a complete, editable 3D scene: perception, promptable segmentation, per-object 3D reconstruction, inter-object relation extraction and scene evolution, publishing scene variants as .glb; requires pinned submodules (sam3, sam-3d-objects) and an OpenAI-compatible API. MIT.
- **How it helps you:** Off-domain for your subtitle/LLM/TTS work; it would only pay off if you wanted 3D scene assets for your streaming content.

### Yuan-ManX/open-motion
https://github.com/Yuan-ManX/open-motion
- **Local README:** [repo-readmes/yuan-manx-open-motion.md](repo-readmes/yuan-manx-open-motion.md)
- **What it is:** AI-native motion runtime: a live web-native execution surface paired with a complete motion-graphics engine (motion blur, null objects, trim paths, repeaters, echoes, time remapping), plus checkpoint-rollback semantics, full-text search over entities, plan-then-execute orchestration and an MCP-native agent surface. v1.0.0, MIT.
- **How it helps you:** Partial fit: an MCP-native animation runtime for web/agent UI work (your zen-mcp/BiDi, agent-surface side), not for the video pipeline itself.

### nexu-io/motion-anything
https://github.com/nexu-io/motion-anything
- **Local README:** [repo-readmes/nexu-io-motion-anything.md](repo-readmes/nexu-io-motion-anything.md)
- **What it is:** Local-first, chat-native motion engine: generate animated pages and launch videos from one sentence, then edit motion on a running page component-by-component; 4 triggers, 13 motion verbs, spring easing and a keyframe editor, 403 curated recipes, 8 coding-agent engines plus BYOK (Claude Code, Codex, Hermes, others). Exports JSON, CSS, React, Lottie, MP4, GIF and portable skills. Apache-2.0, zero npm dependencies.
- **How it helps you:** Partial fit: an agent-driven animation layer (Hermes is a built-in engine) for your UI/agent work; its MP4/GIF/Lottie exports can feed your video pipeline.

### nexu-io/open-design
https://github.com/nexu-io/open-design
- **Local README:** [repo-readmes/nexu-io-open-design.md](repo-readmes/nexu-io-open-design.md)
- **What it is:** Collaborative AI design agent workspace with a desktop app and one-line install into coding agents (claude, codex, hermes, cline, others); core pages cover prototypes (web/desktop/mobile), live artifacts and dashboards, decks, images and video/HyperFrames with agent-native motion. README reports 100K GitHub stars; Apache-2.0 with extensible skills, templates and plugins.
- **How it helps you:** Partial fit: installs into your Hermes/agent workflow as a UI/design agent — useful for prototyping your Kodi addon UI, not for the subtitle/video pipeline itself.

### talsiach/take-one
https://github.com/talsiach/take-one
- **Local README:** [repo-readmes/talsiach-take-one.md](repo-readmes/talsiach-take-one.md)
- **What it is:** A Claude Code skill that turns one line ("make me a launch video") into a finished short film/launch video/ad/music video: idea, script, visuals, voice, music, edit and review, then a review room where your notes reshape the cut. It reads your product site for look and real lines, studies any reference you give, and offers "run to a finished take" or staged (storyboard → frames → first cut → final). Install via `npx skills add talsiach/take-one`; needs Claude Code, Node 18+, Chrome, ffmpeg; so far macOS only. MIT.
- **How it helps you:** A strong fit for your creative/web side — the "one-line brief → rendered video" local-agent pipeline you were mining showtime/fuobe for. Caveat: it's currently macOS-only and leans on cloud image/video models, so on this NixOS box it's a design reference more than a 3090-native tool.

### mankidev/antialgorithm
https://github.com/mankidev/antialgorithm
- **Local README:** [repo-readmes/mankidev-antialgorithm.md](repo-readmes/mankidev-antialgorithm.md)
- **What it is:** A Claude Code skill for creative work (names, copy, story, game ideas, posters, UI) that deliberately moves the model away from its first, most average pick. `seed.py` rolls a starting point, `moves.py` logs the main move behind each off-default answer so it doesn't reuse one that worked before, `rough.py` shakes straight lines/spacing for a hand-made look, and `check.py` renders an SVG at full + icon size to flag text that overflows, overlaps, has low contrast or is too small. Python 3 (check.py needs numpy, Pillow, rsvg-convert/cairosvg). MIT.
- **How it helps you:** Useful for the design/copy side of your creative work — the "don't give me the average answer" bias suits playful kids-style or branded design, and check.py's SVG rendering ties into your local render setup.

### Ciao1019/ArcMD
https://github.com/Ciao1019/ArcMD
- **Local README:** [repo-readmes/ciao1019-arcmd.md](repo-readmes/ciao1019-arcmd.md)
- **What it is:** A native, fast Markdown/rich-text editor written in pure Go + MyGo Native UI (no HTML/JS/WebView/Electron/cgo), inspired by the now-maintenance-mode Arc browser: colorful Spaces, split views, global favorites and inline formula rendering, while reading/writing standard `.md` files so they stay compatible with Obsidian, VS Code, Typora and Git. Reports 120 Hz full-frame and 0.248 ms P50 for 1M-char docs; v0.2.3 preview, macOS/Windows/Linux, MIT.
- **How it helps you:** Off the core of your stack (it's an editor, not a serving/generation tool) — a nice native app to note, but nothing here feeds your LLM/Kodi/ComfyUI pipeline.

### Remocn/remocn
https://github.com/Remocn/remocn
- **Local README:** [repo-readmes/remocn-remocn.md](repo-readmes/remocn-remocn.md)
- **What it is:** Production-ready animations, transitions, backgrounds and scenes for Remotion (the React video-rendering library).
- **How it helps you:** A shortcut for the 'video as code' path — if you adopt motlab/Remotion-style rendering, these are ready-made scene assets.

### gabrielelozupone/kokon
https://github.com/gabrielelozupone/kokon
- **Local README:** [repo-readmes/gabrielelozupone-kokon.md](repo-readmes/gabrielelozupone-kokon.md)
- **What it is:** Edit photos by describing the change, on your own GPU — a free open-source alternative to cloud image editors (AGPL 3.0).
- **How it helps you:** A local-GPU image-editing tool that fits your 3090 and complements your ComfyUI image work (textual photo editing without a cloud service).

### nilbuild/driver.js
https://github.com/nilbuild/driver.js
- **Local README:** [repo-readmes/nilbuild-driver-js.md](repo-readmes/nilbuild-driver-js.md)
- **What it is:** A lightweight, dependency-free JavaScript library for guiding user focus across a web page (MIT).
- **How it helps you:** A small utility if you build web UIs or want to steer focus in browser apps; off your core stack but easy to drop in.

## 7. Mobile & Android

### HQarroum/docker-android
https://github.com/HQarroum/docker-android
- **Local README:** [repo-readmes/hqarroum-docker-android.md](repo-readmes/hqarroum-docker-android.md)
- **What it is:** A minimal Alpine Docker image running the Android emulator as a headless service with KVM support, bundled JRE 11, ADB port-forwarding, customizable API level/device, scrcpy-compatible for remote screen control, and size-optimized build variants (API 28 emulator ≈ 1.46 GB compressed).
- **How it helps you:** Limited fit today; useful later if you want headless emulator/CI automation for Android work (sideload + test loops, e.g. for an addon you ship on Android).

### ersinkoc/phonebox
https://github.com/ersinkoc/phonebox
- **Local README:** [repo-readmes/ersinkoc-phonebox.md](repo-readmes/ersinkoc-phonebox.md)
- **What it is:** Turns an old Android phone into a customizable desk panel and touch control deck for Windows/Linux/macOS: a full-screen Android app pairs with a small desktop agent; build the panel in a browser visual editor with 124 widgets and 30 templates (PC stats, AI coding, media, automation). Shows Claude/Codex/Antigravity quotas + burn-rate forecasts, local Claude Code/Codex sessions, and GitHub reviews/CI status; works over USB or Wi-Fi, no root/account/cloud needed. .NET 10, Android 5+, MIT.
- **How it helps you:** Genuinely useful for your multi-agent setup — a phone dashboard that surfaces your Claude/Codex quotas, local agent sessions and CI status at a glance, using the Android device you already have. It's a side tool (needs an old phone + the desktop agent), not part of the 3090 pipeline.

### DuarteSantos8/openGym
https://github.com/DuarteSantos8/openGym
- **Local README:** [repo-readmes/duartesantos8-opengym.md](repo-readmes/duartesantos8-opengym.md)
- **What it is:** An open-source gym and body-weight tracker, now in the App Store (iPhone + Apple Watch) — workout logging and progress (AGPL 3.0).
- **How it helps you:** Off-domain (fitness, iOS); included only because it was open in your tabs.

### Gathin23/cleanyourtv
https://github.com/Gathin23/cleanyourtv
- **Local README:** [repo-readmes/gathin23-cleanyourtv.md](repo-readmes/gathin23-cleanyourtv.md)
- **What it is:** Debloats Android or Google TV over Wi-Fi to give an Apple-TV-style home screen — a privacy/performance cleanup for smart TVs.
- **How it helps you:** Useful if you run Android/Google TV devices (e.g., your test Android box) and want a cleaner, faster UI; otherwise off-domain.

## 8. Windows on Linux (KVM / Wine-Proton)

### brcly/legion-kvm
https://github.com/brcly/legion-kvm
- **Local README:** [repo-readmes/brcly-legion-kvm.md](repo-readmes/brcly-legion-kvm.md)
- **What it is:** Legion is a lightweight KVM runtime for running Windows apps through Proton inside a Linux guest, with a local desktop window and shared graphics. A single packaged executable bundles the guest kernel + runtime assets — NVIDIA and AMD graphics paths, guest init, CPU compatibility profiles, display/input/audio/directory sharing — and the launcher detects CPU topology to pick the graphics backend per vendor; AVX-512 is **not** a host requirement. It drops in front of Steam/Proton (`/path/to/legion %command%`) or explicitly (`legion run --proton ... --prefix ...`), sharing the prefix/home with the app; the Wayland desktop path is required. 29 stars, AGPL-3.0.
- **How it helps you:** The KVM end of the Windows-games lane your other brcly tab (linuwux-runtime) points to: if you ever want to run a Proton game on the 3090 using its NVIDIA graphics path, this is the self-contained option. It is off your current subtitle/video/LLM stack and needs `/dev/kvm` (your Hyprland session satisfies the Wayland desktop requirement), so it is a side tool, not core.

### brcly/linuwux-runtime
https://github.com/brcly/linuwux-runtime
- **Local README:** [repo-readmes/brcly-linuwx-runtime.md](repo-readmes/brcly-linuwx-runtime.md)
- **What it is:** LinUwUx is a small Rust compatibility runtime for Windows games running through Wine/Proton on Linux. It uses `LD_PRELOAD` to keep the CPU profile, Windows shared system data, clocks, signal handling and Wine env consistent across the game and its child processes — it does **not** replace Proton or modify game files/prefixes (a `linuwux` wrapper just goes in front of the normal launch command). Requirements: x86-64 Linux + glibc 2.34+, `LD_PRELOAD`, and CPU flags **UMIP disabled** + CPUID faulting (Intel 9th gen / Ryzen 3000+ disable UMIP via `clearcpuid=514`; older AMD AM4 / Steam Deck need the `cpuid_fault_emulation` DKMS module). 577 stars, AGPL-3.0.
- **How it helps you:** The Wine/Proton-compat end of the Windows-games lane (complements legion-kvm's KVM route): more surgical (a shared-object LD_PRELOAD shim rather than a full VM). But the repo's own note says it is **no longer compatible with the newest titles** (SWGR, PBZ, PZ2) and points you at [Legion-KVM](https://github.com/brcly/legion-kvm) for those — so it is the route for older Proton games, and legion-kvm is the forward path. Off your current stack either way.

## 9. Developer & security tools

### erkamyaman/rust-anything
https://github.com/erkamyaman/rust-anything
- **Local README:** [repo-readmes/erkamyaman-rust-anything.md](repo-readmes/erkamyaman-rust-anything.md)
- **What it is:** Rewrites an app in Rust one piece at a time, checked against the original's recorded behavior at every step: `record` runs the original on generated edge cases and your inputs and saves what it returns/throws; `bridge` ports and verifies. Targets CLIs, HTTP servers and libraries in TypeScript, Python, C, Go and more. New real-world port: Prettier → Rust (19× faster, 17,224 recorded runs, 0 mismatches). MIT; crates.io + npm.
- **How it helps you:** A powerful general dev tool for safely rewriting your own code to Rust (or verifying a port) with behavior tests — useful if you ever want to move a piece of the addon or tooling to Rust. Not part of the serving/creative pipeline, so it's an optional side tool.

### klippa-app/go-pdfium
https://github.com/klippa-app/go-pdfium
- **Local README:** [repo-readmes/klippa-app-go-pdfium.md](repo-readmes/klippa-app-go-pdfium.md)
- **What it is:** A fast, multi-threaded, easy-to-use PDF library for Go built on PDFium, handling the cgo/WebAssembly plumbing for you. It implements essentially all of PDFium's public API (document load/info/render, text extract/search/structured-text, creation, editing/rotating/importing pages, bookmarks/links/thumbnails/attachments, form filling, annotations, progressive rendering) with single-threaded, multi-threaded (subprocesses) or WASM modes behind one interface. MIT.
- **How it helps you:** Relevant to your Go PDF tooling (you already have pdf-render-go and pdfcpu) — if you want a higher-level PDF library in Go for rendering/extracting/editing documents, this is a solid option. It's a dev dependency, not a 3090-serving or creative tool.

### martin-olivier/airgorah
https://github.com/martin-olivier/airgorah
- **Local README:** [repo-readmes/martin-olivier-airgorah.md](repo-readmes/martin-olivier-airgorah.md)
- **What it is:** A WiFi security auditing tool written in Rust + GTK4 that can capture nearby WiFi traffic, discover clients on access points, perform deauthentication attacks, capture handshakes and PMKIDs, and crack access-point passwords. Linux only; the UI runs as a normal user (X11 or Wayland) and launches a small privileged agent via polkit for privileged operations; needs a wireless card with monitor mode + packet injection. MIT.
- **How it helps you:** Off-domain for your stack — it's a WiFi auditing tool for testing networks you own, not part of the LLM/Kodi/creative pipeline. Keep it only if you do network/security testing on your own gear.

### OpenBMB/MiniCPM-OCR
https://github.com/OpenBMB/MiniCPM-OCR
- **Local README:** [repo-readmes/openbmb-minicpm-ocr.md](repo-readmes/openbmb-minicpm-ocr.md)
- **What it is:** Fast, accurate OCR with built-in correctness assessment — a compact OCR model for reading text from images and screenshots (Apache 2.0).
- **How it helps you:** A local OCR option to pair with your vision/document work (e.g., reading screenshots or PDFs on the 3090); check its VRAM fit before assuming it runs alongside your LLM.

### tt-a1i/archify
https://github.com/tt-a1i/archify
- **Local README:** [repo-readmes/tt-a1i-archify.md](repo-readmes/tt-a1i-archify.md)
- **What it is:** Turn any idea, plan or codebase into a beautiful interactive diagram — an agent skill that generates visual architecture and UI diagrams from text (Apache 2.0).
- **How it helps you:** A skill you can drop into your agent stack to auto-document architecture or UI for your projects (Kodi addon, serving setups).

### awesome-selfhosted/awesome-selfhosted
https://github.com/awesome-selfhosted/awesome-selfhosted
- **Local README:** [repo-readmes/awesome-selfhosted-awesome-selfhosted.md](repo-readmes/awesome-selfhosted-awesome-selfhosted.md)
- **What it is:** The canonical curated list of free software network services and web applications that can be hosted on your own server.
- **How it helps you:** A reference catalog when deciding what else to run on a home/3090 box; not a tool itself.

### dream-num/univer
https://github.com/dream-num/univer
- **Local README:** [repo-readmes/dream-num-univer.md](repo-readmes/dream-num-univer.md)
- **What it is:** Build your own AI office with the Univer Office SDK — editing, calculation and collaboration for spreadsheet/document apps, written as embeddable components (Apache 2.0).
- **How it helps you:** A building block if you want document/spreadsheet capabilities in a web app; otherwise off your core stack.

### shadcn-labs/pdfcn
https://github.com/shadcn-labs/pdfcn
- **Local README:** [repo-readmes/shadcn-labs-pdfcn.md](repo-readmes/shadcn-labs-pdfcn.md)
- **What it is:** Beautiful PDF components built on Takumi and Forme — React UI pieces for PDFs, zero-config, one command (MIT).
- **How it helps you:** Front-end building blocks if you build a PDF-centric web UI; otherwise off your core stack.

### refinedev/refine
https://github.com/refinedev/refine
- **Local README:** [repo-readmes/refinedev-refine.md](repo-readmes/refinedev-refine.md)
- **What it is:** A React framework for building internal tools, admin panels, dashboards and B2B apps with a unified UI layer (MIT).
- **How it helps you:** A fast path to an admin/dashboard UI if you want to manage your self-hosted services; otherwise off your core stack.

### storytold/pdfcraft
https://github.com/storytold/pdfcraft
- **Local README:** [repo-readmes/storytold-pdfcraft.md](repo-readmes/storytold-pdfcraft.md)
- **What it is:** PdfCraft — an open-source, modern PDF reader/editor written from scratch in pure Rust (part of the ArtCraft suite), with OCR, security handlers and more (Apache 2.0).
- **How it helps you:** A capable local PDF app if you want a fast native reader/editor beyond your Kodi/Arabic workflow.

### oomol-lab/pdf-craft
https://github.com/oomol-lab/pdf-craft
- **Local README:** [repo-readmes/oomol-lab-pdf-craft.md](repo-readmes/oomol-lab-pdf-craft.md)
- **What it is:** Converts PDF files into various other formats — focused on producing outputs from PDFs (MIT).
- **How it helps you:** A conversion utility if you need to turn PDFs into other formats; distinct from storytold/pdfcraft.

### blacklanternsecurity/bbot
https://github.com/blacklanternsecurity/bbot
- **Local README:** [repo-readmes/blacklanternsecurity-bbot.md](repo-readmes/blacklanternsecurity-bbot.md)
- **What it is:** A recursive internet scanner for hackers — an open-source security/scanning tool (AGPL 3.0).
- **How it helps you:** Only relevant if you do security scanning or pentesting; otherwise off your core stack.

### c4illin/ConvertX
https://github.com/c4illin/ConvertX
- **Local README:** [repo-readmes/c4illin-convertx.md](repo-readmes/c4illin-convertx.md)
- **What it is:** A self-hosted online file converter supporting 1000+ formats (AGPL 3.0) — turn files between formats on your own server.
- **How it helps you:** A self-hosted conversion service if you want to avoid cloud converters; complements oomol-lab/pdf-craft for PDFs.

### babygoton/WorkDaddy
https://github.com/babygoton/WorkDaddy
- **Local README:** [repo-readmes/babygoton-workdaddy.md](repo-readmes/babygoton-workdaddy.md)
- **What it is:** A desktop enhancement assistant (Chinese) for WorkBuddy/CodeBuddy — multi-account backup, unattended long AI tasks, cross-account session migration.
- **How it helps you:** Off your core stack; a reference if you want to run multiple agent accounts with auto-continuity.

## Notes
- **Non-repo items:** `github.com/topics/subtitles-generator` is a topic page (indexed under Subtitles) and the komikndr gist is a setup note — both included and summarized per your ask; total = 43 repos + 2 non-repo links = 45 tabs.
- **README caveats:** `code-video-model/codevideomodel` has a minimal README (title, tech-report link, citation only) — described as research, no features claimed beyond that. All other repos' entries are based on their README content or the repo description.
- **Placement note:** `ifixai` was tabbed under Voice but is an agent-auditing tool, so it sits under LLM/Skills.
- Stars/versions mentioned are as displayed in the repos on 2026-11-13 → 2026-11-14; nothing was fabricated beyond what the READMEs state (their own measured numbers are quoted as "their measured numbers").
- **Second batch (2026-11-13):** +17 repos across 21 GitHub tabs; 4 of the tabs are repeats of repos already summarized above (Niko1221/Strata, tangerineturtle1/NX2navi, prabanta-dev/janas, volcengine/OpenViking) and are not duplicated in the index.
- **Third batch (2026-11-14):** +3 repos — the git tabs currently open in Zen (brcly/legion-kvm, brcly/linuwux-runtime, Indras-Mirror/Xolotl). Xolotl sits in the LLM-serving lane; the two brcly repos form a new "Windows on Linux (KVM / Wine-Proton)" section.
- **Fourth batch (2026-11-14):** +12 repos — the git tabs currently open in Zen (microsoft/TokenEconomizer, ag-ui-protocol/ag-ui, talsiach/take-one, mankidev/antialgorithm, ersinkoc/phonebox, Ciao1019/ArcMD, workingprototype/ComfyUI-Fuobe-Connect, 0x0funky/audioghost-ai, erkamyaman/rust-anything, edge0-ai/audio8_tts, klippa-app/go-pdfium, martin-olivier/airgorah); workingprototype/Fuobe is already catalogued and not duplicated.
- **Fifth batch (2026-11-14):** +29 repos — the git tabs currently open in Zen (cheaper-inference/OmniRoute, eagle-hq/eagle-4, google/skills, HKUDS/CLI-Anything, backnotprop/plannotator, trycua/cua, milind-soni/OpenMausBot, OpenMausBot/OpenMausBot, staryone/motlab, openfilm/openfilm, zhouxiaoka/autoclip, jamesondh/chimera-vocal-synth, Remocn/remocn, gabrielelozupone/kokon, nilbuild/driver.js, DuarteSantos8/openGym, Gathin23/cleanyourtv, OpenBMB/MiniCPM-OCR, tt-a1i/archify, awesome-selfhosted/awesome-selfhosted, dream-num/univer, shadcn-labs/pdfcn, refinedev/refine, storytold/pdfcraft, oomol-lab/pdf-craft, blacklanternsecurity/bbot, c4illin/ConvertX, babygoton/WorkDaddy, huggingface/open-tts-leaderboard); jub0t/concat was already catalogued (jub0t/Concat) and not duplicated.
- **Downloaded READMEs:** all 105 READMEs saved under `repo-readmes/`, linked from each entry; images downloaded to `repo-readmes/img/<repo>/` so each README renders offline.