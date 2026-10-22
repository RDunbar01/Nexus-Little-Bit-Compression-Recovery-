# Nexus Compression & Recovery Studio — Accueil

## [Essayer dans le navigateur](<https://rdunbar01.github.io/Nexus-Little-Bit-Compression-Recovery-/Nexus_Compression_Recovery_Studio_v2_7_Browser.html>) · accès navigateur publié

La page HTTPS est publiée et son écran initial a été vérifié. Cela ne constitue pas une qualification complète des charges WebGPU, Windows ou Radeon. L’affichage du HTML dans GitHub n’exécute pas l’application.

Le paquet natif **2.7.1** est publié sur main. Ce correctif de démarrage empêche les mises à jour du titre natif de monopoliser les minuteries de l’interface. Le navigateur **2.7.1** est en ligne au lien stable v2_7_Browser ; son panneau de résidence attend les commandes du workflow et reste derrière l’avertissement initial. L’écran initial a été vérifié sans accepter cet avertissement ni exécuter de modèle. Les anciennes versions restent disponibles ; ne mélangez pas leurs composants. La revue du paquet et les contrôles d’extraction ont réussi, mais la qualification Windows, WebView2, Radeon et des modèles complets sur matériel réel reste à réaliser.

Ouvrez le lien et choisissez **Check WebGPU adapter**. L’objectif des dix premières secondes est d’examiner l’interface et les capacités du navigateur, pas de télécharger un modèle ni de garantir l’entraînement ou l’inférence. Le chargement dépend de la connexion et de l’appareil.

**L’essai HTML ne nécessite pas Python. Le moteur PyTorch natif exige le téléchargement complet.** Gardez l’installateur Python et toutes les parties de données de la même version ensemble. Python et PyTorch ne s’exécutent pas dans le HTML. La prise en charge de WebGPU, les fichiers locaux et les contrôles de compatibilité du modèle restent nécessaires.

## Versions de Python et environnement natif

- **Interpréteur conseillé : CPython 3.12 standard, 64 bits.** L’installateur annonce Python **3.11–3.14**, mais son programme de démarrage ne vérifie pas cette plage. L’ouverture avec une autre version ne prouve pas la compatibilité du moteur natif.
- **L’installation d’un nouvel environnement AMD exige CPython standard 64 bits 3.11–3.14, sans mode free-threaded**, sous Windows 11 **25H2**. Les environnements existants sont testés avant cette restriction d’installation et réutilisés uniquement si le test réussit ; leur Python doit correspondre aux paquets PyTorch installés. Aucune compatibilité plus large n’est certifiée ici.
- Le test natif attend **PyTorch 2.14.0+rocm10.1.0**, HIP et le périphérique RX 7900 XT/XTX configuré, puis vérifie un calcul FP32 avant/arrière avec des valeurs finies. Le paquet n’installe ni ne modifie Python, les pilotes AMD ou les prérequis du compilateur. Consultez la [matrice officielle AMD](https://rocm.docs.amd.com/en/latest/compatibility/compatibility-matrix.html).

Ces conditions ne constituent pas une validation sur matériel Windows, WebView2 ou Radeon réel, ni une qualification du modèle complet. Un test réussi ne valide pas toutes les précisions, compilations ou charges de travail. Recovery admet aussi provisoirement Windows 11 **26H2, build 26300 ou ultérieur**. Cette autorisation dans le code ne constitue ni une validation complète de la plateforme ni une extension de la matrice de prise en charge AMD.

**2.7.1 · Français**

Documentation de la version publiée. Consultez les preuves et limites ci-dessous.

[English](https://github.com/RDunbar01/Nexus-Little-Bit-Compression-Recovery-/wiki/Home) · [Français](https://github.com/RDunbar01/Nexus-Little-Bit-Compression-Recovery-/wiki/Home.fr) · [日本語](https://github.com/RDunbar01/Nexus-Little-Bit-Compression-Recovery-/wiki/Home.ja) · [한국어](https://github.com/RDunbar01/Nexus-Little-Bit-Compression-Recovery-/wiki/Home.ko)

## Objectif

Explorez la compression factorisée à faible précision et la récupération guidée par un modèle enseignant. Compression, inférence réussie et qualité récupérée sont des étapes distinctes. Choisissez un modèle et un corpus locaux compatibles. Le ZIP du corpus original est sélectionné localement et vérifié par somme de contrôle ; il n’est pas intégré au HTML.

## Choisir une édition

### Édition navigateur

[HTML](https://github.com/RDunbar01/Nexus-Little-Bit-Compression-Recovery-/blob/main/Nexus_Compression_Recovery_Studio_v2_7_Browser.html) · [README](https://github.com/RDunbar01/Nexus-Little-Bit-Compression-Recovery-/blob/main/README.md)

Utilisez un navigateur compatible WebGPU en HTTPS ou sur une origine localhost sécurisée prise en charge. Le fichier HTML unique contient le moteur JavaScript/WGSL personnalisé. Importez des fichiers locaux compatibles. Python, PyTorch, les services natifs, le téléchargement de jeux de données en ligne et la télémétrie GPU native ne sont pas disponibles ; les requêtes réseau de l’application sont bloquées. L’affichage du code sur GitHub n’exécute pas l’application.

### Édition installée

Téléchargez ensemble tous les fichiers du [paquet 2.7.1](https://github.com/RDunbar01/Nexus-Little-Bit-Compression-Recovery-/tree/main/releases/2.7.1), en conservant leur disposition. Gardez toutes les parties de données `.nxd` numérotées à côté de [Start_Nexus.py](https://github.com/RDunbar01/Nexus-Little-Bit-Compression-Recovery-/blob/main/releases/2.7.1/Start_Nexus.py), puis lancez `python Start_Nexus.py` avec l’interpréteur compatible. Lisez le [guide correspondant](https://github.com/RDunbar01/Nexus-Little-Bit-Compression-Recovery-/blob/main/releases/2.7.1/README.md) et le récapitulatif avant de confirmer. Chaque partie `.nxd` fait au plus **10 000 000 octets** ; chaque fichier distribué, avant installation, fait moins de **20 000 000 octets**. L’archive complète, l’application reconstruite, les fichiers installés et les modèles téléchargés peuvent être plus volumineux. Ne mélangez pas les versions. Les réglages et tests PyTorch natifs concernent l’édition installée, pas l’essai HTML seul.

## Mesures et limites

Les tests CPU et les contrôles statiques/DOM ne valident pas l’exécution sur du matériel Windows/Radeon/WebGPU réel. Comparez uniquement des conditions équivalentes : modèle, corpus, contexte, lot, précision et moteur. Les débits d’entraînement, de récupération, de traitement des invites et de génération sont des mesures différentes. Aucune compatibilité universelle ni vitesse maximale n’est garantie.

Débit de récupération enregistré, déclaré par le développeur : **2 500 jetons/seconde**. Il n’a pas été reproduit indépendamment ici et ne mesure pas la génération conversationnelle. Ce travail Nexus indépendant s’inspire de LittleBit de Samsung Research ; il ne s’agit pas d’une version officielle Samsung. Un stockage sous un bit ne prouve ni une mémoire d’entraînement sous un bit ni une résidence dans le cache L3. Conservez les licences applicables, dont CC BY-NC 4.0 pour le code SamsungLabs LittleBit.

## Crédits et licences

Rich Dunbar / Nexus Emerging Technology, avec l’aide d’outils de codage par IA. Les licences existantes et les conditions applicables aux recherches, au code, aux modèles et aux données tiers restent en vigueur. Cette page n’accorde aucune licence supplémentaire.

## Licence de la version actuelle

Cette version de Nexus n’est pas proposée sous la licence Apache 2.0. Le logiciel appartenant à Nexus ne peut être utilisé qu’à des fins personnelles et non commerciales. Toute autre utilisation, y compris commerciale, ainsi que toute modification ou redistribution, nécessite le consentement écrit exprès du titulaire des droits. Les codes, modèles, jeux de données tiers et composants sous licence distincte conservent leurs propres licences et mentions. Les droits déjà accordés et les droits qui ne peuvent légalement être restreints restent inchangés.

