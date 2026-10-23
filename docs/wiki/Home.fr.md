# Nexus Compression & Recovery Studio

**Version 2.7.1**

Compresser les modèles de langage pris en charge en représentations factorielles à faible nombre de bits, puis mesurer la qualité linguistique récupérable par entraînement de récupération.

**[Essayer dans le navigateur](https://rdunbar01.github.io/Nexus-Little-Bit-Compression-Recovery-/Nexus_Compression_Recovery_Studio_v2_7_Browser.html)** · [Télécharger les composants de bureau](https://github.com/RDunbar01/Nexus-Little-Bit-Compression-Recovery-/tree/main/releases/2.7.1) · [README](https://github.com/RDunbar01/Nexus-Little-Bit-Compression-Recovery-/blob/main/README.md)

Ouvrez la version d’essai pour examiner l’interface et choisissez **Check WebGPU adapter**. Aucune installation de Python n’est nécessaire. L’objectif est un premier aperçu rapide ; le chargement d’un modèle et l’exécution d’une tâche dépendent des données et de l’appareil.

Paquet natif 2.7.1 ; édition navigateur 2.7.1.

## Fonctionnalités

- Compression factorielle à faible nombre de bits à partir de modèles et de corpus locaux.
- Commandes de récupération guidée par un modèle enseignant et évaluation des modèles pris en charge.
- Parcours distincts pour WebGPU dans le navigateur et PyTorch installé.
- Journaux de progression, de durée et de diagnostic pour comparer les essais.

## Contribution technique

Une implémentation indépendante qui rend les expériences de compression et de récupération accessibles dans une interface graphique locale. Le programme d’entraînement de récupération Nexus prolonge cette démarche ; il ne reproduit pas un produit officiel Samsung.

## Pourquoi un seul fichier HTML ?

L’édition navigateur réunit l’interface, JavaScript, CSS et les noyaux WGSL dans un seul fichier HTML. Ce choix facilite les essais en ligne, le partage du lien et l’inspection, sans compilation ni CDN à l’exécution. Le fichier contient le moteur navigateur, pas les poids des modèles ni le backend PyTorch natif.

Utilisez un navigateur compatible WebGPU en HTTPS. Les requêtes réseau à l’exécution, la surveillance matérielle native et les passerelles vers un serveur local sont désactivées. L’entraînement ou l’évaluation exige des entrées prises en charge. Le backend PyTorch natif nécessite le téléchargement complet.

[English](https://github.com/RDunbar01/Nexus-Little-Bit-Compression-Recovery-/wiki/Home) · [Français](https://github.com/RDunbar01/Nexus-Little-Bit-Compression-Recovery-/wiki/Home.fr) · [日本語](https://github.com/RDunbar01/Nexus-Little-Bit-Compression-Recovery-/wiki/Home.ja) · [한국어](https://github.com/RDunbar01/Nexus-Little-Bit-Compression-Recovery-/wiki/Home.ko)

## Versions de Python et environnement natif

- **Interpréteur conseillé : CPython 3.12 standard, 64 bits.** L’installateur annonce Python **3.11–3.14**, mais son programme de démarrage ne vérifie pas cette plage. L’ouverture avec une autre version ne prouve pas la compatibilité du moteur natif.
- **L’installation d’un nouvel environnement AMD exige CPython standard 64 bits 3.11–3.14, sans mode free-threaded**, sous Windows 11 **25H2**. Les environnements existants sont testés avant cette restriction d’installation et réutilisés uniquement si le test réussit ; leur Python doit correspondre aux paquets PyTorch installés. Aucune compatibilité plus large n’est certifiée ici.
- Le test natif attend **PyTorch 2.14.0+rocm10.1.0**, HIP et le périphérique RX 7900 XT/XTX configuré, puis vérifie un calcul FP32 avant/arrière avec des valeurs finies. Le paquet n’installe ni ne modifie Python, les pilotes AMD ou les prérequis du compilateur. Consultez la [matrice officielle AMD](https://rocm.docs.amd.com/en/latest/compatibility/compatibility-matrix.html).

Ces conditions ne constituent pas une validation sur matériel Windows, WebView2 ou Radeon réel, ni une qualification du modèle complet. Un test réussi ne valide pas toutes les précisions, compilations ou charges de travail. Recovery admet aussi provisoirement Windows 11 **26H2, build 26300 ou ultérieur**. Cette autorisation dans le code ne constitue ni une validation complète de la plateforme ni une extension de la matrice de prise en charge AMD.


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

## Utilisation et attribution

Rich Dunbar / Nexus Emerging Technology. L’usage personnel ainsi que les tests et évaluations commerciaux internes sont autorisés pour les éléments appartenant à Nexus. La distribution, la modification, le déploiement en production et les autres usages commerciaux nécessitent un consentement écrit exprès. Les licences tierces et les droits déjà accordés restent inchangés. [licence](https://github.com/RDunbar01/Nexus-Little-Bit-Compression-Recovery-/blob/main/LICENSE) · [autorisation d’évaluation (en anglais)](https://github.com/RDunbar01/Nexus-Little-Bit-Compression-Recovery-/blob/main/COMMERCIAL_EVALUATION_PERMISSION.md).
