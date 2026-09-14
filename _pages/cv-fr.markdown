---
layout: single
title: "CV (français)"
permalink: /cv-fr/
toc: true
toc_label: "Sommaire"
toc_sticky: true
---

*Ceci n'est pas un CV résumé, mais une version plus exhaustive conservée comme référence. Mes coordonnées personnelles (adresse postale et téléphone) sont volontairement omises de la version en ligne.*

**Sébastien Rombauts** · Ingénieur logiciel senior, systèmes et automatisation

[sebastien.rombauts@gmail.com](mailto:sebastien.rombauts@gmail.com) · [LinkedIn](https://www.linkedin.com/in/srombauts/) · [GitHub](https://github.com/SRombauts) · [Blog et portfolio](https://srombauts.eu/)

Ingénieur logiciel, diplômé de l'ISEP en 2003, j'ai travaillé sur les systèmes embarqués, les outils de développement et l'exploitation de serveurs de jeu Linux dans le Cloud. Mon expérience comprend l'automatisation des builds et des déploiements (CI/CD), le diagnostic de crashs et de performances serveurs, ainsi que la documentation et la transmission aux équipes.

Je développe aujourd'hui ma pratique de l'infrastructure cloud et de Kubernetes pour évoluer vers des responsabilités DevOps/SRE.
Admis au programme **Cloud & DevOps Engineer de La Capsule**, en complément de mon expérience professionnelle ; [programme et apprentissage en cours](#formation-cloud-devops).

## Compétences

* **Automatisation, build et CI/CD** : Jenkins, GitLab CI, CMake, scripts Python et shell ; Yamato CI, PackageWorks et HAL chez Unity ; déploiements par environnement, branche et région.
* **Systèmes** : Linux, macOS, Windows ; expérience des systèmes embarqués et des interactions matériel/logiciel.
* **Cloud et exploitation (LiveOps)** : SpatialOS, Google Cloud Platform (GCP), Multiplay, serveurs physiques (bare metal) et cloud ; déploiements du backend web Plastic SCM en Europe, aux États-Unis et en Asie.
* **Infrastructure as Code (IaC)** : contributions secondaires et revues de PR sur les configurations Terraform de l'infrastructure chez Unity.
* **Observabilité et diagnostic** : suivi des logs et des performances avec Datadog, création de tableaux de bord et de graphiques dans Grafana, rapports de plantage, profilage et analyse de problèmes réseau et de réplication.
* **Données et services** : accès SQL et interventions ponctuelles de déploiement, d'administration et de surveillance sur PostgreSQL ; pipeline analytique Python et BigQuery ; intégration de services backend et de paiement.
* **Langages** : C++, Python, C#, SQL, Bash/Batch/PowerShell.
* **Transmission** : documentation des procédures, mentorat, formation et support technique aux équipes.
* **En cours d'acquisition** : Kubernetes, en autoformation pratique à domicile.
* **Moteurs** : Unity, Unreal Engine.
* **Bibliothèques & API** : SQLite3, jsoncpp, TinyXml, SDL3, googletest, doctest, OpenGL.
* **Outils** : Unreal Profiler, Unity Version Control (UVCS, anciennement Plastic SCM), Perforce, Jenkins/GitLab CI, CMake, Git, Valgrind.
* **Méthodes** : Agile/SCRUM, TDD, DevOps, CI/CD, Design Patterns, UML.
* **IDEs/Agents** : Visual Studio, Rider, Visual Studio Code, Cursor, Claude Code, Codex.
* **Langues** : anglais courant et technique, conversations simples en allemand et en espagnol.

Voir les [compétences complémentaires](#competences-complementaires) en fin de page.

## Expérience

### Unity, Paris, France — Senior Software Engineer, package éditeur Unity (équipe VCS Tech)

*Juillet 2024 à juillet 2026*

*Environnement de travail chez Unity : MacBook pour dévelopement sous Windows, macOS et Linux.*

**Build, CI/CD et publications**

* Mise à jour des configurations Yamato CI et du pipeline PackageWorks pour les publications du package Unity Version Control : adaptation aux exigences de release, vérification de compatibilité de l'API publique et mises à jour automatisées des dépendances.
* Intégration d'outils de mesure de couverture de code, documentation du workflow et correction de tests et d'avertissements pour satisfaire les contrôles de publication.
* Extension ponctuelle de HAL, l'outil CI/CD historique de Plastic SCM en C# intégré à Jira et Slack, pour tester le package Unity sur des images Bokken, utilisées par les machines virtuelles de build multiplateforme de Unity.
* Participation au cycle de publication hebdomadaire : sélection d'une release stable, validation manuelle partagée dans l'équipe, puis publication automatisée des installeurs et des notes de version après accord collectif.

**Package Unity Version Control (Unity Editor, C#)**

* Ma première contribution a été livrée dans la version 2.0.5 (juin 2023). À mesure que l'équipe s'est élargie pour prendre aussi en charge le package de l'éditeur Unity et les applications de bureau, le package Unity Version Control pour l'éditeur Unity (C#) est devenu ma priorité, le plugin Unreal est passé en maintenance, et je n'ai contribué que ponctuellement aux applications de bureau et à Gluon.
* Responsable de la planification et de l'exécution des publications sur de nombreuses versions (de la 2.5.0 à la 2.12.x), en coordonnant la validation de l'équipe et en alignant les sorties sur les jalons de l'éditeur Unity, notamment pour être prêt à temps pour Unity 6.1 à la GDC 2025 et Unity 6.3 à l'Unite 2025.
* Conception et réalisation d'une fonctionnalité « créer une revue de code depuis le plugin » pour faciliter l'adoption des workflows par branches, incluant une boîte de dialogue de confirmation réutilisable et le travail d'UI multiplateforme (macOS) associé.
* Validation des workflows de fusion de branches, de « shelve & switch » et de la vue des « shelves », et investigation de problèmes de performance et de plantages difficiles à reproduire remontés par le support client.

**Analytics produit**

* Ajout d'événements Amplitude dans le package Unity et le code client partagé, et création de tableaux de bord et de graphiques de suivi dans Amplitude.

**Éditeur Unity (C#)**

* Une centaine de pull requests fusionnées dans l'éditeur Unity, en plus de contributions à des dépôts internes associés.
* Réduction du coût des suites de tests automatisés du module Version Control et de l'outil de fusion YAML de l'éditeur.

**Maintenance du plugin Unreal Engine (C++)**

* Maintien du plugin à jour avec le moteur : compatibilité et correctifs pour Unreal Engine 5.5 et 5.6, avec des publications livrées dans la semaine suivant chaque sortie du moteur.
* Correction de graves problèmes de performance dans le traitement des grandes listes de fichiers.
* Diagnostic et correction de problèmes subtiles d'authentification multi-comptes (requierant des évolutions de l'outil de CLI).
* Refonte de l'UX de l'assistant de création de workspace (sélection par menu déroulant des organisations et projets unifiés).
* Migration de la distribution du plugin de l'Unreal Marketplace vers Fab, et livraison de la vue « Changesets ».

**Perforce et travaux transverses**

* Maintenance du plugin Perforce et de l'intégration du contrôle de version dans l'éditeur Unity : mises à jour de la CI et de l'infrastructure, support de Perforce Cloud, support de macOS ARM64 (« Apple Silicon ») et des chemins longs sous Windows.
* Extension du client en ligne de commande `cm` (support des organisations unifiées, nouvelles options de vérification de connexion) et ajout de son premier smoke test multi-serveurs.
* Étude d'une nouvelle architecture envisagée pour le package Perforce et documentation des compromis.
* Mentorat et pratiques d'équipe : introduction d'un workflow de couverture de code dans l'équipe, promotion d'une culture QA renforcée en complément des revues de code et des tests unitaires, refonte de la roadmap du package, et dogfooding de Unity Version Control lors du HackWeek 2024.

**Ingénierie logicielle assistée par IA**

Pilotage de l'effort IA de l'équipe pour montrer, former et encourager une démarche coordonnée :

* Pratique de terrain : près d'un an d'usage quotidien intensif de Cursor (IDE IA), puis de Claude Code. Lecture, expérimentation et construction de vrais prototypes (dont un package Perforce expérimental en C# avec l'UI Toolkit), tout en itérant sur des instructions personnalisées et des agent skills.
* Partage à grande échelle : coaching de coéquipiers, Unity Talks internes et démos en direct pour diffuser la pratique à toute l'équipe, plutôt que de garder ces acquis pour moi.
* Montée en niveau de toute l'équipe : transformation de mes fichiers SKILL (instructions pour agents IA) en skills génériques et performants, publiés sur le dépôt de l'équipe, pour que chacun parte d'une base commune au lieu de réinventer la roue dans son propre environnement local. J'ai rédigé la grande majorité de ces fichiers.

### Unity, Paris, France — Senior Software Engineer, plugin Unreal Engine (équipe Integration / Ecosystem)

*Février 2022 à juillet 2024*

**Backend cloud, déploiements multi-région et DevOps (C#, SQL)**

* Évolutions ciblées du backend C# et du frontend ASP.NET de plasticscm.com. Le backend gérait la création de comptes, l'authentification SSO des clients Plastic SCM (application de bureau, CLI, package Unity et serveurs), la facturation, les paiements Stripe et certaines API.
* Modifications incluant des mises à jour de version du schéma de la base de données ; suivi des problèmes de performance avec Datadog, sur une instrumentation mise en place par un collègue de la squad.
* Participation aux déploiements multi-région du backend web et du frontend en Europe, aux États-Unis et en Asie, avant l'intégration partielle de plasticscm.com à unity.com.
* Contribution secondaire aux évolutions de l'infrastructure : modification et revue des fichiers de configuration Terraform dans un dépôt Git, avec déploiements automatisés après fusion des PR.
* Environnement cloud principalement sur GCP, avec un historique AWS, des configurations d'Infrastructure as Code en Terraform et des microservices sur Kubernetes dont je n'assurais pas l'administration. L'environnement comprenait aussi Prometheus/Grafana pour le monitoring des clusters et BigQuery/Looker pour l'analytics.

**Plugin Unity Version Control (Unreal Engine, C++)**

* Recruté comme développeur initial du plugin Unity Version Control (anciennement Plastic SCM) pour Unreal Engine, avec pour mission de le moderniser et de le migrer vers Unreal Engine 5 (C++).
* Propriétaire du plugin de bout en bout : développement des fonctionnalités, support client et publications, en l'alignant sur les API de contrôle de version modernes d'Unreal Engine 5 et en le maintenant à jour à chaque sortie du moteur, jusqu'à la version 1.12.0 en décembre 2024.
* Ajout d'événements de suivi pour le plugin Unreal Engine 5 dans l'environnement Prometheus/Grafana, et création de tableaux de bord et de graphiques dans Grafana.

Le plugin Unreal est resté ma priorité durant toute cette période, même si dès mi-2023 j'avais commencé à contribuer au package de l'éditeur Unity (ci-dessus).

### Darewise Entertainment, Paris (75019) · Lead Tech and Tools Programmer

*Février 2020 à février 2022*

*MMO « Life Beyond », initialement « Project-C » ; équipe Tech, Tools et Backend.*

**Build, déploiements et backend**

* Encadrement du programmeur outils, de l'ingénieur build et de l'équipe backend ; conception des évolutions du pipeline Jenkins/Perforce et migration des scripts vers Python avec notre bibliothèque interne.
* Gestion des déploiements par branches : environnements de développement et de QA depuis la branche principale, puis environnements de staging et live depuis la branche de release.
* Corrections et améliorations du backend de matchmaking en C# sur GCP, avec PlayFab.

**Migration vers GCP et Multiplay**

* Participation à la migration de SpatialOS vers le réseau natif d'Unreal Engine et une infrastructure cloud sur Google Cloud Platform (GCP).
* Participation au déploiement des serveurs Unreal avec Multiplay : orchestration sur serveurs physiques (bare metal), complétée par des ressources cloud pour absorber la montée en charge.

**Ingénierie et transmission**

* Maintenance de notre fork Unreal Engine 4.26, backport de correctifs, améliorations du plugin Perforce et contributions amont avec Epic Games (GitHub). Coordination avec UDN.
* Mentorat des programmeurs, tech artists et tech designers ; développement d'API Blueprint et Python pour leurs outils.
* Analyse de crashs, profilage et optimisation, diagnostic des problèmes réseau et de réplication.

### Darewise Entertainment, Paris (75019) · Senior Software Engineer, Tools & Tech

*Avril 2018 à février 2020*

*Phase initiale de « Life Beyond » (« Project-C »), sur SpatialOS, au sein d'une équipe de 6 programmeurs.*

**Serveurs Linux, build et exploitation**

* Exploitation initiale de nos serveurs de jeu dédiés Unreal Engine sur la plateforme cloud SpatialOS.
* Intégration et maintenance du SpatialOS GDK pour Unreal, avec des contributions d'améliorations en collaboration avec les équipes techniques d'Improbable.
* Développement du système de build avec un stagiaire : pipelines Jenkins intégrés à Perforce et scripts Python, compilation et envoi automatiques du serveur de jeu Linux et de ses symboles de débogage dans le cloud.
* Surveillance des serveurs de jeu et des déploiements sur SpatialOS dans le cadre du LiveOps.

**Ingénierie et outils**

* Maintenance de notre fork d'Unreal Engine 4.22, backport de correctifs, intégration de plugins. Coordination avec UDN. Contributions amont avec Epic Games (GitHub).
* Mentorat de programmeurs juniors, assistance aux tech designers, artists et animateurs.
* Développement de barres d'outils & extensions de menus dans l'éditeur Unreal.
* Développement d'APIs Blueprint & Python pour les tech designers & tech artists.
* Développement d'un serveur web intégré au client du jeu pour l'outiller (UI & API REST).
* Développement C++ de la couche technique du jeu : infrastructure réseau, managers et configuration ; intégration de PlayFab pour l'authentification et la découverte des serveurs.
* Intégration et exploitation d'un outil de rapports de plantage fondée sur Unreal Crash Reporter et un backend open source.
* Formation à l'analytics sur GCP et BigQuery, puis participation à la mise en place du pipeline analytique : traitement par lots toutes les six heures par un script Python dans Google Cloud.
* Intégration du service de paiement Xsolla.

**Contributions sur la période Darewise (2018 à 2022)**

* Interventions ponctuelles sur PostgreSQL, la base du serveur de jeu : accès SQL dans la couche technique du jeu, déploiement, administration, surveillance et ajustements de configuration lors de problèmes de disponibilité ou de performance.
* Services utilisés dans l'environnement du projet : GCP Compute, S3, PostgreSQL et BigQuery.

### Projets open source, GitHub · Développement de bibliothèques et logiciels

*Mai 2009 à aujourd'hui ; activité personnelle menée en parallèle de mes emplois.*

* Pac Man C++ / SDL, challenge multi CodinGame « The Great Escape ».
* [char-rnn-tensorflow](https://github.com/SRombauts/char-rnn-tensorflow) (2017) : expérimentation de TensorFlow sur un modèle de langage LSTM caractère par caractère en Python. J'avais découvert [char-rnn](https://github.com/karpathy/char-rnn) et l'article d'Andrej Karpathy [« The Unreasonable Effectiveness of Recurrent Neural Networks »](https://karpathy.github.io/2015/05/21/rnn-effectiveness/) par la publication d'OpenAI [« Unsupervised sentiment neuron »](https://openai.com/index/unsupervised-sentiment-neuron/).
* [SQLiteCpp](https://github.com/SRombauts/SQLiteCpp), bibliothèque C++ autour de SQLite3.
* Logger C++, shared_ptr compatible C++98, serveur web embarqué en C++ avec Boost Asio, tutoriels OpenGL puis Vulkan.

### Freelance · Développement de plugins Unreal Engine 4 (open source)

*Mars 2014 à février 2022*

* Plugin Git pour Unreal Engine 4.1, intégré officiellement depuis UE4.7 ; Epic Games m'a invité à rejoindre l'équipe Unreal Engine à la GDC 2016 à San Francisco.
* Plugin Plastic SCM depuis Unreal Engine 4.11, intégré pour UE4.24.
* Tutoriels et prototypes avec Unreal Engine (ArchViz, jeux, multi, C++ et Blueprints).

### ENGIE INEO Systrans, Achères (78) — Développement logiciels applicatifs embarqués

*Mai 2009 à avril 2018*

* Formation et encadrement en équipe de 2 à 5 personnes (Agile SCRUM).
* Conception, développement dirigés par les tests (TDD) de l'interface du SAEIV (transports en commun).
* Migration des postes de développement de Windows vers Ubuntu, resté notre environnement de travail principal pendant plusieurs années. Mise en place de machines virtuelles et de serveurs Linux pour des outils internes.
* Mise en place du framework C++, des couches d'abstraction de l'OS, des bibliothèques C/C++ et du build-système CMake, avec des portages sur Windows CE, Linux, Android et OpenAT.
* Contribution à la migration des calculateurs embarqués de Windows CE vers Linux, puis développement et maintenance pendant plusieurs années d'applications sans interface graphique exécutées sur ces calculateurs.
* Applications Android, avec service de VoIP en Protocol Buffers sur TCP/IP, serveur web de maintenance embarqué, séquenceur de traitements asynchrones.
* Développement et déploiement d'un service de rapports de plantage, d'abord sur Android puis sous Linux.
* Conception et développement du moteur de scénarios de tests automatiques pour Jenkins puis GitLab CI.
* Déploiement et maintenance de Jenkins pour l'équipe de R&D embarquée, puis adaptation des processus d'intégration continue aux besoins d'autres équipes.
* Déploiement de Git dans l'entreprise, puis de GitLab CI sur l'infrastructure virtualisée gérée par l'IT. Mise en place du workflow de développement et de sa documentation de référence.
* Administration d'une partie de l'intranet : wiki, outils de mesure d'audience et, plus ponctuellement, Mantis après avoir contribué à son déploiement initial.

### ENGIE INEO Systrans, Achères (78) — Responsable drivers et logiciels bas niveau

*Mai 2006 à mai 2009*

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

* Développements embarqués au sein d'une équipe projet de 10 personnes :
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

### ISEP, Paris — Projet d'option de fin d'études

*Fin 2002 à janvier 2003*

**Architecture processeur** : conception et simulation d'un processeur RISC simplifié, définition de son jeu d'instructions et implémentation de son microcode.

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

### La Capsule · Cloud & DevOps Engineer {#formation-cloud-devops}

*Admission confirmée, session du 12 octobre au 18 décembre 2026, 400 heures sur 10 semaines à temps plein.*

[Programme officiel Cloud & DevOps Engineer, La Capsule](https://www.lacapsule.academy/program/devops-full-time). Préparation au titre professionnel « Administrateur système DevOps » (niveau 6).

**Programme prévu :**

* **Linux, systèmes et réseaux** : administration, SSH, scripts shell et sécurité des infrastructures.
* **Docker et Kubernetes (K8s)** : conteneurisation, administration de clusters, orchestration de services sur plusieurs serveurs, haute disponibilité et scalabilité.
* **Infrastructure as Code (IaC)** : Terraform et Ansible, création et configuration automatisées des serveurs.
* **Observabilité et monitoring** : Prometheus, Grafana, tableaux de bord et alertes pour surveiller les services en production.
* **CI/CD et fiabilité** : automatisation des mises en production, environnements de déploiement, tests de montée en charge ; Git, GitLab et SonarQube.
* **Cloud et données** : déploiement sur AWS et Linode, programmation Python, installation et administration de PostgreSQL.
* **Projet pratique** : déploiement d'une infrastructure de plusieurs services, sécurisation, stockage de données et supervision.

### Autoformation

- Docker et Kubernetes ces derniers jours en préparation de responsabilités DevOps/SRE.
- Apprentissage de Rust commencé l'année dernière, reprise prévue dans les prochaines semaines.

### ISEP, Paris — Ingénieur (Architecture des Systèmes Temps Réels)

*2000 à 2003*

* Diplôme d'ingénieur de l'Institut Supérieur d'Électronique de Paris (75006), spécialisation « Architecture des Systèmes Temps Réels ».
* Formation Informatique / Électronique / Télécommunication en 3 ans sur concours.
* Classes préparatoires aux grandes écoles scientifiques au Lycée Pothier d'Orléans (45000), 1998 à 2000.
* Baccalauréat S en 1998 (mention bien).

## Compétences complémentaires {#competences-complementaires}

*Acquises au fil de mon parcours, notamment en développement embarqué, en électronique et en temps réel.*

* **Langages** : C, assembleur, VHDL, Java, PHP, JavaScript, HTML5, VBA.
* **Temps réel** : architecture des processeurs, gestion d'interruptions, couches basses, séquenceurs temps réel, objets de synchronisation et drivers temps réel.
* **Matériels** : CPLD et FPGA, DSP TI TMS320F240, processeurs RISC embarqués sans OS.
* **Réseaux & protocoles** : SPI, I2C, CAN, TCP/IP, UDP/IP, liaisons série RS232 et RS485.

### Environnements et outils utilisés par le passé

*Conservés pour documenter les environnements de mes précédents projets.*

* **Bibliothèques** : Boost, Protocol Buffers, Assimp, TensorFlow.
* **Systèmes** : Windows CE 5.0, Windows XP et Windows NT.
* **Logiciels & outils** : Eclipse, Android Studio ; Platform Builder et eMbedded Visual C++ pour Windows CE 5 ; développement de drivers Windows XP avec le DDK et le débogueur Visual SoftICE ; chaîne de développement FPGA d'Altera (Quartus II, SOPC Builder, ModelSim) et Code Composer (expérience de Xilinx) ; outils GNU (Cygwin, binutils, gcc, Makefile, gdbtk) ; serveurs et clients CVS et SVN.
* **Méthodes & normes** : Merise, SART/SADT.

## Centres d'intérêt

* Développements open source (GitHub : C++, Unreal Engine, Machine Learning, VR).
* Travail du bois : plusieurs pièces en chêne réalisées à la main, dont un meuble de piano, des maillets et une planche à découper en bois de bout, de la conception aux assemblages jusqu'à la finition. J'aime passer ce temps loin des écrans, tout en mettant en œuvre la même planification et la même précision qu'en ingénierie.
* Boulangerie sans gluten : j'aime préparer mon pain au levain, faire mes propres mélanges de farines et fécules, calculer hydratation, nutrition et coût au kilo. Retrouvez [mes recettes sans gluten](https://srombauts.github.io/recettes-sans-gluten/).
* Lecture SF, cf. [liste de lecture de ce blog](https://srombauts.eu/lectures-sf/).
* Jeux vidéo, pilotage de drone, jogging, randonnée, voyages.
