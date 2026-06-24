---
layout: single
title: "CV (français)"
permalink: /cv-fr/
toc: true
toc_label: "Sommaire"
toc_sticky: true
---

*Ceci n'est pas un CV résumé conforme aux attentes des entreprises, mais une version exhaustive conservée comme référence. Mes coordonnées personnelles (adresse postale et téléphone) sont volontairement omises de la version en ligne ; pour me contacter, voir la page [About](/about/).*

**Sébastien Rombauts** — Ingénieur logiciel expérimenté

[sebastien.rombauts@gmail.com](mailto:sebastien.rombauts@gmail.com) · [github.com/SRombauts](https://github.com/SRombauts)

## Compétences

* **Langages** : C++, Python, Java, C, C#, SQL, Javascript, HTML5/CSS, Bash, Batch (Go).
* **Bibliothèques** : Boost, Protocol Buffer, SQLite3, jsoncpp, TinyXml (Assimp, TensorFlow).
* **Outils** : Unreal Profiler, Perforce, Jenkins/Gitlab CI, CMake, Git, valgrind, SVN.
* **Méthodes** : Agile/SCRUM, TDD, Intégration Continue, Design Patterns, UML.
* **IDE** : Visual Studio & Visual Assist, Eclipse, Android Studio.
* **Langues** : Anglais courant et technique, bases d'Espagnol et d'Allemand.

## Compétences techniques — période embarqué / temps réel (≈ 2001 à 2009)

*Reprises de mes CV de 2008 et 2013. Conservées ici comme trace : ces compétences bas niveau, électronique et temps réel ne figurent plus dans le bloc ci-dessus, mais restent mobilisables.*

* **Langages** : C, C++, Assembleur, VHDL, Java, PHP, SQL, VBA.
* **Logiciels & outils** : Visual Studio (C, C++, MFC) ; Platform Builder et eMbedded Visual C++ pour Windows CE 5 ; développement de drivers Windows XP avec le DDK et le débogueur Visual SoftICE ; chaîne de développement FPGA d'Altera (Quartus II, SOPC Builder, ModelSim) et Code Composer (expérience de Xilinx) ; outils GNU (Cygwin, binutils, gcc, Makefile, gdbtk) ; serveurs et clients CVS.
* **Temps réel** : architecture des processeurs, gestion d'interruptions, couches basses, séquenceurs temps réel, objets de synchronisation et drivers temps réels.
* **Systèmes** : Windows CE 5.0, Windows XP-NT, Linux.
* **Matériels** : PC, CPLD et FPGA, DSP TI TMS320F240, processeurs RISC embarqués sans OS.
* **Réseaux & protocoles** : SPI, I2C, CAN, TCP/IP, UDP/IP, séries RS232 et RS485.
* **Méthodes & normes** : Scrum, Merise, SART/SADT.

## Expérience

### Unity, Paris, France — Senior Software Engineer (équipe VCS Tech)

*Février 2022 à aujourd'hui*

* Membre de l'équipe VCS Tech : développement de Unity Version Control (Plastic SCM) sur plusieurs moteurs (avec une focalisation sur Unity), ainsi que des outils et services associés.
* Recruté comme propriétaire et développeur initial du plugin Unity Version Control pour Unreal Engine 5 (C++).
* Plus récemment, focalisé sur le package Unity Version Control pour l'éditeur Unity (C#).
* Travaux d'intégration Outils & CI/CD sur Github, liés à l'infrastructure Unity et au pipeline de publication des packages.
* Maintenance du plugin Perforce et de l'intégration du contrôle de version dans l'éditeur Unity.
* Auparavant, au sein de l'équipe Integration / Ecosystem, contribution au backend C# et au frontend ASP.NET de plasticscm.com sur Azure (« full stack »).

**Ingénierie logicielle assistée par IA**

* Usage quotidien intensif de Cursor (IDE IA) pendant près d'un an, puis de Claude Code.
* Package Perforce expérimental construit avec l'UI Toolkit, en m'appuyant sur Cursor pour accélérer le prototype (C#).
* Pilotage de l'effort IA de l'équipe pour montrer, former et encourager une démarche coordonnée ; rédaction de la grande majorité de nos fichiers SKILL (instructions pour agents IA).
* Présentation de quelques Unity Talks internes sur la rédaction de fichiers SKILL.md pour Claude Code.

### Darewise Entertainment, Paris (75019) — Senior Software Engineer, Tools & Tech

*Avril 2018 à février 2022*

* MMO « Project-C » en pre-alpha fermée, au sein d'une équipe de 6 programmeurs.
* Mentorat de programmeurs juniors, assistance aux tech designers, artists et animateurs.
* Dev (avec stagiaires) du système de build : pipelines Jenkins, scripts Python, Commandlets.
* Maintenance de notre fork d'Unreal Engine 4.22, backport de correctifs, intégration de plugins. Coordination avec UDN. Contributions amont avec Epic Games (Github).
* Intégration et maintenance du plugin SpatialOS GDK pour Unreal, contributions d'améliorations en collaboration avec les équipes techniques d'Improbable.
* Dev C++ du jeu (tech) : game instance, managers, config, PlayFab online services.
* Analyse de crash, profiling & optimisations, problématiques réseau / réplication.
* Développement de barres d'outils & extensions de menus dans l'éditeur Unreal.
* Développement d'APIs Blueprint & Python pour les tech designers & tech artists.
* Développement d'un serveur web intégré au client du jeu pour l'outiller (UI & API REST).

### Projets Open Source, Github — Développement bibliothèques et logiciels

*2009 à mars 2018*

* Plugin Git pour Unreal Engine 4.1, intégré depuis UE4.7 (GDC 2016 avec Epic Games).
* Plugin Plastic SCM depuis Unreal Engine 4.11, en cours d'intégration pour UE4.24.
* Tutoriels et prototypes avec Unreal Engine (ArchViz, jeux, multi, C++ et Blueprints).
* Pac Man C++ / SDL, challenge multi CodinGame « The Great Escape ».
* Bibliothèque C++ wrapper de SQLite3, Logger C++, shared_ptr compatible C++98, serveur web embarqué en C++ avec Boost Asio, tutoriels OpenGL puis Vulkan.

### ENGIE INEO Systrans, Achères (78) — Développement logiciels applicatifs embarqués

*2009 à mars 2018*

* Formation et encadrement en équipe de 2 à 5 personnes (Agile SCRUM).
* Conception, développement dirigés par les tests (TDD) du SAEIV (transports en commun).
* Mise en place du framework C++ et des couches d'abstraction de l'OS, des bibliothèques C/C++, portages (WinCE, Linux, Android, OpenAT), du build-système CMake.
* Applications Android, service de VoIP en Protocol Buffer sur TCP/IP, serveur de maintenance Web embarquée, séquenceur de traitements asynchrones.
* Conception/dev du moteur de scénarios de tests automatiques pour Jenkins puis Gitlab CI.
* Mise en place du workflow de développement Git, Gitlab, Jenkins et Doc de référence.
* Mise en place des outils de l'intranet : portail custom, Mediawiki, Mantis.

### ENGIE INEO Systrans, Achères (78) — Responsable drivers et logiciels bas niveau

*Mai 2006 à 2009*

* Responsable des développements bas niveau au sein d'une équipe R&D de 4 personnes, sur le projet de renouvellement de la gamme de matériel embarqué :
  * Conception et développement du logiciel d'orchestration de nos applications embarquées.
  * Rédaction des plans de validation des deux cartes calculatrices principales (ARM9 et x86), en coordination avec le bureau d'études électroniques et le service d'architecture embarqué.
  * Réalisation de noyaux Windows CE 5.0 à partir des BSP fournis par les deux constructeurs Cirix et Intel, et intégration de drivers supplémentaires.
  * Développement/adaptation de quelques drivers d'E/S manquants.
  * Conception, développement et coordination du logiciel embarqué bas niveau de supervision du hardware, fournissant des services de maintenance aux différentes applications de nos produits.

### EURILOGIC (société de services) — Multiples missions de développement bas niveau

*Juillet 2003 à mai 2006*

**RENAULT, Lardy (91) — Ingénierie synthèse architecture Diagnostics et Modes Dégradés Contrôle GMP**
*Mai 2005 à avril 2006*

* Conception, validation et suivi de la mise en œuvre de l'architecture dysfonctionnelle du nouveau système de contrôle moteur de Renault, dans le cadre du projet EMS2010. Ce projet a pour objectif une reprise par Renault des compétences et de la maîtrise des processus de développement électroniques et logiciels, et en particulier de maîtriser les conséquences d'une défaillance sur le système :
  * Mise en place des processus de spécification relatifs à la maîtrise des pannes.
  * Traitement et analyses des données issues des formulaires de descriptions des « Indicateurs de VaLiDités ».
  * Comparaisons et mise en œuvre des outils de modélisation de la propagation des défaillances, des diagnostics déclenchés jusqu'aux modes dégradés activés par ces Indicateurs de VaLiDités.
  * Synthèse de ces informations sous forme de pseudo AMDEC automatisées, analyse, comparaison aux AMDEC types et exploitation des résultats pour diriger/corriger les développements.

**EURILOGIC, équipe Embedded, Chatenay Malabry (92) — Développements logiciels embarqués**
*Septembre 2004 à avril 2006*

* Développements embarqués au sein d'une équipe projets de 10 personnes :
  * Portage de 4 BSP STPC depuis Windows CE 4.20 vers Windows CE 5.00.
  * Réalisation d'un démonstrateur et d'un document de formation de Windows CE 5.00 sur carte Freescale ADS i.MX21 ARM9.
  * Conception et développement d'une application embarquée sur carte Digi connect ARM7 réalisant une interface Ethernet/Série intelligente et multi-protocoles (Modbus, TCP/IP, UDP/IP) entre réseau local et compteurs de particules dans l'air en salles blanches.
  * Portage de 2 drivers PCI pour XPE, au standard WDM : cartes d'entrées-sorties TOR, et cartes de multiplexage audio, pilotées par I2C.

**ISEP, Paris (75), intervenant extérieur Eurilogic en option Temps Réel — Formation d'élèves ingénieurs « Intégration Hard/Soft – des FPGA aux SOPC »**
*6 journées, fin septembre 2004*

* Encadrement « Cours/Ateliers Pratiques » des élèves ingénieurs en dernière année dans l'option « Architecture des Systèmes Temps Réels » (20 élèves) à l'Institut Supérieur d'Électronique de Paris, sur les aspects programmation du matériel :
  * Rédaction d'un document de cours sur les composants programmables, le VHDL et la notion d'intégration de Soft dans un « System On Programmable Chip ».
  * Formation des étudiants sous forme de cours entrecoupés d'ateliers pratiques.
  * Rédaction d'un projet complet de réalisation d'une UART en VHDL sur un FPGA d'Altera.

**INEO Systrans, Achères (78), pour Eurilogic — Ingénierie électronique programmable et système temps réel embarqué**
*Août 2003 à septembre 2004*

* Forfait chez INEO Systrans pour le développement matériel et logiciel d'un calculateur embarqué dans un FPGA. Malgré les difficultés techniques et l'environnement complexe de la mission, le projet a débouché sur un calculateur très robuste et fiable, au logiciel particulièrement souple et adaptable. Ce calculateur est le nœud de communication entre tous les équipements des bus et des tramways : équipements de phonie, poste radio 1200 bauds, récepteur GPS et calculateur principal du système embarqué :
  * Rédaction des spécifications matérielles techniques du système complet.
  * Conception et choix des caractéristiques du calculateur programmable embarqué (équipe de 3 personnes).
  * Réalisation et simulation de l'ensemble du système en VHDL (seul).
  * Intégration et validation du matériel sur les cartes de série pour la recette matérielle.
  * Conception et réalisation d'un outil de tests automatiques des cartes de série pour leur contrôle en sortie d'usine.
  * Programmation des drivers pour fourniture à l'équipe de développement logiciel.
  * Rédaction des spécifications précises du logiciel, principalement des protocoles de communication, et rédaction du cahier de recette logicielle.
  * Développement en C sur ce calculateur des protocoles de communication, puis reprise complète du développement et formation d'une nouvelle équipe logicielle de 3 personnes au sein d'INEO Systrans embarqué.
  * Implication dans la définition et le déroulement des procédures de tests et de validation du logiciel sur plate-forme client.
  * Rédaction de la documentation associée à ces différentes étapes.
  * Portage complet de l'application Bus (mono-calculateur) vers la plate-forme Tramway (deux calculateurs en maître-esclave liés par RS485).
  * Formation de 4 personnes sur les aspects programmation matérielle de la carte calculateur (VHDL).

### Dassault Aviation, Architecture Système, Saint-Cloud (92) — Stage de fin d'études : Étude des SOPC sur FPGA (System On Programmable Chip)

*Février à juillet 2003*

* Stage de fin d'études de 6 mois, de recherche et développement concernant les systèmes embarqués sur des architectures électroniques programmables en VHDL (type FPGA). Analyse des architectures concurrentes et de leurs évolutions récentes permettant d'embarquer des processeurs RISC pour réaliser de véritables sous-systèmes avioniques sur un seul composant. Démonstration de ces possibilités par la mise au point d'un système de filtrage d'images vidéo en temps réel (filtrage d'image vidéo, picture in picture, pour visu d'avion de combat) :
  * Rédaction de la documentation associée à l'analyse des technologies les plus récentes et des applications les plus pertinentes.
  * Spécification puis conception d'une application de filtrage vidéo et de réduction d'image en temps réel, pour affichage sur une visu d'avion de combat.
  * Développement et simulation électronique détaillée.
  * Rapport sur le travail réalisé et évaluation des possibilités démontrées au cours de l'étude, en particulier l'intégration aisée de processeur(s).

### ISEP, Paris — Coupe de France de Robotique (E=M6) : Électronique et Informatique appliquée à la robotique

*2000 à 2003 (trois participations)*

* Successivement Responsable de l'électronique, Chef de Projet de l'équipe de l'ISEP, puis Président de l'association, responsable des choix techniques et des relations extérieures. Travail d'équipe et formation aux contraintes d'un projet complexe dans l'embarqué :
  * Conception et réalisation d'une carte électronique programmable (EPLD ALTERA) de calcul des déplacements du robot à partir de 4 odomètres, carte s'interfaçant avec un DSP d'asservissement.
  * Conception et programmation de l'asservissement du robot par DSP T.I. sur carte de contrôle moteur.
  * Conception d'un protocole de communication par port série en C entre PC sous Linux et deux DSP.
  * Réalisation de documents de spécifications puis de conception.
  * Encadrement d'une équipe de 15 personnes, formation et organisation des réunions de travail.

### Explo-Control, Paris — Électronique analogique et numérique

*2 mois en 2001*

* Réalisation d'un circuit combinant composants analogiques et numériques, avec de très fortes contraintes de taille et de coût :
  * Analyse d'une maquette et de schémas antérieurs, adaptation au besoin.
  * Réalisation du PCB et de 2 prototypes pour industrialisation.

### ALM, Orléans (45) — Programmation d'Interface Homme Machine

*Six semaines durant l'été 2001*

* Conception puis programmation d'un outil sur PC de test et d'assistance aux réglages de tables d'opérations chirurgicales motorisées (domaine médical) pilotées par des cartes électroniques à base de DSP :
  * Étude des prototypes de tables et analyse des besoins exprimés par le personnel sur la chaîne de production.
  * Découverte des outils existants.
  * Conception de l'Interface Homme Machine.
  * Réalisation en Visual C++ et MFC, codage du protocole de communication par port série, puis intégration de l'outil de test à l'application existante.
  * Traduction en anglais du logiciel.
  * Rédaction de la documentation associée.

## Formation

### ISEP, Paris — Ingénieur (Architecture des Systèmes Temps Réels)

*2000 à 2003*

* Diplôme d'ingénieur de l'Institut Supérieur d'Électronique de Paris (75006), spécialisation « Architecture des Systèmes Temps Réels ».
* Formation Informatique / Électronique / Télécommunication en 3 ans sur concours.
* Classes préparatoires aux grandes écoles scientifiques au Lycée Pothier d'Orléans (45000), 1998 à 2000.
* Baccalauréat S en 1998 (mention bien).

## Centres d'intérêts

* Développements open-sources (Github : C++, Unreal Engine, Machine Learning, VR).
* Travail du bois : plusieurs pièces en chêne réalisées à la main, dont un meuble de piano, des maillets et une planche à découper en bois de bout, de la conception aux assemblages jusqu'à la finition. J'aime passer ce temps loin des écrans, tout en mettant en oeuvre la même planification et la même précision qu'en ingénierie.
* Boulangerie sans gluten : j'aime préparer mon pain au levain, faire mes propres mélanges de farines et fécules, calculer hydratation, nutrition et coût au kilo. Recettes publiée sous forme de [site Jekyll en Pages GitHub](https://srombauts.github.io/recettes-sans-gluten/).
* Jeux vidéo, lecture SF, pilotage de drone, jogging, randonnée, voyages.
</content>
