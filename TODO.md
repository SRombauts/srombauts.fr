# TODO — blog & portfolio backlog

Private working notes for the blog. **Not committed** (see `.gitignore`): it carries
the job-search framing that the public repo deliberately keeps out, the same way the
local `CV *.md` files stay untracked. Source material for the retrospective items lives
in those CVs.

The blog doubles as verifiable career evidence for a 2026 job search, so the bar is
substance over post count: each post should be specific and checkable, and capture the
*why* (problem solved, key decisions and trade-offs, what was learned) so it also works
as a recall aid before an interview. Verify every technical claim against the real repo
and its real dates before publishing. Pre-2010 material is written as an openly
retrospective piece (the blog's first real post is 2010-09-07), not silently backdated.

---

## 1. Portfolio repos still missing a post

Carried over from the public TODO in `_pages/portfolio.markdown`. When a post ships,
turn the portfolio bullet into a real link to it.

- [ ] **ecs** — Entity Component System experiments. <https://github.com/SRombauts/ecs>
- [ ] **SDL** — 2D experiments with SDL (see also pong-cpp-sdl below). <https://www.libsdl.org/>
- [ ] **OpenGL / gltext** — OpenGL experiments, including the small `gltext` text renderer. <https://github.com/SRombauts/gltext>
- [ ] **Ogre 3D** — Ogre3D experiments (note: an old `ogre3d-to-android` post already exists, 2011-03-12; cross-link rather than duplicate). <https://www.ogre3d.org/>
- [ ] **ZMQCpp** — ZeroMQ C++ wrapper. <https://github.com/SRombauts/ZMQCpp>

Also lacking their own post (already linked from the portfolio, worth a short write-up):

- [ ] **LoggerC++** — simple, efficient C++ logger library. <https://github.com/SRombauts/LoggerCpp>
- [ ] **HtmlBuilder** — C++ HTML DOM generator, used in a couple of embedded web services. <https://github.com/SRombauts/HtmlBuilder>

C++ libs that already have posts (do not duplicate, link instead): SQLiteC++, SimplexNoise, shared_ptr.

---

## 2. New post ideas

### 2.1 VHDL / FPGA hardware-description retrospective

The strongest gap on the blog right now: a whole early career in programmable logic and
real-time embedded that nothing public points to. Written as a clear retrospective.

Source (local CVs, factual, no confidentiality breaches):

- **Dassault Aviation, end-of-studies internship (Feb–Jul 2003)** — System-On-Programmable-Chip
  on FPGA, in VHDL: real-time video image filtering and reduction (picture-in-picture) for a
  combat-aircraft display. Surveyed FPGA architectures able to embed RISC soft cores.
- **INEO Systrans via Eurilogic (Aug 2003–Sep 2004)** — FPGA-based embedded computer, the
  communication node between all bus/tram equipment (voice, 1200-baud radio, GPS, main
  computer). Designed and simulated the whole system in VHDL solo; wrote the C drivers;
  built an automated production-line board-test tool; ported the single-computer Bus app to
  a two-computer master/slave Tram platform over RS485.
- **ISEP guest lecturer via Eurilogic (Sep 2004)** — taught "Hard/Soft integration: from
  FPGAs to SOPC" to ~20 final-year students; wrote the course on programmable logic, VHDL and
  System-On-Programmable-Chip; authored a full "build a UART in VHDL on an Altera FPGA" project.
- **ISEP robotics, Coupe de France de Robotique (2000–2003)** — Altera EPLD board computing
  the robot's displacement from 4 odometers, interfacing a TI DSP servo-control board.

Angle: what designing in a hardware-description language teaches that software does not —
true concurrency, timing/clock domains, simulation-before-silicon (ModelSim), the
hardware/software co-design mindset that still shows up in how I reason about performance
and parallelism today.

To verify before publishing: any surviving code or course material that can be shared; do
not reproduce employer-confidential specifics; keep the combat-aircraft detail at the
level already public in a CV.

Tooling to name (recruiter keywords): VHDL, Altera Quartus II, SOPC Builder, ModelSim,
Nios soft core, Xilinx, CPLD / EPLD / FPGA, SoC / SOPC, RS485.

### 2.2 AI series (publish under the [ai tag](https://srombauts.eu/tags/))

The portfolio already promises "a longer write-up series" on AI-assisted engineering. Turn
that into concrete posts.

- [ ] **Build and write up an MCP server.** Implement a small Model Context Protocol server
  (a focused, real tool, not a toy), then a post on the protocol, the design, and how it
  plugs into an agent like Claude Code. Ties directly to the existing `AGENTS.md` / skills
  story on this very site.
- [ ] **RAG / enterprise AI implementation.** Work through a Retrieval-Augmented Generation
  build (embeddings, vector store, retrieval, grounding/citations) from tutorials or
  training, framed around enterprise use (private knowledge bases, source-cited answers).
  Post the architecture and the gotchas (chunking, eval, hallucination control).
- [ ] **Reference `pong-cpp-sdl`.** Newest C++/SDL repo; add it to the portfolio SDL entry
  and consider a short post. Pairs with the older Pac-Man C++/SDL work.
  <https://github.com/SRombauts/pong-cpp-sdl> *(verify exact repo name/URL and dates)*.

### 2.3 Woodworking projects (at least a couple of posts)

A different facet worth showing: hands-on craft, planning and precision off-screen.
Each post should have decent photos plus the *why/how* (wood choice, joinery, finish,
mistakes and fixes). Verify dates and measurements before publishing.

- [ ] **Piano stand in oak planks** — design, sizing for the instrument, assembly, finish.
- [ ] **Simple single shelf in oak & resin** — wood + epoxy resin combo, pour and levelling.
- [ ] **Bicolour wooden mallets ("maillets en bois bicolore de chêne et frêne")** — a couple
  built; oak and ash, turning/glue-up, contrast of the two woods.
- [ ] **End-grain bread cutting board ("planche à découper le pain en bois de bout, en
  damier de chêne et frêne")** — more recent; checkerboard end-grain glue-up in oak and
  ash, food-safe finish.

### 2.4 Gluten-free bread baking (recipe R&D, at least one post)

Another off-screen facet that doubles as evidence of methodical, iterative work: a
French-language gluten-free recipe collection with an initial focus on bread, already
published as its own Jekyll / GitHub Pages site (same stack as this blog):
<https://srombauts.github.io/recettes-sans-gluten/>. It shows the same engineering habits
applied to the kitchen: controlled variables, measurement, iteration and documentation.

- [ ] **The gluten-free sourdough loaf.** The flagship recipe: sourdough levain, a custom
  flour/starch blend, ~92% hydration, psyllium + xanthan for structure, seeds, Dutch-oven
  bake (35 min covered at 240°C, then 20 min at 210°C). Walk through the *why* of each lever.
  <https://srombauts.github.io/recettes-sans-gluten/Pain/RecettePainLevain.html>
- [ ] **Designing a gluten-free flour blend.** The constraints driving the recipes: good
  taste, higher protein (glycaemic management), limited saturated fat, reasonable cost per
  kg. The site already carries per-100g nutrition and ingredient pricing; turn that into a
  short write-up on optimising a recipe like a small engineering problem.
- [ ] **Cross-link the site itself.** Mention `recettes-sans-gluten` from the portfolio as a
  second small Jekyll / GitHub Pages project (Just the Docs theme), alongside this blog.

Verify before publishing: exact recipe figures and dates against the live site; keep any
health/nutrition wording modest and factual (a personal recipe project, not medical advice).

---

## 3. Technology keywords to surface for recruiting filters & interviews

A checklist of strong, true keywords from the CVs that the blog should make discoverable
(in posts, tags, the about/portfolio pages). Many are absent from the site today. Used both
to pass automated CV/keyword screening and as interview-recall anchors.

| Area | Keywords (all backed by real experience) |
|------|------------------------------------------|
| Languages | C++ (incl. modern C++11/14/17), C, Python, C#, Java, VHDL, Assembler, SQL, Bash/Batch |
| Game / engine | Unreal Engine 4 & 5, Blueprints, SDL, OpenGL, Vulkan, ECS, gameplay & tools programming |
| Source control | Git, Perforce, Plastic SCM, SVN, Mercurial, CVS; **authored two official Unreal source-control plugins** |
| Build / CI / quality | CMake, Jenkins, GitLab CI, TDD, Agile/Scrum, Design Patterns, UML, code review, mentoring |
| Networking / online | TCP/IP, UDP/IP, Protocol Buffers, VoIP, SpatialOS, PlayFab, replication, REST APIs, embedded web server (Boost.Asio) |
| Embedded / real-time | RTOS concepts, interrupt handling, low-level drivers, bare-metal (no-OS) RISC, processor architecture, Windows CE / WDM / DDK |
| Hardware / FPGA | VHDL, FPGA/CPLD/EPLD, SOPC/SoC, Altera Quartus II, ModelSim, SOPC Builder, Nios, Xilinx, DSP (TI TMS320F240) |
| Buses / protocols | SPI, I2C, CAN, RS232, RS485, Modbus |
| AI-assisted engineering | AI coding agents, `AGENTS.md` / `CLAUDE.md`, reusable skills, slash commands, MCP servers, RAG (planned) |
| Platforms | Windows, Linux, Android (NDK), Windows CE |

Cross-cutting strengths worth telling as stories, not just listing: solo end-to-end
ownership (the VHDL bus/tram computer), open-source contributions merged upstream by Epic
Games (GDC 2016), training and leading small teams, and a hardware-to-AI-agents career arc
that few candidates can show.
