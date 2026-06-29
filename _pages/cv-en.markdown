---
layout: single
title: "CV (English)"
permalink: /cv-en/
toc: true
toc_label: "Contents"
toc_sticky: true
---

*This is not a concise, company-ready CV but an exhaustive reference version. My personal contact details (postal address and phone number) are intentionally omitted from the online version; to reach me, see the [About](/about/) page.*

**Sébastien Rombauts** — Senior Software Engineer

[sebastien.rombauts@gmail.com](mailto:sebastien.rombauts@gmail.com) · [github.com/SRombauts](https://github.com/SRombauts)

## Skills

* **Languages**: C++, Python, Java, C, C#, SQL, Javascript, HTML5/CSS, Bash, Batch (Go).
* **Libraries**: Boost, Protocol Buffer, SQLite3, jsoncpp, TinyXml (Assimp, TensorFlow).
* **Tools**: Unreal Profiler, Perforce, Jenkins/Gitlab CI, CMake, Git, valgrind, SVN.
* **Methods**: Agile/SCRUM, TDD, Continuous Integration, Design Patterns, UML.
* **IDEs**: Visual Studio & Visual Assist, Eclipse, Android Studio.
* **Languages (spoken)**: fluent and technical English, basics of Spanish and German.

## Technical skills — embedded / real-time period (≈ 2001 to 2009)

*Taken from my 2008 and 2013 CVs. Kept here as a record: these low-level, electronics and real-time skills no longer appear in the block above, but remain readily usable.*

* **Languages**: C, C++, Assembly, VHDL, Java, PHP, SQL, VBA.
* **Software & tools**: Visual Studio (C, C++, MFC); Platform Builder and eMbedded Visual C++ for Windows CE 5; Windows XP driver development with the DDK and the Visual SoftICE debugger; Altera FPGA toolchain (Quartus II, SOPC Builder, ModelSim) and Code Composer (some Xilinx experience); GNU tools (Cygwin, binutils, gcc, Makefile, gdbtk); CVS servers and clients.
* **Real-time**: processor architecture, interrupt handling, low-level layers, real-time sequencers, synchronization objects and real-time drivers.
* **Operating systems**: Windows CE 5.0, Windows XP-NT, Linux.
* **Hardware**: PC, CPLD and FPGA, TI TMS320F240 DSP, embedded RISC processors with no OS.
* **Networks & protocols**: SPI, I2C, CAN, TCP/IP, UDP/IP, RS232 and RS485 serial links.
* **Methods & standards**: Scrum, Merise, SART/SADT.

## Experience

### Unity, Paris, France — Senior Software Engineer (VCS Tech team)

*February 2022 to present*

* Member of the VCS Tech team: developing Unity Version Control (formerly Plastic SCM) across multiple engines (with a focus on Unity), along with the related tools and services.
* Hired as the owner and original developer of the Unity Version Control plugin for Unreal Engine 5 (C++).
* More recently focused on the Unity Version Control package for the Unity Editor (C#).
* Earlier, as part of the Integration / Ecosystem team, contributed to the plasticscm.com C# backend and ASP.NET frontend on Azure ("full stack").

**Unity Version Control package (Unity Editor, C#)**

* Owned release planning and execution across many versions (from 2.5 to 2.10), coordinating team validation and aligning releases with Unity Editor milestones, including shipping in time for Unity 6.1 at GDC 2025 and Unity 6.3 at Unite 2025.
* Designed and built a "create a code review from the plugin" feature to make branch-based workflows easier to adopt, including a reusable confirmation dialog and the related cross-platform (macOS) UI work.
* Validated the branch-merge, shelve-and-switch and shelve-view workflows, and investigated hard-to-reproduce performance and crash reports raised through customer support.
* Modernized the package CI and release pipeline: public-API compatibility checks, automated dependency updates, and a documented code-coverage workflow.

**Unity Editor (C#)**

* Around 100 merged pull requests to the Unity Editor, plus contributions to related internal repositories.
* Added Perforce Cloud support, and reduced the overhead of the Editor's version-control and YAML-merge automated test suites.

**Unreal Engine plugin (C++)**

* Kept the plugin current with the engine: compatibility and fixes for Unreal Engine 5.5 and 5.6, with new releases shipped within a week of each engine launch.
* Fixed severe performance issues in large file-list handling and authentication problems across multiple accounts, and reworked the Create Workspace wizard UX (dropdown selection of unified organizations and projects).
* Moved the plugin's distribution from the Unreal Marketplace to Fab, and shipped the "Changesets" view.

**Perforce and cross-cutting work**

* Maintained the Perforce plugin and the Editor's version-control integration: CI and infrastructure updates, Perforce Cloud support, macOS ARM64 ("Apple Silicon") and Windows long-path support.
* Extended the `cm` command-line client with unified-organization support and new check-connection options, and added its first multi-server smoke test.
* Studied a prospective new Perforce package architecture and documented the trade-offs.
* Mentoring and team practices: introduced a code-coverage workflow to the team, advocated for a stronger QA culture alongside code reviews and unit tests, revamped the package roadmap, and dogfooded Unity Version Control during HackWeek 2024.

**AI-assisted software engineering**

Spearheaded the team's AI effort to demonstrate, teach and encourage a coordinated approach:

* Hands-on practice: nearly a year of intensive daily use of Cursor (AI IDE), then Claude Code. I read, experimented, and built real prototypes (including an experimental Perforce package in C# with the UI Toolkit) while iterating on custom instructions and agent skills.
* Sharing broadly: coached teammates and gave internal Unity Talks and live demos to spread the practice across the team, rather than keeping the gains to myself.
* Raising the whole team's baseline: refined my SKILL files (AI agent instructions) into generic, performant skills and published them on the team repository, so everyone works from a shared toolkit instead of re-inventing the wheel in their own local setup. I authored the large majority of those files.

### Darewise Entertainment, Paris (75019), France — Senior Software Engineer, Tools & Tech

*April 2018 to February 2022*

* MMO "Project-C" in closed pre-alpha, within a team of 6 programmers.
* Mentoring of junior programmers, support to tech designers, artists and animators.
* Build system development (with interns): Jenkins pipelines, Python scripts, Commandlets.
* Maintenance of our Unreal Engine 4.22 fork, backporting fixes, integrating plugins. Coordination with UDN. Upstream contributions with Epic Games (Github).
* Integration and maintenance of the SpatialOS GDK plugin for Unreal, contributing improvements in collaboration with Improbable's technical teams.
* C++ game (tech) development: game instance, managers, config, PlayFab online services.
* Crash analysis, profiling & optimization, networking / replication issues.
* Development of toolbars & menu extensions in the Unreal editor.
* Development of Blueprint & Python APIs for tech designers & tech artists.
* Development of a web server embedded in the game client to provide tooling (UI & REST API).

### Open Source projects, Github — Library and software development

*2009 to March 2018*

* Git plugin for Unreal Engine 4.1, integrated officially since UE4.7; Epic Games invited me to join the Unreal Engine team at GDC 2016 in San Francisco.
* Plastic SCM plugin since Unreal Engine 4.11, being integrated for UE4.24.
* Tutorials and prototypes with Unreal Engine (ArchViz, games, multiplayer, C++ and Blueprints).
* Pac Man C++ / SDL, CodinGame multiplayer challenge "The Great Escape".
* C++ wrapper library for SQLite3, C++ Logger, C++98-compatible shared_ptr, C++ embedded web server with Boost Asio, OpenGL then Vulkan tutorials.

### ENGIE INEO Systrans, Achères (78), France — Embedded application software development

*2009 to March 2018*

* Training and team leadership of 2 to 5 people (Agile SCRUM).
* Test-driven design and development (TDD) of the SAEIV public-transport operations and passenger-information system.
* Set-up of the C++ framework and of the OS abstraction layers, of the C/C++ libraries, ports (WinCE, Linux, Android, OpenAT), and of the CMake build system.
* Android applications, a VoIP service over Protocol Buffer on TCP/IP, an embedded web maintenance server, an asynchronous task sequencer.
* Design/development of the automated test scenario engine for Jenkins then Gitlab CI.
* Set-up of the Git, Gitlab, Jenkins development workflow and reference documentation.
* Set-up of the intranet tools: custom portal, Mediawiki, Mantis.

### ENGIE INEO Systrans, Achères (78), France — Drivers and low-level software lead

*May 2006 to 2009*

* Lead of low-level development within an R&D team of 4 people, on the project to renew the embedded hardware range:
  * Design and development of the orchestration software for our embedded applications.
  * Writing of the validation plans for the two main computing boards (ARM9 and x86), in coordination with the electronics design office and the embedded architecture department.
  * Building of Windows CE 5.0 kernels from the BSPs provided by the two manufacturers Cirix and Intel, and integration of additional drivers.
  * Development/adaptation of a few missing I/O drivers.
  * Design, development and coordination of the low-level embedded hardware-supervision software, providing maintenance services to the various applications of our products.

### EURILOGIC (IT services company) — Multiple low-level development assignments

*July 2003 to May 2006*

**RENAULT, Lardy (91) — Systems engineering: fault diagnostics and degraded-mode architecture, powertrain (GMP) control**
*May 2005 to April 2006*

* Design, validation and follow-up of the implementation of the failure architecture of Renault's new engine-control system, as part of the EMS2010 project. The goal of this project is for Renault to bring back in-house the skills and the mastery of the electronics and software development processes, and in particular to master the consequences of a failure on the system:
  * Set-up of the specification processes related to failure management.
  * Processing and analysis of the data from the description forms of the "Validity Indicators" ("Indicateurs de VaLiDités").
  * Comparison and implementation of the modeling tools for failure propagation, from the triggered diagnostics to the degraded modes activated by those Validity Indicators.
  * Synthesis of this information as automated pseudo-FMEAs, analysis, comparison with reference FMEAs, and use of the results to steer/correct the developments.

**EURILOGIC, Embedded team, Chatenay Malabry (92) — Embedded software development**
*September 2004 to April 2006*

* Embedded development within a project team of 10 people:
  * Porting of 4 STPC BSPs from Windows CE 4.20 to Windows CE 5.00.
  * Building of a demonstrator and of a Windows CE 5.00 training document on a Freescale ADS i.MX21 ARM9 board.
  * Design and development of an embedded application on a Digi connect ARM7 board, implementing an intelligent multi-protocol Ethernet/serial gateway (Modbus, TCP/IP, UDP/IP) between a local network and air particle counters in cleanrooms.
  * Porting of 2 PCI drivers to XPE, to the WDM standard: digital I/O boards, and audio multiplexing boards, driven over I2C.

**ISEP, Paris (75), external lecturer for Eurilogic in the Real-Time option — Training of engineering students "Hardware/Software integration – from FPGAs to SOPCs"**
*6 days, late September 2004*

* Leading of "lectures/practical workshops" for final-year engineering students in the "Real-Time Systems Architecture" option (20 students) at the Institut Supérieur d'Électronique de Paris, on the hardware-programming aspects:
  * Writing of a course document on programmable devices, VHDL and the notion of integrating software into a "System On Programmable Chip".
  * Training of the students through lectures interspersed with practical workshops.
  * Writing of a complete project to build a UART in VHDL on an Altera FPGA.

**INEO Systrans, Achères (78), for Eurilogic — Programmable-electronics and real-time embedded-systems engineering**
*August 2003 to September 2004*

* Fixed-price contract at INEO Systrans for the hardware and software development of a computer embedded in an FPGA. Despite the technical difficulties and the complex environment of the assignment, the project resulted in a very robust and reliable computer, with particularly flexible and adaptable software. This computer is the communication node between all the equipment of the buses and trams: voice equipment, 1200-baud radio set, GPS receiver and the main computer of the embedded system:
  * Writing of the technical hardware specifications of the complete system.
  * Design and selection of the characteristics of the embedded programmable computer (team of 3 people).
  * Implementation and simulation of the whole system in VHDL (alone).
  * Integration and validation of the hardware on the production boards for hardware acceptance.
  * Design and implementation of an automated test tool for the production boards, for their inspection at the factory output.
  * Programming of the drivers to provide to the software development team.
  * Writing of the detailed software specifications, mainly the communication protocols, and writing of the software acceptance plan.
  * Development in C on this computer of the communication protocols, then complete takeover of the development and training of a new software team of 3 people within INEO Systrans embedded.
  * Involvement in the definition and conduct of the software test and validation procedures on the customer platform.
  * Writing of the documentation associated with these various steps.
  * Complete port of the Bus application (single-computer) to the Tram platform (two computers in master-slave linked by RS485).
  * Training of 4 people on the hardware-programming aspects of the computer board (VHDL).

### Dassault Aviation, Systems Architecture, Saint-Cloud (92) — End-of-studies internship: study of SOPCs on FPGA (System On Programmable Chip)

*February to July 2003*

* 6-month end-of-studies internship, of research and development concerning embedded systems on programmable electronic architectures in VHDL (FPGA type). Analysis of the competing architectures and of their recent developments allowing RISC processors to be embedded in order to build genuine avionics subsystems on a single device. Demonstration of these possibilities by developing a real-time video image filtering system (video image filtering, picture in picture, for a fighter-aircraft display):
  * Writing of the documentation associated with the analysis of the most recent technologies and the most relevant applications.
  * Specification then design of a real-time video filtering and image reduction application, for display on a fighter-aircraft display.
  * Development and detailed electronic simulation.
  * Report on the work carried out and evaluation of the possibilities demonstrated during the study, in particular the easy integration of processor(s).

### ISEP, Paris — French national robotics cup (Coupe de France de Robotique, E=M6): electronics and computing applied to robotics

*2000 to 2003 (three entries)*

* Successively in charge of electronics, then Project Lead of the ISEP team, then President of the association, responsible for the technical choices and the external relations. Teamwork and training in the constraints of a complex embedded project:
  * Design and implementation of a programmable electronic board (Altera EPLD) computing the robot's movements from 4 odometers, interfacing with a motion-control DSP.
  * Design and programming of the robot's motion control with a TI DSP on a motor-control board.
  * Design of a serial-port communication protocol in C between a Linux PC and two DSPs.
  * Writing of specification then design documents.
  * Leading of a team of 15 people, training and organization of the working meetings.

### Explo-Control, Paris — Analog and digital electronics

*2 months in 2001*

* Building of a circuit combining analog and digital components, with very strong size and cost constraints:
  * Analysis of a mock-up and of earlier schematics, adaptation to the need.
  * Building of the PCB and of 2 prototypes for industrialization.

### ALM, Orléans (45) — Human-Machine Interface programming

*Six weeks during summer 2001*

* Design then programming of a PC tool for testing and assisting the adjustment of motorized surgical operating tables (medical field) driven by DSP-based electronic boards:
  * Study of the table prototypes and analysis of the needs expressed by the staff on the production line.
  * Survey of the existing tools.
  * Design of the Human-Machine Interface.
  * Implementation in Visual C++ and MFC, coding of the serial-port communication protocol, then integration of the test tool into the existing application.
  * English translation of the software.
  * Writing of the associated documentation.

## Education

### ISEP, Paris — Engineering degree (Real-Time Systems Architecture)

*2000 to 2003*

* Engineering degree (French "diplôme d'ingénieur", Master's level) from the Institut Supérieur d'Électronique de Paris (75006), specialization "Real-Time Systems Architecture".
* Computing / Electronics / Telecommunications curriculum over 3 years, entry by competitive examination.
* Preparatory classes for the French "grandes écoles" (CPGE, science track) at Lycée Pothier in Orléans (45000), 1998 to 2000.
* French Scientific Baccalauréat in 1998 (with honours).

## Interests

* Open-source development (Github: C++, Unreal Engine, Machine Learning, VR).
* Woodworking: hand-built oak pieces, including a piano stand, mallets and an end-grain cutting board, taken from design and joinery to finishing. I enjoy spending this time away from a screen, while exercising the same planning and precision as engineering work.
* Gluten-free bread baking: I enjoy taking care of my sourdough levain, making custom flour and starch blends, calculating hydration, nutrition and cost-per-kg figures. Recipes published as its own [Jekyll site on GitHub Pages](https://srombauts.github.io/recettes-sans-gluten/).
* Video games, science-fiction reading, drone piloting, jogging, hiking, travel.
</content>
