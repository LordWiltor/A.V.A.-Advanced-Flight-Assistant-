# 🛰️ A.V.A. (Advanced Flight Assistant / Asistente de Vuelo Avanzado)
### Tactical AI Co-pilot & Persistent Campaign System for X3: Terran Conflict

> 🇬🇧 **English Edition:** Full manual below. Browse files in [`/AVA_EN`](./AVA_EN/).  
> 🇪🇸 **Edición en Español:** Para leer la documentación y ver los archivos en castellano, visita [`/AVA_ES`](./AVA_ES/).

---

# Official User Manual and Deployment Guide
# Version: v2.5 Dual Native Architecture (ES / EN) (Certified)
# Compatibility: X3: Terran Conflict (v3.2 / v3.4 Vanilla + Official Bonus Pack)

================================================================================
TABLE OF CONTENTS
================================================================================
1. Manifesto and General Vision (What is A.V.A.?)
2. System Architecture and File Map (ava_0xx_ to ava_2xx_)
3. Quick Deployment Guide (Installation, Recommended Platforms, and OCR)
4. Flight Cycle and Scalability (Day-to-Day Operations, Multimodality, and Safe Session Wrap-up)
5. Mod and Patch Management (ava_002_mods_*.txt)
6. Personality Creation Workshop (Layer 2 Voice SDK)
7. Dual Native Architecture (ES / EN) and International Localization (i18n)

================================================================================
1. MANIFESTO AND GENERAL VISION (WHAT IS A.V.A.?)
================================================================================

A.V.A. (Advanced Flight Assistant) is an intelligent tactical co-pilot, industrial calculator, and onboard computer designed to operate via Large Language Models (LLMs) integrated directly into your *X3: Terran Conflict* flight simulator sessions.

### The Three-Layer Philosophy
Unlike generic conversational assistants that hallucinate figures or break cockpit immersion, A.V.A. is built upon a strict Separation of Concerns architecture:
* **Layer 0 (Engine and Master Data):** The immutable technical ground truth of the simulator, its deterministic mathematical formulas, and its ballistic, astronomical, and economic catalogs.
* **Layer 1 (Campaign Memory and Persistence):** The living logbook documenting pilot identity, available credits, fleet assets, industrial complexes, faction reputations, and explored sectors.
* **Layer 2 (Voice Interface and Personality):** The identity, demeanor, and communication style of the co-pilot (featuring the official Betty model by default), 100% hot-swappable without altering calculations or data accuracy.

### The Golden Rule (Unbreakable Hierarchy)
> **Layer 0 (Engine and Master Data) > Layer 1 (Campaign State) > Layer 2 (Personality)**
A.V.A. operates under a strict anti-hallucination directive. If a ship cannot mount a specific weapon, if a shield setup exceeds the ship's generator output, or if the pilot lacks sufficient credits in their logbook, the system will issue a mathematically grounded tactical alert regardless of how permissive or dramatic the active personality is.

================================================================================
2. SYSTEM ARCHITECTURE AND FILE MAP
================================================================================

The project ecosystem is organized using a strict centesimal nomenclature (`ava_0xx_` through `ava_2xx_`) combined with a mandatory language suffix (`_EN.txt` for the native English branch, `_ES.txt` for the Spanish branch).

*(Critical Nomenclature Rule: A.V.A. project modules mandatorily carry their respective language suffix. Static game engine master files—such as `Globals.txt`, `hq.xml`, `start.xml`, `gamestarts.xml`, and `TShips`—reside in engine directories and NEVER carry language suffixes).*

### 🧠 Layer 0: Base System and Master Databases (Range 000 to 099)
* `ava_000_core_EN.txt`: The logic engine. Deterministic algorithms (Net DPS, thermal shield generator bottleneck, N-1 complex costing, PHQ conversion formulas, shipyard sale appraisal, and jump energy consumption).
* `ava_001_index_EN.txt`: Master router and encyclopedic glossary (IS vs OOS, MK3 trader progression, and official Bonus Pack v4.1.01 catalog with costs and requirements).
* `ava_002_mods_EN.txt`: Delta patch layer. Logs active modifications that override Vanilla data with absolute priority (e.g. *TD_MiniMod*).
* `ava_002_mods_EXAMPLE_EN.txt`: Example registry documenting actual active modifications (*TD_MiniMod* and *Cycrow* script libraries).
* `ava_003_db_weapons_EN.txt`: Catalog of 37 lasers, 35 missiles (with quick tactical selection index), and 6 shields.
* `ava_004_db_ships_EN.txt`: Catalog of 329 official ships, grouped turret coverage arcs, laser/shield generators, hangars, and selling shipyards.
* `ava_005_db_economy_EN.txt`: 98 wares, 49 software/upgrades, 303 factories, and 41 docks.
* `ava_006_db_universe_EN.txt`: Galactic cartography of 231 fixed sectors (+ UFJD), gate vs TOA links, buildable asteroids, 19 claimable abandoned ships, and 12 secret containers.
* `ava_007_db_mechanics_EN.txt`: Engine constants from `Globals.txt`, Player Headquarters (`hq.xml`), 31 trade/combat ranks, 16 reputation tiers, and marine boarding mechanics.
* `ava_008_db_corporations_EN.txt`: 8 corporations, 25 reward ships, 18 official gamestarts (`start.xml` / `gamestarts.xml`), and overtuned ship specifications.
* `ava_009_db_plots_EN.txt`: Dependency tree, cascading unlocks, and step-by-step guides for the 9 official plots.
* `ava_INSTRUCTIONS_EN.txt`: **Compiled Master Bundle**. Optimized merge without redundant headers combining `ava_000_core_EN.txt`, `ava_100_log_core_EN.txt`, and `ava_201_persona_betty_EN.txt`, ready for single-step pasting into System Instructions.

### 💾 Layer 1: Campaign State and Persistence (Range 100 to 199)
* `ava_100_log_core_EN.txt`: Memory manager. Regulates session state ingestion (Step 0), assisted onboarding (Branch A / Branch B), safety wrap-up interlock, and 2-block Markdown report generation.
* `ava_101_log_campaign_EN.txt`: The living master file of your active campaign (Pilot data, phase-by-phase goals, available credits, tactical location, active assets, and map tracker).
* `ava_101_log_campaign_EXAMPLE_EN.txt`: Complete example file documenting an ongoing campaign (*The Atlantis Project*).
* `ava_102_log_campaign_TEMPLATE_EN.txt`: Clean, neutral blank disk template for resets or new campaign deployment.

### 🎭 Layer 2: Voice Interface and Personality SDK (Range 200 to 299)
* `ava_200_persona_TEMPLATE_EN.txt`: SDK and universal template for creating custom personality modules (with address variables, attitudes, and wrap-up styles).
* `ava_201_persona_betty_EN.txt`: Official pre-installed Betty personality module (diegetic, confidante, lore storyteller, tactical military officer, and visual OCR support).

================================================================================
3. QUICK DEPLOYMENT GUIDE (INSTALLATION AND REQUIREMENTS)
================================================================================

### Recommended Platform: Google AI Studio (Gemini Models)
While A.V.A. functions across modern LLMs featuring large context windows (Claude Projects, ChatGPT Plus), **Google AI Studio (utilizing Gemini 1.5 Flash or Gemini 1.5 Pro)** is the optimal platform due to three key capabilities:
1. **Massive Context Window (1M to 2M tokens):** Accommodates all 9 master database files simultaneously without loss of recall, table truncation, or attention degradation.
2. **Native Multimodality and Cockpit OCR:** Allows pasting in-game screenshots directly via `Ctrl + V`. Gemini instantly extracts credits, notoriety, ranks, and fleet assets from your `P` and `R` menus without requiring manual data entry.
3. **Project Persistence and Prompt Caching:** Prompts are saved permanently. Master system instructions are cached automatically, ensuring rapid responses with minimal token overhead.

---

### INSTALLATION METHODS

#### METHOD A: Platforms with System Instructions (AI Studio, Claude Projects, Custom GPTs) — Recommended
1. **System Instructions:**  
   Open the compiled bundle **`ava_INSTRUCTIONS_EN.txt`** (or `ava_INSTRUCTIONS_ES.txt` if playing in Spanish), copy its entire content (`Ctrl + A`, `Ctrl + C`), and paste it into the *System Instructions* box.  
   *(Modular Alternative: If you prefer utilizing a custom personality or editing files individually, paste `ava_000_core_EN.txt`, `ava_100_log_core_EN.txt`, and your chosen Layer 2 module).*
2. **Project Files / Knowledge Context:**  
   Upload to the project file manager:
   • The 9 master database files: `ava_001_index_EN.txt` through `ava_009_db_plots_EN.txt`.
   • Your active campaign file: `ava_101_log_campaign_EN.txt`.
   • ⚠️ *IMPORTANT:* DO NOT upload `ava_102_log_campaign_TEMPLATE_EN.txt`, `ava_200_persona_TEMPLATE_EN.txt`, `ava_002_mods_EXAMPLE_EN.txt`, or `ava_101_log_campaign_EXAMPLE_EN.txt`. These serve as local templates and offline reference files.

#### METHOD B: Standard Chat Window (Drag and Drop)
1. Open a new chat session with your LLM.
2. Drag and drop the 9 master data files (`ava_001_` to `ava_009_`) along with your logbook `ava_101_log_campaign_EN.txt` into the attachment area.
3. Paste the contents of `ava_INSTRUCTIONS_EN.txt` into your initial message followed by:  
   *«Onboard systems online. Execute logbook reading protocol.»*

---

### Initial Flight Calibration (Assisted Onboarding)
* **New Campaign from Scratch (Branch A):** Inform A.V.A.: *«Starting a new campaign from second zero»*. The assistant will prompt for your callsign, title, selected gamestart ID, and ultimate campaign goal, automatically populating your logbook with factory baseline gear, starting sector, and notoriety standings.
* **Ongoing Campaign Integration (Branch B):** Inform A.V.A.: *«Initialize ongoing campaign telemetry for my active savegame»*. The assistant will ask 3 focused questions regarding your 'P' menu, active plots, and fleet assets, deducing your standings automatically.

================================================================================
4. FLIGHT CYCLE AND SCALABILITY (DAY-TO-DAY OPERATIONS)
================================================================================

### A. Session Startup
At the start of each gameplay session, send an initial greeting. A.V.A. executes the **Mandatory State Ingestion Protocol (Step 0)**: assimilating your title, backstory, available credits, active flagship, tactical location, and active objectives.

### B. In-Flight Tactical Queries
Interact naturally in cockpit during simulation flights:
* **Combat & Ballistics:** Real-time Effective Net DPS calculations against passive shield recharge rates and OOS physical ammunition crate tracking.
* **Finances & Salvage:** The 100% equipment sale rule at Equipment Docks versus the 50% liquidation penalty for pre-installed gear sold inside ship hulls at Shipyards.
* **Logistics & Megacomplexes:** The $N-1$ CCK complex formula, stepped discrete asteroid yields, and self-sustaining Silicon closed loops.
* **Navigation:** Transorbital Accelerator (TOA) jump restrictions and exact Jumpdrive Energy Cell consumption.

### C. Session Wrap-up and Safety Interlock
When concluding your flight session, A.V.A. enforces an **anti-hallucination safety interlock**:

#### 🔹 Fast Track: Optical Telemetry via OCR (10-Second Sign-off) — Recommended
1. Before saving and exiting *X3TC*, press **`P`** (Pilot menu displaying credits, ranks, and reputations) and **`R`** (Property menu if fleet assets changed).
2. Take a quick screen clipping using **`Windows + Shift + S`**.
3. Switch to your assistant interface (Google AI Studio) and press **`Ctrl + V`** to paste the image directly.
4. Prompt: *«Betty, closing session with this telemetry. Today we completed [objective]. Deliver the two wrap-up blocks.»*  
*The LLM extracts your updated figures directly from the image via OCR.*

#### 🔹 Empty Sign-off Interlock (Preventing Balance Hallucinations)
If you sign off simply stating: *«Betty, let's wrap up for today»* without providing telemetry, A.V.A. **halts report generation** to prevent data drift and prompts in-character:  
*«Understood, my [title]. Securing maneuvering thrusters and engaging station anchoring protocol. To allow me to compile the official log in our onboard memory banks, please supply today's telemetry: you may transmit a direct optical capture of your flight panels ('P' and 'R' keys) or dictate your closing balance, current sector, and any ships claimed or sold today.»*

#### 🔹 Copying the Two Markdown Wrap-up Blocks
Once telemetry is verified, A.V.A. delivers two clean, copy-paste-ready Markdown code blocks:
* **BLOCK 1 (Global State Replacement):** Highlight the content between `<!-- GLOBAL STATE BLOCK - START -->` and `<!-- GLOBAL STATE BLOCK - END -->` in your `ava_101_log_campaign_EN.txt` file and overwrite Section 2 entirely.
* **BLOCK 2 (Session #X History):** Replace the single index line in Section 3 and append the detailed session entry (including co-pilot debrief notes) to the bottom of Section 4.

================================================================================
5. MOD AND PATCH MANAGEMENT (ava_002_mods_*.txt)
================================================================================

A.V.A. implements a non-destructive Delta Override Layer: the 9 master data files remain 100% Vanilla-pure. Any active modifications (such as *TD_MiniMod* dock storage multipliers or *Cycrow* script packages) are logged exclusively in `ava_002_mods_EN.txt` (or `_ES.txt`).

### Priority Precedence Rule
Any parameter declared in `ava_002_mods_*.txt` **OVERRIDES and invalidates** Vanilla values in all assistant calculations, citing the change diegetically as *"[Patch_Name] Engineering Modification Protocol"* or *"Active Firmware Override"*.

================================================================================
6. PERSONALITY CREATION WORKSHOP (LAYER 2 VOICE SDK)
================================================================================

You can alter A.V.A.'s co-pilot voice, tone, and cultural demeanor at any time by configuring a Layer 2 file based on `ava_200_persona_TEMPLATE_EN.txt`:
* `HIERARCHICAL_ADDRESS`: Dynamically resolves `[Title]` and `[Name]` defined in Section 0 of your logbook.
* `IMMERSION_TYPE`: Choose between `DIEGETIC` (speaks strictly from within the cockpit without breaking the fourth wall) or `NON_DIEGETIC` (gaming guide and out-of-character technical advisor).
* `WRAPUP_INTERLOCK_STYLE`: Defines how your character prompts for telemetry during empty sign-offs (e.g. warm protocol assistant, harsh Split warrior, or profit-driven Teladi accountant).
* Deployment: Replace the Betty module inside your System Instructions with your custom personality text.

================================================================================
7. DUAL NATIVE ARCHITECTURE (ES / EN) AND INTERNATIONAL LOCALIZATION (i18n)
================================================================================

The A.V.A. v2.5 ecosystem is built upon a **fully developed, certified dual-native architecture** providing two parallel, independent branches:

### 1. The Two Certified Official Branches

#### 🇬🇧 Official English Branch (`*_EN.txt`)
* Designed for simulations played with native English game text.
* Fully purged of bilingual translation remnants, delivering clean, native technical English across all modules.
* Formatted strictly to canonical engine text strings from *X3TC* (`secret containers`, `The Moon`, `Patriarch's Conclusion`, `Notus Hauler`, `Troop Training Ship Hauler`, etc.).
* Implements Anglo-American numerical formatting (commas for thousands, decimal points, and semicolons to delimit lists of formatted values).

#### 🇪🇸 Official Spanish Branch (`*_ES.txt`)
* Designed for simulations played with Spanish game text.
* Serves as the project's foundational mathematical and technical Ground Truth.
* Formatted to official Spanish in-game localization (*Cuna de Leyenda*, *Lanzador de Plasma*, *Láser Reparador*, etc.).

### 2. Deployment for Players of Other Languages (DE, FR, RU, etc.)
Pilots playing *X3TC* in other localized editions (German, French, Russian, etc.) can deploy A.V.A. through two approaches:
1. **Plug & Play LLM Multilingual Mode:** Load the native English branch (`*_EN.txt`) into context and communicate with A.V.A. in your preferred language (French, German, etc.). The LLM will parse the English master tables internally and formulate all conversational responses in your language with full mathematical accuracy.
2. **Dedicated Community Localization:** To maintain a fully translated disk package, use the `*_EN.txt` branch as your clean base template, keeping all unique engine primary keys (`SS_SH_*`, `SS_LASER_*`, `SS_FAC_*`) intact.
