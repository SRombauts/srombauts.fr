---
layout: single
title: "CV (English)"
permalink: /cv-en/
toc: true
toc_label: "Contents"
toc_sticky: true
---

*This is not a concise CV but a more exhaustive reference version. My personal contact details (postal address and phone number) are intentionally omitted from the online version.*

**Sébastien Rombauts** · Senior Software Engineer, systems, tools and DevOps

[sebastien.rombauts@gmail.com](mailto:sebastien.rombauts@gmail.com) · [LinkedIn](https://www.linkedin.com/in/srombauts/) · [GitHub](https://github.com/SRombauts) · [Blog and portfolio](https://srombauts.eu/)

A software engineer with an engineering degree from ISEP (2003), I have worked on embedded systems, developer tools and the operation of Linux game servers in the cloud. My experience includes build and deployment automation (CI/CD), crash investigation and server performance analysis, as well as documentation and knowledge sharing with teams.

I am developing my cloud infrastructure and Kubernetes practice alongside my experience in systems development, tools and automation.
Admitted to **La Capsule's Cloud & DevOps Engineer programme** to build on my professional experience; see [the programme and current learning](#cloud-devops-training).

## Skills

* **Automation, build and CI/CD**: Jenkins, GitLab CI, CMake, Python and shell scripts; Yamato CI, PackageWorks and HAL at Unity; deployments by environment, branch and region.
* **Operating systems**: Linux, macOS, Windows; experience with embedded systems and hardware/software interactions.
* **Cloud and operations (LiveOps)**: SpatialOS, Google Cloud Platform (GCP), Multiplay, bare metal and cloud servers; Plastic SCM web backend deployments in Europe, the United States and Asia.
* **Infrastructure as Code (IaC)**: secondary contributions and PR reviews on Terraform infrastructure configurations at Unity.
* **Observability and diagnostics**: log and performance monitoring with Datadog, dashboards and charts created in Grafana, crash reporting, profiling and investigation of networking and replication issues.
* **Data and services**: SQL access and occasional PostgreSQL deployment, administration and monitoring; Python and BigQuery analytics pipeline; backend and payment service integration.
* **Languages**: C++, Python, C#, SQL, Bash/Batch/PowerShell.
* **Knowledge sharing**: procedure documentation, mentoring, training and technical support for teams.
* **Currently learning**: Kubernetes through practical self-study at home.
* **Engines**: Unity, Unreal Engine.
* **Libraries & APIs**: SQLite3, jsoncpp, TinyXml, SDL3, googletest, doctest, OpenGL.
* **Tools**: Unreal Profiler, Unity Version Control (UVCS, formerly Plastic SCM), Perforce, Jenkins/GitLab CI, CMake, Git, Valgrind.
* **Methods**: Agile/SCRUM, TDD, DevOps, CI/CD, Design Patterns, UML.
* **IDEs/Agents**: Visual Studio, Rider, Visual Studio Code, Cursor, Claude Code, Codex.
* **Languages (spoken)**: fluent and technical English, basic conversations in German and Spanish.

See the [additional skills](#additional-skills) at the end of the page.

## Experience

### Unity, Paris, France — Senior Software Engineer, Unity Editor package (VCS Tech team)

*July 2024 to July 2026*

**Build, CI/CD and releases**

* Updated Yamato CI configurations and the PackageWorks pipeline for Unity Version Control package releases: adapting to release requirements, checking public API compatibility and automating dependency updates.
* Integrated code coverage tools, documented the workflow and fixed tests and warnings to meet release checks.
* Made a targeted extension to HAL, Plastic SCM's historical C# CI/CD tool integrated with Jira and Slack, to test the Unity package on Bokken build virtual machines running Windows, macOS and Linux.
* Participated in the weekly release cycle: selecting a stable release, sharing manual validation across the team, then automatically publishing installers and release notes after collective approval.

**Unity Version Control package (Unity Editor, C#)**

* My first contribution shipped in release 2.0.5 (June 2023). As the team broadened to also own the Unity Editor package and the desktop applications, the Unity Version Control package for the Unity Editor (C#) became my main focus, the Unreal plugin moved into maintenance, and I contributed to the desktop and Gluon applications only occasionally.
* Owned release planning and execution across many versions (from 2.5.0 to 2.12.x), coordinating team validation and aligning releases with Unity Editor milestones, including shipping in time for Unity 6.1 at GDC 2025 and Unity 6.3 at Unite 2025.
* Designed and built a "create a code review from the plugin" feature to make branch-based workflows easier to adopt, including a reusable confirmation dialog and the related cross-platform (macOS) UI work.
* Validated the branch-merge, shelve-and-switch and shelve-view workflows, and investigated hard-to-reproduce performance and crash reports raised through customer support.

**Product analytics**

* Added Amplitude events to the Unity package and shared client code, and created dashboards and tracking charts in Amplitude.

**Unity Editor (C#)**

* Around 100 merged pull requests to the Unity Editor, plus contributions to related internal repositories.
* Reduced the cost of running automated test suites for the Editor's Version Control module and YAML merge tool.

**Unreal Engine plugin maintenance (C++)**

* Kept the plugin current with the engine: compatibility and fixes for Unreal Engine 5.5 and 5.6, with new releases shipped within a week of each engine launch.
* Fixed severe performance issues in large file-list handling.
* Diagnosed and fixed subtle authentication problems across multiple accounts that required changes to the command-line tool.
* Reworked the Create Workspace wizard UX (dropdown selection of unified organizations and projects).
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

### Unity, Paris, France — Senior Software Engineer, Unreal Engine plugin (Integration / Ecosystem team)

*February 2022 to July 2024*

**Cloud backend, multi-region deployments and DevOps (C#, SQL)**

* Made targeted changes to the plasticscm.com C# backend and ASP.NET frontend. The backend handled account creation, SSO authentication for Plastic SCM clients (desktop application, CLI, Unity package and servers), billing, Stripe payments and some APIs.
* Changes included database schema version updates; investigated performance issues with Datadog, using instrumentation set up by a squad colleague.
* Contributed to multi-region deployments of the web backend and frontend in Europe, the United States and Asia, before plasticscm.com was partly integrated into unity.com.
* Contributed to infrastructure changes in a supporting role: editing and reviewing Terraform configuration files in a Git repository, with automated deployments after PR merges.
* Cloud environment primarily on GCP, with historical AWS usage, Terraform Infrastructure as Code configurations and Kubernetes microservices which I did not administer. The environment also included Prometheus/Grafana for cluster monitoring and BigQuery/Looker for analytics.

**Unity Version Control plugin (Unreal Engine, C++)**

* Hired as the original developer of the Unity Version Control (formerly Plastic SCM) plugin for Unreal Engine, with a mandate to modernize it and migrate it to Unreal Engine 5 (C++).
* Owned the plugin end to end: feature development, customer support and releases, bringing it in line with the modern Unreal Engine 5 source-control APIs. After joining the VCS Tech team in July 2024, I continued maintaining it in parallel, including the 1.12.x releases published in 2024 and 2025.
* Added tracking events for the Unreal Engine 5 plugin in the Prometheus/Grafana environment, and created dashboards and charts in Grafana.

The Unreal plugin stayed my primary focus throughout this period, though by mid-2023 I had also begun contributing to the Unity Editor package (above).

### Darewise Entertainment, Paris, France · Lead Tech and Tools Programmer

*February 2020 to February 2022*

*MMO "Life Beyond", initially "Project-C"; Tech, Tools and Backend team.*

**Build, deployments and backend**

* Managed the tools programmer, build engineer and backend team; designed improvements to the Jenkins/Perforce pipeline and migrated scripts to Python using our internal library.
* Managed branch-based deployments across development and QA environments from the main branch, then staging and live environments from the release branch.
* Contributed fixes and improvements to the C# matchmaking backend on GCP, with PlayFab.

**Migration to GCP and Multiplay**

* Led the migration from SpatialOS to Unreal Engine's native networking and cloud infrastructure on Google Cloud Platform (GCP).
* Contributed to Unreal server deployment with Multiplay: orchestration on bare metal servers, supplemented by cloud resources to handle increased demand.

**Engineering and knowledge sharing**

* Maintained our Unreal Engine 4.26 fork, backported fixes, improved the Perforce plugin and contributed upstream with Epic Games (GitHub). Coordinated with UDN.
* Mentored programmers, tech artists and tech designers; developed Blueprint and Python APIs for their tools.
* Investigated crashes, profiled and optimized code, and diagnosed networking and replication issues.

### Darewise Entertainment, Paris, France · Senior Software Engineer, Tools & Tech

*April 2018 to February 2020*

*Initial phase of "Life Beyond" ("Project-C") on SpatialOS, within a team of 6 programmers.*

**Linux servers, build and operations**

* Initially ran our Unreal Engine dedicated game servers on the SpatialOS cloud platform.
* Integrated and maintained the SpatialOS GDK for Unreal, contributing improvements in collaboration with Improbable's technical teams.
* Developed the build system with an intern: Jenkins pipelines integrated with Perforce and Python scripts, automatically compiling and uploading the Linux game server and its debug symbols to the cloud.
* Monitored game servers and deployments on SpatialOS as part of LiveOps.

**Engineering and tools**

* Maintenance of our Unreal Engine 4.22 fork, backporting fixes, integrating plugins. Coordination with UDN. Upstream contributions with Epic Games (GitHub).
* Mentoring of junior programmers, support to tech designers, artists and animators.
* Development of toolbars & menu extensions in the Unreal editor.
* Development of Blueprint & Python APIs for tech designers & tech artists.
* Development of a web server embedded in the game client to provide tooling (UI & REST API).
* Developed the game's C++ technical layer: network infrastructure, managers and configuration; integrated PlayFab for authentication and server discovery.
* Integrated and operated a crash-reporting stack based on Unreal Crash Reporter and an open-source backend.
* Trained in GCP and BigQuery analytics and contributed to the analytics pipeline: ingestion from S3 object storage and batch processing every six hours with a Python script in Google Cloud.
* Integrated the Xsolla payment service.

**Contributions across the Darewise period (2018 to 2022)**

* Occasional work on PostgreSQL, the game server database: SQL access in the game's technical layer, deployment, administration, monitoring and configuration adjustments when investigating availability or performance issues.
* Services used in the project environment: GCP Compute, S3, PostgreSQL and BigQuery.

### Open source projects, GitHub · Library and software development

*May 2009 to present; personal projects alongside my employment.*

* Pac Man C++ / SDL, CodinGame multiplayer challenge "The Great Escape".
* [char-rnn-tensorflow](https://github.com/SRombauts/char-rnn-tensorflow) (2017): a TensorFlow experiment with a character-level LSTM language model in Python. I had discovered [char-rnn](https://github.com/karpathy/char-rnn) and Andrej Karpathy's article ["The Unreasonable Effectiveness of Recurrent Neural Networks"](https://karpathy.github.io/2015/05/21/rnn-effectiveness/) through OpenAI's publication ["Unsupervised sentiment neuron"](https://openai.com/index/unsupervised-sentiment-neuron/).
* Creator of [SQLiteCpp](https://github.com/SRombauts/SQLiteCpp), a C++ wrapper library for SQLite3, with about 2,800 GitHub stars in September 2026.
* C++ Logger, C++98-compatible shared_ptr, C++ embedded web server with Boost Asio, OpenGL then Vulkan tutorials.

### Freelance · Unreal Engine 4 plugin development (open source)

*March 2014 to February 2022*

* Git plugin for Unreal Engine 4.1, integrated officially since UE4.7; Epic Games invited me to join the Unreal Engine team at GDC 2016 in San Francisco.
* Plastic SCM plugin since Unreal Engine 4.11, integrated for UE4.24.
* Tutorials and prototypes with Unreal Engine (ArchViz, games, multiplayer, C++ and Blueprints).

### ENGIE INEO Systrans, Achères (78), France — Embedded application software development

*May 2009 to April 2018*

* Training and team leadership of 2 to 5 people (Agile SCRUM).
* Test-driven design and development (TDD) of the interface for the SAEIV public-transport operations and passenger-information system.
* Migrated the development workstations from Windows to Ubuntu, which remained our main working environment for several years. Set up Linux virtual machines and servers for internal tools.
* Built the C++ framework, OS abstraction layers, C/C++ libraries, and CMake build system, with ports to Windows CE, Linux, Android, and OpenAT.
* Contributed to the migration of the embedded computers from Windows CE to Linux, then spent several years developing and maintaining headless applications running on them.
* Android applications with a VoIP service over Protocol Buffers on TCP/IP, an embedded web maintenance server and an asynchronous task sequencer.
* Developed and deployed a crash-reporting service, first on Android and later on Linux.
* Designed and developed the automated test scenario engine for Jenkins and later GitLab CI.
* Deployed and maintained Jenkins for the Embedded R&D team, then adapted its continuous-integration processes for other teams.
* Rolled out Git across the company, then deployed GitLab CI on the virtualized infrastructure managed by IT. Established the development workflow and wrote its reference documentation.
* Administered part of the intranet, including the wiki and analytics tools, with occasional maintenance of Mantis after contributing to its initial deployment.

### ENGIE INEO Systrans, Achères (78), France — Drivers and low-level software lead

*May 2006 to May 2009*

* Lead of low-level development within an R&D team of 4 people, on the project to renew the embedded hardware range:
  * Design and development of the orchestration software for our embedded applications.
  * Writing of the validation plans for the two main computing boards (ARM9 and x86), in coordination with the electronics design office and the embedded architecture department.
  * Building Windows CE 5.0 kernels from BSPs supplied by the manufacturers and integrating additional drivers.
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

### ISEP, Paris — Final-year project

*End of 2002 to January 2003*

**Processor architecture**: designed and simulated a simplified RISC processor, defined its instruction set, and implemented its microcode.

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

### La Capsule · Cloud & DevOps Engineer {#cloud-devops-training}

*Admission confirmed, session from October 12 to December 18, 2026, 400 hours over 10 weeks, full time.*

[Official Cloud & DevOps Engineer programme, La Capsule](https://www.lacapsule.academy/program/devops-full-time). Preparation for the French professional qualification "Administrateur système DevOps" (level 6).

**Planned curriculum:**

* **Linux, systems and networking**: administration, SSH, shell scripting and infrastructure security.
* **Docker and Kubernetes (K8s)**: containerization, cluster administration, service orchestration across multiple servers, high availability and scalability.
* **Infrastructure as Code (IaC)**: Terraform and Ansible, automated server provisioning and configuration.
* **Observability and monitoring**: Prometheus, Grafana, dashboards and alerts for production services.
* **CI/CD and reliability**: automated production deployments, deployment environments and load testing; Git, GitLab and SonarQube.
* **Cloud and data**: deployment on AWS and Linode, Python programming, PostgreSQL installation and administration.
* **Practical project**: deploying an infrastructure with multiple services, security, data storage and monitoring.

### Self-study

- Recent Docker and Kubernetes practice at home.
- Started Rust tutorials in 2025, with a planned return to the subject.

### ISEP, Paris — Engineering degree (Real-Time Systems Architecture)

*2000 to 2003*

* Engineering degree (French "diplôme d'ingénieur", Master's level) from the Institut Supérieur d'Électronique de Paris (75006), specialization "Real-Time Systems Architecture".
* Computing / Electronics / Telecommunications curriculum over 3 years, entry by competitive examination.
* Preparatory classes for the French "grandes écoles" (CPGE, science track) at Lycée Pothier in Orléans (45000), 1998 to 2000.
* French Scientific Baccalauréat in 1998 (with honours).

## Additional skills

*Acquired throughout my career, particularly in embedded software, electronics and real-time systems.*

* **Languages**: C, Assembly, VHDL, Java, PHP, JavaScript, HTML5, VBA.
* **Real-time**: processor architecture, interrupt handling, low-level layers, real-time sequencers, synchronization objects and real-time drivers.
* **Hardware**: CPLD and FPGA, TI TMS320F240 DSP, embedded RISC processors with no OS.
* **Networks & protocols**: SPI, I2C, CAN, TCP/IP, UDP/IP, RS232 and RS485 serial links.

### Environments and tools used in past projects

*Kept as a record of the environments used in my previous projects.*

* **Libraries**: Boost, Protocol Buffers, Assimp, TensorFlow.
* **Operating systems**: Windows CE 5.0, Windows XP and Windows NT.
* **Software & tools**: Eclipse, Android Studio; Platform Builder and eMbedded Visual C++ for Windows CE 5; Windows XP driver development with the DDK and the Visual SoftICE debugger; Altera FPGA toolchain (Quartus II, SOPC Builder, ModelSim) and Code Composer (some Xilinx experience); GNU tools (Cygwin, binutils, gcc, Makefile, gdbtk); CVS and SVN servers and clients.
* **Methods & standards**: Merise, SART/SADT.

## Interests

* Open-source development (GitHub: C++, Unreal Engine, Machine Learning, VR).
* Woodworking: hand-built oak pieces, including a piano stand, mallets and an end-grain cutting board, taken from design and joinery to finishing. I enjoy spending this time away from a screen, while exercising the same planning and precision as engineering work.
* Gluten-free bread baking: I enjoy taking care of my sourdough levain, making custom flour and starch blends, calculating hydration, nutrition and cost-per-kg figures. See [my gluten-free recipes](https://srombauts.github.io/recettes-sans-gluten/).
* Reading science fiction; see the [reading list on this blog](https://srombauts.eu/lectures-sf/).
* Video games, drone piloting, jogging, hiking, travel.
