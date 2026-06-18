---
name: career-timeline-pre-unity
description: PII-free professional timeline (2000-2022) extracted from the local CVs; source for retrospective posts
metadata: 
  node_type: memory
  type: reference
  originSessionId: 20dbce7b-9c8c-45c3-9928-e6b19fc13995
---

Extracted from the local, gitignored `CV *.md` files (no personal contact data copied
here). Use as factual source material for retrospective posts. See [[blog-as-portfolio]].

**Education:** ISEP Paris, engineering degree 2003, specialty "Architecture des Systèmes
Temps Réels". Prépa at Lycée Pothier, Orléans (1998-2000). Bac S 1998.

**2000-2003 — ISEP, Coupe de France de Robotique (E=M6):** electronics lead, then project
lead, then association president (team ~15). Altera EPLD odometry board from 4 odometers,
TI DSP motor servo control, serial C protocol between a Linux PC and two DSPs.

**2001 — Explo-Control** (2 mo): mixed analog/digital circuit, PCB + 2 prototypes for
industrialization. **ALM, Orléans** (6 wk): Visual C++/MFC HMI test tool for motorized
surgical tables (medical), serial protocol, English localization.

**Feb-Jul 2003 — Dassault Aviation**, Architecture Système, Saint-Cloud (end-of-studies
internship): SOPC on FPGA in VHDL; real-time video image filtering (picture-in-picture)
for a combat-aircraft display; surveyed FPGA architectures able to embed RISC cores.

**Aug 2003-Sep 2004 — INEO Systrans** (via Eurilogic), Achères: FPGA-based embedded
computer, the comms node between all bus/tram equipment (phonie, 1200-baud radio, GPS,
main computer). Wrote/simulated the whole system in VHDL solo; hardware specs; drivers in
C; comms protocols; built an automated production-line board test tool; ported the Bus
(single-computer) app to the Tram platform (two computers master/slave over RS485);
trained a 3-person software team and 4 people on board-level VHDL.

**Sep 2004 — ISEP guest lecturer** (via Eurilogic), Real-Time option (~20 final-year
students): taught "Hard/Soft integration: from FPGAs to SOPC"; wrote the course on
programmable logic, VHDL and System-On-Programmable-Chip; authored a full
build-a-UART-in-VHDL-on-Altera project.

**Sep 2004-Apr 2006 — Eurilogic Embedded**, Châtenay-Malabry: ported 4 STPC BSPs from
Windows CE 4.20 to 5.00; WinCE 5.0 demonstrator + training doc on Freescale i.MX21 ARM9;
Ethernet/serial multi-protocol gateway (Modbus/TCP-IP/UDP-IP) on a Digi Connect ARM7 for
clean-room air-particle counters; ported 2 PCI drivers to WDM (digital I/O board, I2C
audio-mux board) for XPe.

**May 2005-Apr 2006 — Renault**, Lardy (via Eurilogic): EMS2010 engine-control project;
designed/validated the dysfunctional (fault-management) architecture; fault-spec
processes, "validity indicators", failure-propagation modeling, automated pseudo-FMEA
(AMDEC).

**May 2006-2009 — INEO Systrans (ENGIE)**, Achères: low-level driver/software lead, R&D
team of 4. WinCE 5.0 kernels from Cirrus and Intel BSPs for ARM9 and x86 calculator
boards; missing I/O drivers; hardware-supervision orchestration software exposing
maintenance services to the product applications.

**2009-Mar 2018 — ENGIE INEO Systrans**, Achères: applicative embedded software for SAEIV
(public-transport fleet info systems). C++ framework + OS abstraction layers; ports across
WinCE/Linux/Android/OpenAT; CMake build system; TDD; Android apps; VoIP over Protocol
Buffers/TCP; embedded web maintenance server; async processing sequencer; automated
test-scenario engine for Jenkins then GitLab CI; set up the Git/GitLab/Jenkins workflow +
reference docs; intranet tooling (custom portal, MediaWiki, Mantis). Agile/Scrum, teams of
2-5, mentoring.

**2009-2018 (parallel, open-source on GitHub):** UE4 Git plugin (merged into UE4.7, shown
at GDC 2016 with Epic), UE Plastic SCM plugin (from UE4.11), Unreal tutorials/prototypes
(ArchViz, multiplayer, C++/Blueprints), Pac-Man in C++/SDL, CodinGame "The Great Escape",
SQLiteC++, LoggerC++, shared_ptr (C++98-compatible), an embedded C++ web server with Boost
Asio, OpenGL then Vulkan tutorials, SimplexNoise.

**Apr 2018-2022 — Darewise Entertainment**, Paris: Senior Software Engineer, Tools & Tech.
MMO "Project-C" (closed pre-alpha), team of 6. Build system (Jenkins pipelines, Python,
commandlets); maintained a fork of UE4.22 (backports, UDN coordination, upstream PRs to
Epic); SpatialOS GDK integration with Improbable; gameplay tech in C++ (game instance,
managers, config, PlayFab online services); crash analysis, profiling, networking/
replication; Unreal editor toolbars/menu extensions; Blueprint & Python APIs for tech
designers/artists; an in-client embedded web server (REST API + UI) for tooling; mentoring.

**Feb 2022 — joined Unity** (current role; see the 2022 blog post).

**Tooling seen across the embedded years:** Altera Quartus II, SOPC Builder, ModelSim;
Xilinx; TI TMS320F240 DSP; Code Composer; Platform Builder / eMbedded Visual C++; Windows
XP DDK + SoftICE; CVS (early), later SVN, Mercurial, then Git; Boost, Protocol Buffers,
SQLite3. Languages: C, C++, Assembler, VHDL, Java, Python, C#, plus the usual web/scripting.
